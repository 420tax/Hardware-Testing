# Samsung 860 EVO 500GB — S3Z1NB0M265385E

Updated: 2026-10-30 (America/New_York)

## Status

Extended SMART self-test passed. SMART media and interface error counters are clean. Samsung Magician performance benchmark completed. Hard Disk Sentinel Read surface test is pending completion; an earlier run was aborted for a firmware update and is not a completed pass. Full write/read verification (H2testw) is not recorded for this drive.

## Identity and current configuration

| Field | Value |
|---|---|
| Model | Samsung SSD 860 EVO 500GB |
| Serial | S3Z1NB0M265385E |
| Capacity | 500,107,862,016 bytes |
| Form factor | 2.5-inch SATA SSD |
| Logical/physical sector size | 512 / 512 bytes |
| Previous firmware | RVT02B6Q |
| Current firmware | RVT04B6Q |
| Firmware confirmation | Samsung Magician screenshot shows latest version, Samsung authenticated, no reported compatibility issue |
| Connection | Dell Precision T3600 SATA1, Intel C600 SATA AHCI controller |
| Negotiated link | SATA 6 Gb/s |
| AHCI | Activated, confirmed in Magician |
| Current filesystem | GPT / NTFS, TEST-SAMSUNG |
| Drive letter at testing | D: |
| Role | Standalone spare / bench testing |

Disk numbers and drive letters may change. Identify by serial before any destructive operation.

## RAID history and conversion to standalone

Previously a member of the T3600 Intel RSTe RAID1 Volume0, paired with Samsung serial S3Z1NB0M265508Z. The original controller reported the mirror failed and both members as Error Occurred; the cause has not been established.

This drive initially remained exposed as Intel Raid 1 Volume through the SCU. Moving it from HDD3 to SATA1 did not by itself remove that presentation: Windows controller association showed the Intel volume under the SATA AHCI controller as well.

The spare was connected through a USB dock, brought online, cleared with Clear-Disk, initialized GPT, and quick-formatted NTFS. After returning to SATA1, Get-Disk identified both Samsungs individually at their full 500,107,862,016-byte capacities; the Intel RAID volume was no longer listed. This verifies current standalone presentation, not a forensic check that every old metadata byte was erased.

The working Windows disk ending 5508Z was retained on SATA0. No BIOS RAID Delete/Reset operation was performed as part of this conversion.

## SMART evidence

Baseline smartctl report: 2026-10-30 13:54:52, firmware RVT02B6Q.

| Metric | Baseline | Later Magician export |
|---|---:|---:|
| Power-on hours | 56,413 | 56,416 |
| Power cycles | 273 | 278 |
| Wear leveling normalized value | 72 | 72 |
| Wear leveling raw count | 418 | 418 |
| Reallocated sectors | 0 | 0 |
| Used reserved blocks | 0 | 0 |
| Program failures | 0 | 0 |
| Erase failures | 0 | 0 |
| Runtime bad blocks | 0 | 0 |
| Uncorrectable errors | 0 | 0 |
| ECC error raw counter | 0 | 0 |
| CRC errors | 0 | 0 |
| POR recovery count | 155 | 156 |
| Total LBAs written | 81,126,355,750 | 81,126,793,169 |
| Temperature | 22 C | 27 C |

Baseline SMART overall status: PASSED. Extended error log: no errors logged.
Device Statistics reported 29% endurance used. CrystalDiskInfo reported Good (72%), 38,684 GB host writes, 34 C and 56,416 hours at 16:39. Preserve each tool's reporting conventions; the health percentage is not a forecast of remaining operating years.

Baseline transport statistics also showed 1,056 hardware resets and one reset between command acceptance and completion. These counts do not establish the cause of the RAID failure; interface CRC errors were zero.

## Internal self-tests

| Test | Result | Power-on hours |
|---|---|---:|
| Extended offline, 2026-10-30 | Completed without error, 0% remaining, no failing LBA | 56,414 |
| Earlier short offline | Completed without error, no failing LBA | 56,317 |

The extended test was run before the firmware update. No repeat extended test is recorded after updating.

## Samsung Magician benchmark

2026-10-30 16:58:29. D: TEST-SAMSUNG, 1 GB, 6 times. Direct SATA AHCI connection.

| Measurement | Result | Settings |
|---|---:|---|
| Sequential read | 535 MB/s | 128 KB, QD32, 1 thread |
| Sequential write | 502 MB/s | 128 KB, QD32, 1 thread |
| Random read | 33,447 IOPS | 4 KB, QD32, 1 thread |
| Random write | 28,076 IOPS | 4 KB, QD32, 1 thread |

This is a performance benchmark, not full-capacity integrity verification.

## Hard Disk Sentinel surface test

Read test: awaiting completed report. Earlier attempts were interrupted; do not record them as passes. Final good/damaged/bad block counts, read errors, elapsed time and transfer rates have not yet been supplied.

## Evidence supplied

- smartctl full report: Pasted text(20261030-175537).txt
- smartctl self-test log pasted in conversation: extended pass at 56,414 hours
- CrystalDiskInfo_20261030163932.txt
- Magician SMART 5385E.csv
- Magician Performance Banchmark 5385E.png
- Magician Firmware 5385E.PNG

Evidence filenames identify user-supplied reports; binary attachments are not uploaded by this Markdown entry.

## Assessment

Candidate for bench reuse based on clean SMART media counters, passed extended self-test and completed benchmark. Surface-test completion remains outstanding. The failed RAID status alone does not prove SSD failure or SCU hardware failure.
