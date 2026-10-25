# Intel SSDPEKNW512G8 — PHNH852005YT512A

## Disposition

**Bench screening passed; reuse candidate with cooling follow-up.** H2testw completed its available-space write/verify without errors, and Hard Disk Sentinel completed a full-surface read with no damaged or bad blocks. No media/data-integrity errors or error-log entries were reported in the supplied SMART snapshots.

No additional bench testing is planned under the streamlined screening process. These results describe observed behavior, not a guarantee of future reliability. Internal NVMe self-testing was not completed.

## Identity and test environment

| Field | Value |
|---|---|
| Model | INTEL SSDPEKNW512G8 |
| Serial | PHNH852005YT512A |
| Firmware | 002C |
| Capacity | 512,110,190,592 bytes (512 GB; approximately 476.94 GiB) |
| Interface | NVMe 1.3; CrystalDiskInfo reported PCIe 3.0 x4 current/supported |
| Logical sector size | 512 bytes |
| Bench | Dell Precision T3600; Windows 10 Pro 22H2, build 19045 |
| Windows assignment during testing | Disk 1; E:; label BENCH-TEST |
| smartctl assignment during testing | /dev/sdb, device type nvme |
| Tools | smartmontools 7.5; H2testw 1.4; Hard Disk Sentinel Pro 6.40; CrystalDiskInfo 9.9.3 |
| Test dates | October 23–25, 2026; supplied logs use EDT |

Device numbers and drive letters are temporary. Identify this drive by model and serial before future operations.

## Preparation

The user confirmed Disk 1 was not the boot or system disk. E: was formatted NTFS and labeled BENCH-TEST before H2testw. The PowerShell format command did not request a full format; the later H2testw operation supplied the write/read verification.

## Completed tests

### H2testw available-space write and verification

Completed October 25, 2026.

```text
Warning: Only 488272 of 488383 MByte tested.
Test finished without errors.
You can now delete the test files *.h2w or verify them again.
Writing speed: 56.3 MByte/s
Reading speed: 520 MByte/s
H2testw v1.4
```

The test covered available filesystem space, not every physical NAND cell or every device LBA. Approximately 111 MByte was outside the tested allocation; no data mismatches were reported. The writing speed is a workload result, not a standalone diagnosis.

### Hard Disk Sentinel full-surface READ test

Completed October 25, 2026, 12:52:39 PM EDT; started 12:43:09 PM.

| Metric | Result |
|---|---|
| Passes | 1 of 1 |
| Coverage | 100% |
| Total sectors | 1,000,215,216 |
| Displayed block size | 100,024 sectors / 48.84 MB |
| Good blocks | 10,000 |
| Damaged blocks | 0 |
| Bad blocks | 0 |
| Duration | 00:09:29 |
| Completion speed display | 810.73 MB/s |
| Temperature at completion | 70°C |

Evidence: user-supplied screenshots named `image(20261025-165359).png` and `image(20261025-165422).png`. Screenshots were reviewed; image binaries are not stored in this record.

An exclusive-lock warning was bypassed for the READ test. The completed test reported no damaged or bad blocks. Concurrent activity can affect timing; the completion speed display should not be treated as a controlled benchmark.

## SMART comparison

Values below are transcribed from user-supplied smartctl reports. TB values are smartctl's rounded decimal displays.

| Metric | Oct 23, 17:33:51 | Oct 25, 12:01:48 | Final: Oct 25, 12:55:12 |
|---|---:|---:|---:|
| Overall assessment | PASSED | PASSED | PASSED |
| Critical warning | 0x00 | 0x00 | 0x00 |
| Temperature | 38°C | 36°C | 41°C |
| Available spare | 100% | 100% | 100% |
| Percentage used | 0% | 0% | 0% |
| Data read | 1.87 TB | 2.38 TB | 3.41 TB |
| Data written | 1.25 TB | 1.76 TB | 1.76 TB |
| Power-on hours | 56,141 | 56,184 | 56,185 |
| Power cycles | 139 | 139 | 139 |
| Unsafe shutdowns | 39 | 39 | 39 |
| Media/data-integrity errors | 0 | 0 | 0 |
| Error-information entries | 0 | 0 | 0 |
| Warning-temperature time | 0 | 0 | 0 |
| Critical-temperature time | 0 | 0 | 0 |
| Thermal Temp. 1 transitions | 111 | 480 | 519 |
| Thermal Temp. 1 total time, seconds | 3,667 | 5,572 | 5,819 |

The final report shows no new media errors, error-log entries, unsafe shutdowns, or temperature-warning time. Reported endurance usage of 0% is a device estimate; it does not mean the drive is new. Power-on time is approximately 6.4 years.

### Thermal follow-up

The surface-test graph displayed approximately 39°C initially, then an abrupt change to 70°C. The graph alone does not establish why the reading changed or prove a specific performance impact.

Between the last two SMART snapshots, thermal-management state 1 counters increased by **39 transitions and 247 seconds**. This is evidence of reported thermal-management activity. It does not by itself establish how much performance was affected. Final temperature had returned to 41°C. The reported warning and critical thresholds are 77°C and 80°C, respectively; their accumulated times remained zero.

**Deployment follow-up:** provide heatsink/airflow, verify ASUS card fan operation, and monitor temperature and thermal-management counters under the intended workload.

## Test unavailable through current Windows path

An attempted extended NVMe self-test returned:

```text
NVMe Self-test cmd with type=0x2, nsid=0xffffffff failed:
IOCTL_STORAGE_PROTOCOL_COMMAND(NVMe) failed, Error=1117
```

The command did not start successfully. All supplied self-test logs say no self-tests logged. This is **not a recorded failed self-test**. The cause of the command failure was not established; a driver or command-passthrough limitation remains possible.

## Final SMART snapshot

Captured October 25, 2026, 12:55:12 PM EDT using:

```powershell
& "C:\Program Files\smartmontools\bin\smartctl.exe" -x -d nvme /dev/sdb
```

```text
Model Number:                       INTEL SSDPEKNW512G8
Serial Number:                      PHNH852005YT512A
Firmware Version:                   002C
Namespace 1 Size/Capacity:          512,110,190,592 [512 GB]
SMART overall-health self-assessment test result: PASSED

Critical Warning:                   0x00
Temperature:                        41 Celsius
Available Spare:                    100%
Available Spare Threshold:          10%
Percentage Used:                    0%
Data Units Read:                    6,670,800 [3.41 TB]
Data Units Written:                 3,448,305 [1.76 TB]
Host Read Commands:                 51,718,506
Host Write Commands:                34,765,180
Controller Busy Time:               1,483
Power Cycles:                       139
Power On Hours:                     56,185
Unsafe Shutdowns:                   39
Media and Data Integrity Errors:    0
Error Information Log Entries:      0
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0
Thermal Temp. 1 Transition Count:   519
Thermal Temp. 1 Total Time:         5819

Error Information: No Errors Logged
Self-test status: No self-test in progress
No Self-tests Logged
```

## Intended reuse

Candidate for a new Unraid ZFS mirror with a WD Blue SN550 500 GB, after that drive is independently tested. Expected nominal mirrored capacity is limited by the smaller member, before filesystem overhead. Deployment and formatting have not occurred.

## Not performed or not confirmed

- Internal NVMe short/extended self-test: not completed.
- CrystalDiskMark benchmark: not performed.
- Post-reboot H2testw re-verification: previously discussed, not confirmed.
- Cooling improvements and testing in the final Unraid installation: pending.
