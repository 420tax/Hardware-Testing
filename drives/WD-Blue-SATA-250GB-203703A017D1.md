# WD Blue SATA SSD 250 GB — 203703A017D1

Record date: October 26, 2026 (EDT).

## Status

**H2testw write/verify and Sentinel surface READ passed.** Final SMART media/error counters remain clean. SMART error-log checksum warnings remain unresolved; an additional extended internal self-test was selected in Sentinel, but its result has not been supplied. Provisional reuse candidate pending that follow-up. This is a SATA drive, distinct from the WD SN550 NVMe drives.

## Identity

| Field | Value |
|---|---|
| Model, CrystalDiskInfo | WDC WDS250G2B0A-00SM50 (display includes extra spaces) |
| Serial | 203703A017D1 |
| Firmware | 401020WD |
| Capacity | 250,059,350,016 bytes |
| Interface | SATA |
| Negotiated / supported transfer mode | SATA/300 / SATA/600 |
| Bench | Dell Precision T3600, Windows 10 Pro 22H2 |
| Temporary assignments | Windows Disk 1; E:; /dev/sdb, type sat |
| Baseline tool | CrystalDiskInfo 9.9.3 |

The 3 Gb/s connection can limit measured performance. Disk numbers and device paths are temporary.

## Baseline

Sources: CrystalDiskInfo_20261026091722.txt and CrystalDiskInfo_20261026091731.txt, supplied before instructed H2testw testing.

| Metric | Value |
|---|---:|
| Health | Good 100% |
| Temperature | 27°C |
| Power-on hours | 409 |
| Power cycles | 213 |
| Host reads | 25 GB as displayed |
| Host writes | 22 GB as displayed |
| Reassigned blocks | 0 |
| Grown bad blocks | 0 |
| Program / erase failures | 0 / 0 |
| Reported uncorrectable errors | 0 |
| End-to-end errors | 0 |
| Command timeouts | 0 |
| CRC errors | 0 |
| Unexpected power losses | 1 |
| Available reserve space, normalized | 100 |
| Total Bad Block, raw vendor attribute A9 | 83 |
| Maximum Bad Blocks per die, raw attribute A7 | 22 |

The nonzero vendor bad-block attributes are preserved as baseline values; their precise vendor meaning has not been independently established. They should not be conflated with the zero grown/reassigned block counts or described as newly failed sectors.

## Preparation

User authorized erasing this test drive. Instructions were supplied to initialize GPT and create a full-size NTFS E: test volume. Formatting output was not supplied.

## H2testw Write + Verify

```text
Warning: Only 238357 of 238458 MByte tested.
Test finished without errors.
You can now delete the test files *.h2w or verify them again.
Writing speed: 208 MByte/s
Reading speed: 209 MByte/s
H2testw v1.4
```

Passed for the tested filesystem space. This does not test spare NAND or every physical cell. The small untested difference alone is not an error.

## Final smartctl report — October 26, 2026, 11:46:26 EDT

smartctl 7.5; overall assessment PASSED; SATA negotiated 3.0 Gb/s, supported 6.0 Gb/s.

| Metric | Final |
|---|---:|
| Power-on hours | 411 |
| Power cycles | 213 |
| Temperature | 25°C (reported min/max 16/37°C) |
| Reallocated / grown bad blocks | 0 / 0 |
| Program / erase failures | 0 / 0 |
| End-to-end / reported uncorrectable errors | 0 / 0 |
| Command timeouts / CRC errors | 0 / 0 |
| Unexpected power losses | 1 |
| Reserve space, normalized | 100 |
| Total bad blocks / max bad blocks per die, vendor raw | 83 / 22 |
| Host writes / reads, SMART attributes 241/242 | 255 / 258 GiB |
| NAND GB written TLC / SLC | 241 / 259 |
| Device statistics endurance percentage used | 0 |

Relevant failure counters and vendor bad-block counts did not increase from baseline. Attribute 230 raw 0x000800000008 is retained without interpreting its packed vendor value as a failure or a remaining-life percentage.

**Log qualification:** both the extended comprehensive SMART error log and the separately requested standard ATA error log returned **invalid SMART checksum** warnings. Both also displayed “No Errors Logged,” but that output is not a fully trustworthy clean-log result given the checksum warnings. Cause is unresolved; this is not by itself proof of failed media.

Six historical short self-tests completed without error at 406, 375, 232, 137, 134 and 4 power-on hours. These are historical, not a new extended-test result.

## Hard Disk Sentinel surface READ

Completion screenshot Sentinal.PNG:
- October 26, 2026, 13:42:46–14:00:40; duration 17 minutes 54 seconds.
- 100% complete: **10,000 good blocks, 0 damaged, 0 bad**.
- No new reallocations reported; displayed health 100%, temperature 33°C.
- Completion speed display 237.02 MB/s; retained as reported, not a controlled benchmark.

## Follow-up

An extended internal self-test was chosen in Hard Disk Sentinel after discussion of the checksum warnings. **Result pending; do not mark it passed without the completion result.** Preserve these warnings in any deployment record.

[Shared screening procedure](https://github.com/420tax/Hardware-Testing/blob/main/procedures/STREAMLINED-DISK-TESTING.md)
