# WD Blue WD5000AZLX 500GB — WD-WCC6Z6RC35JN

## Identity and test setup
- Model: WDC WD5000AZLX-75K2TA0 (CMR mechanical HDD)
- Serial: WD-WCC6Z6RC35JN
- Firmware: 02.01A02
- Capacity: 500,107,862,016 bytes; 3.5-inch, 7200 RPM
- Sectors: 512-byte logical / 4096-byte physical
- Connection: T3600 Intel C600 SATA AHCI, SATA1, negotiated 6 Gb/s
- Windows 10 Pro 22H2; test volume D:
- Test date: November 3, 2026
- Existing root contents: $RECYCLE.BIN and System Volume Information only.

## Results
**PASS — suitable for bench reuse. Testing complete; no additional surface scan required.**

### Internal self-test
Extended offline completed without error, 0% remaining, at 26,340 lifetime hours; no failing LBA. Earlier short tests also passed.

### H2testw 1.4
```text
Warning: Only 476826 of 476937 MByte tested.
Test finished without errors.
Writing speed: 128 MByte/s
Reading speed: 128 MByte/s
```
This verifies the tested available filesystem space, rather than every physical sector.

### SMART comparison
| Counter | Baseline | Final |
| --- | ---: | ---: |
| Power-on hours | 26,339 | 26,344 |
| Power cycles | 423 | 423 |
| Start/stop count | 426 | 426 |
| Load/unload cycles | 200,065 | 200,069 |
| Power-off retract count | 71 | 71 |
| Temperature | 22°C | 24°C |
| Reallocated sectors/events | 0 / 0 | 0 / 0 |
| Pending sectors | 0 | 0 |
| Offline uncorrectable | 0 | 0 |
| Raw read/seek errors | 0 / 0 | 0 / 0 |
| Spin/calibration retries | 0 / 0 | 0 / 0 |
| Multi-zone/write error raw count | 0 | 0 |
| UDMA CRC errors | 63 | 63 |

The 63 CRC errors are a historical interface-error count and did not increase through qualification. No new media or interface errors were recorded. Exact cause of the historical CRC errors is unconfirmed. Final seek normalized VALUE/WORST was 100/253 with raw 0; retained as reported, not interpreted as a new raw error.

Final raw counters: head flying hours 24,409; total LBAs written 43,029,399,053; total LBAs read 32,691,188,033.

## Evidence
User-supplied smartctl 7.5 identity, self-test log and pre/post attributes; CrystalDiskInfo 9.9.3 export CrystalDiskInfo_20261103072606.txt; H2testw completion report. CrystalDiskInfo baseline status Good. A passing qualification does not establish remaining lifetime.
