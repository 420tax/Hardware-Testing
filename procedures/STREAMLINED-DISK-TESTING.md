# Streamlined Disk Screening

Version: 1.0 — October 25, 2026

## Standard test sequence

For used disks being considered for reuse. Run one full write/read verification per disk, compare SMART before and after, and investigate only exceptions. NVMe drives are SSDs; this repository uses NVME for NVMe and SSD for SATA/non-NVMe models.

| Stage | NVMe and SATA SSD | Mechanical HDD |
|---|---|---|
| 1. Identify and baseline | Record model, serial, capacity, connection and full SMART | Same; note reallocated, pending and uncorrectable sectors |
| 2. Full write/read verification | H2testw: all available space, Write + Verify, once | Same |
| 3. Internal extended test | Optional follow-up if needed and supported | Run once if supported; save completion result |
| 4. Final SMART and decision | Compare errors, wear, spare and thermal counters | Compare media and interface errors and self-test log |
| 5. Archive | Save evidence and disposition on NVME or SSD branch | Save evidence and disposition on HDD branch |

No routine CrystalDiskMark, separate surface READ test, random seek test, repeated short tests, or weekend write loops. They add time without being required by this screening policy. This is a practical reuse screen, not manufacturer certification or a guarantee of future reliability.

## 1. Identify the disk and capture the baseline

1. Connect the disk, preferably directly by SATA or PCIe/NVMe. A USB bridge may limit SMART or internal self-test commands.
2. Match the physical label's **model and serial number** to the selected disk in Hard Disk Sentinel or smartctl. Drive letters, disk numbers and /dev names can change.
3. Record the date, capacity, connection/adapter and tool versions.
4. Save a full SMART report before any long test. Hard Disk Sentinel or smartctl is sufficient; CrystalDiskInfo is optional.
5. Inspect health details, rather than relying only on a green health badge. Review any existing critical warnings, errors, worn-out spare capacity or failed tests before proceeding.

PowerShell discovery, run as administrator:

```powershell
Get-Disk | Select-Object Number, FriendlyName, SerialNumber, Size, IsBoot, IsSystem
& "C:\Program Files\smartmontools\bin\smartctl.exe" --scan-open
```

Then use the discovered device and type:

```powershell
# Example only: confirm identity; this device name is not permanent.
& "C:\Program Files\smartmontools\bin\smartctl.exe" -x -d nvme /dev/sdb
```

Use the reported type for SATA drives rather than copying the NVMe example. If the disk is behind RAID, inspect each physical member where passthrough permits; a virtual-volume health badge is not a member-level test.

## 2. Run one full write/read verification

**Preparation can erase data. Confirm that the exact disk's contents are disposable or backed up before deleting partitions or formatting. Never target the Windows boot/system disk or an active pool/RAID member.**

1. Prepare an empty volume covering the intended usable capacity. A quick NTFS format is adequate preparation; do not add a full format merely as a duplicate test.
2. Open H2testw, select English, and select the confirmed target volume.
3. Select **all available space**, then **Write + Verify**.
4. Let both phases finish. Prevent system sleep for the test and keep the disk powered. Other disks may be tested concurrently if connections, power and cooling permit; do not run multiple tests against the same disk.
5. Save the full result text, tested amount and write/read speeds. A successful result states **Test finished without errors**.
6. Leave test files until the result has been saved. Delete the test's *.h2w files afterward.

H2testw verifies files in available filesystem space. It does not cover occupied files, filesystem metadata, spare NAND, or every physical cell. On an empty full-size volume it exercises nearly all usable space. A small difference between available and tested space is not itself an error; investigate a large unexplained difference or reported corruption. A quick format by itself is not a media test.

### Alternative: Hard Disk Sentinel Pro

Instead of H2testw, use **Disk → Surface Test → WRITE + read test**, covering the entire selected physical disk, one pass. This is destructive, including existing partitions/data; verify the exact model and serial before starting. Save the final block/error counts and temperature graph.

Use **one** full write/read method as the routine screen. A READ-only surface test cannot replace write verification. If an exclusive lock fails during a destructive test, cancel and resolve it; permission to continue a READ-only test is not permission to bypass protection for a write test.

