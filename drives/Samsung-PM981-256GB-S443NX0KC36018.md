# Samsung PM981 256 GB — S443NX0KC36018

Screening date: October 26, 2026 (EDT).

## Disposition

**Bench screening passed; candidate for reuse with adequate cooling.** Existing H2testw test files verified without error. The original Write + Verify completion dialog was dismissed without saving, so its write speed and original completion text are unavailable. No new media errors were reported. This screen does not guarantee future reliability.

## Identity

| Field | Value |
|---|---|
| Model | PM981 NVMe Samsung 256GB |
| Serial | S443NX0KC36018 |
| Firmware | EXD72D1Q |
| Capacity | 256,060,514,304 bytes |
| NVMe / sector size | 1.2 / 512 bytes |
| Link, baseline CrystalDiskInfo | PCIe 3.0 x4 current and supported |
| Bench | Dell Precision T3600, Windows 10 Pro 22H2 build 19045 |
| Tools | CrystalDiskInfo 9.9.3; H2testw 1.4; smartmontools 7.5 |
| Temporary test assignments | Disk 0; E:; /dev/sda, type nvme |

Disk numbering is not permanent. Confirm identity before future operations.

## Preparation and verification

User confirmed nothing needed saving. Identity-guarded cleaning/GPT initialization/NTFS quick-format instructions were supplied. Original H2testw Write + Verify completion was reported by the user but its result text was not retained. A subsequent Verify read the existing files:

```text
Warning: Only 244080 of 244181 MByte tested.
Test finished without errors.
Reading speed: 630 MByte/s
H2testw v1.4
```

The small 101 MByte difference is not itself a failure. H2testw tests available filesystem space, not metadata or spare NAND. Original write speed is unavailable; do not infer it from the later reading speed.

## SMART comparison

Baseline: CrystalDiskInfo_20261026080005.txt, internal timestamp 08:00:08 EDT.
Final: supplied smartctl -x output, 08:57:50 EDT.

| Metric | Baseline | Final |
|---|---:|---:|
| Health | Good 96% | PASSED |
| Critical warning | 0 | 0x00 |
| Available spare | 100% | 100% |
| Percentage used | 4% | 4% |
| Power-on hours | 5,169 | 5,170 |
| Power cycles | 5,136 | 5,136 |
| Unsafe shutdowns | 93 | 93 |
| Media/data-integrity errors | 0 | 0 |
| Error-information entries | 85 | 86 |
| Composite temperature | 38°C | 48°C |
| Warning/critical temperature time | 0 / 0 | 0 / 0 |

Final sensor 1: 48°C; sensor 2: 69°C. Sensor identities/locations were not established; peak temperature during testing was not captured. Reported composite warning/critical thresholds: 81°C / 82°C. Ensure airflow and monitor both sensors in deployment.

### Error-log interpretation

Visible final entries:

| Error count | Message |
|---|---|
| 86 | Invalid Log Page |
| 85 | Invalid Log Page |
| 84 | Invalid Field in Command |

The newest entry is a rejected diagnostic command, not a recorded media failure. Which tool issued it was not established. Only the visible entries were inspected; this does not explain every historical event.

### Historical self-tests

Six short tests in the final log completed without error at power-on hours 5,148 (two), 5,136, 4,941, 4,532 and 4,393. No new internal self-test was performed during this screening session.

## Final SMART counters

```text
Data Units Read:                 12,683,491 [6.49 TB]
Data Units Written:              44,034,216 [22.5 TB]
Host Read Commands:              191,972,094
Host Write Commands:             690,090,790
Controller Busy Time:            1,676
Power Cycles:                    5,136
Power On Hours:                  5,170
Unsafe Shutdowns:                93
Media and Data Integrity Errors: 0
Error Information Log Entries:   86
Warning Comp. Temperature Time:  0
Critical Comp. Temperature Time: 0
```

No separate Sentinel surface test or CrystalDiskMark benchmark was required. Intended deployment is not yet confirmed.

[Shared screening procedure](https://github.com/420tax/Hardware-Testing/blob/main/procedures/STREAMLINED-DISK-TESTING.md)