## 3. Mechanical HDD: run the extended internal self-test

In Hard Disk Sentinel, select the correct physical HDD, then **Disk → Extended Self-Test**. Wait for its completion and save the result.

Alternatively use smartctl with the device/type discovered earlier:

```powershell
# SATA example only; use the discovered device path and type.
& "C:\Program Files\smartmontools\bin\smartctl.exe" -t long -d ata /dev/sdX
# After the recommended interval:
& "C:\Program Files\smartmontools\bin\smartctl.exe" -x -d ata /dev/sdX
```

A command accepted or a timer elapsed is not a pass; verify the self-test log says it completed without error. If unsupported or blocked by an adapter/controller, record **not completed**, not passed or failed. A direct connection may permit the test. For SSDs, internal extended testing is optional follow-up rather than a mandatory duplicate of the host write/read screen.

## 4. Final SMART, temperature and disposition

Save full SMART after testing and compare against baseline.

| Outcome | Decision |
|---|---|
| Verification clean; no relevant new errors; no unresolved health or cooling concern; HDD extended test passed when available | Bench screening passed; candidate for reuse |
| Tests clean but cooling, wear, interface instability or unavailable diagnostics need attention | Conditional reuse / investigate; document limitation |
| Verification mismatch, unreadable data, failed self-test, critical warning or increasing media defects | Hold out of service; diagnose before reuse |

For SSDs, check media/data-integrity or uncorrectable errors, available spare, endurance estimate, critical warnings, and thermal-management counters. For HDDs, examine pending and offline-uncorrectable sectors and changes in reallocated sectors. Nonzero historical reallocation or interface errors need review; they are not automatically erased by a later passing test. CRC/link errors may originate in cabling or adapters.

Record idle and observed load temperature. Use the model's published limits or reported thresholds; do not apply one universal threshold to every drive. A cool final reading does not show the peak temperature. Resolve excessive heat or thermal-management activity in the intended installation.

If SMART cannot be read, label it unavailable and retain that limitation in the disposition. A host verification pass does not substitute for missing health telemetry.

## 5. Follow-up only when justified

- **Read-only surface test:** needed when contents must be preserved, to map slow/problem regions, or to investigate inconsistent reads. It does not verify writing.
- **CrystalDiskMark:** only for a performance question. Remove test files, allow SSD idle time, and record free space, connection, settings and temperature.
- **Repeat write/read:** only after a failure has a plausible corrected cause, such as a cable, adapter or power issue. Keep both the failed and retest evidence.
- **Reboot/power-cycle and reverify existing H2testw files:** optional for suspected retention/power problems; not required on every disk.
- **SSD internal self-test:** useful for unexplained problems if supported.
- Avoid routine multi-pass reinitialization/repair modes or endless SSD writes. Remapping or a later pass does not erase evidence of an earlier failure.

## Per-drive record checklist

Store records under `drives/MODEL-SERIAL.md` on the relevant hardware branch.

- [ ] Model, serial, capacity, firmware and connection
- [ ] Date, bench machine and tool versions
- [ ] Baseline SMART
- [ ] Full write/read result, tested capacity, duration/speeds
- [ ] HDD extended self-test result, or reason unavailable
- [ ] Final SMART and relevant counter changes
- [ ] Observed temperatures and cooling concerns
- [ ] Disposition: pass, conditional/investigate, or hold
- [ ] Intended reuse and remaining follow-up

Keep full reports or clearly identified excerpts, rather than only the health percentage. Do not mark attempted or unavailable tests as completed.

## Sources and tool downloads

- [H2testw — Heise publisher download](https://www.heise.de/download/product/h2testw-50539)
- [Hard Disk Sentinel surface-test documentation](https://www.hdsentinel.com/help/en/61_surfacetest.html): test types, overwrite behavior and verification.
- [Hard Disk Sentinel test FAQ](https://www.hdsentinel.com/help/en/62_testfaq.html): limitations and destructive testing.
- [smartmontools](https://www.smartmontools.org/)

The sequence and acceptance decisions above are this repository's streamlined screening policy, not a claim that the publishers prescribe this exact sequence.
