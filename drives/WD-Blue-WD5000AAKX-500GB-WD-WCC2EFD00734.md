# WD Blue WD5000AAKX 500GB — WD-WCC2EFD00734

## Identity and test setup
- Model: WDC WD5000AAKX-75U6AA0 (CMR mechanical HDD)
- Serial: WD-WCC2EFD00734
- WWN: 5 0014ee 25dda8990
- Firmware: 19.01H19 (confirmed directly over SATA)
- Capacity: 500,107,862,016 bytes; 512-byte logical/physical sectors
- Buffer: 16,384 KB
- Connection: T3600 Intel C600 SATA AHCI, SATA1, negotiated 6 Gb/s
- Windows 10 Pro 22H2; volume D:
- Tests completed November 2, 2026; record added November 3
- Root inspection showed only System Volume Information.

## Results
**PASS — suitable for bench reuse. Testing complete; no additional surface scan required.**

### Internal self-test
Extended offline completed without error, 0% remaining, at 39,974 lifetime hours; no failing LBA. Historical short tests passed. An earlier extended test was aborted by host at 39,052 hours, superseded by the completed extended test.

### H2testw 1.4
```text
Warning: Only 476812 of 476923 MByte tested.
Test finished without errors.
Writing speed: 93.2 MByte/s
Reading speed: 95.1 MByte/s
```
Coverage is the tested available filesystem space, not every physical sector.

### SMART comparison
| Counter | Baseline | Final |
| --- | ---: | ---: |
| Power-on hours | 39,976 | 39,980 |
| Power cycles | 134 | 134 |
| Start/stop count | 136 | 136 |
| Load/unload cycles | 106 | 106 |
| Power-off retract count | 69 | 69 |
| Temperature | 32°C | 32°C |
| Reallocated sectors/events | 0 / 0 | 0 / 0 |
| Pending sectors | 0 | 0 |
| Offline uncorrectable | 0 | 0 |
| Raw read/seek errors | 0 / 0 | 0 / 0 |
| Spin/calibration retries | 0 / 0 | 0 / 0 |
| UDMA CRC errors | 0 | 0 |
| Multi-zone/write error raw count | 0 | 0 |

Final raw counters: head flying hours 37,680; total LBAs written 38,473,779,137; total LBAs read 39,150,823,152. Final seek normalized VALUE/WORST was 100/253 with raw 0; retained as reported, not interpreted as a new raw error.

## USB diagnostic limitation
Initial dock report lacked SMART attributes and logs, reported incomplete ATA status registers and a different firmware string (13501070). Direct SATA supplied complete data and firmware 19.01H19; the incomplete USB output was not used to assess drive health.

## Evidence
User-supplied smartctl 7.5 identity, self-test and pre/post attributes; H2testw completion report; WD Capture.PNG and CrystalDiskInfo_20261102171346.txt (November 2, 17:13:48). Final CrystalDiskInfo status Good and counters agree with smartctl. A passing qualification does not establish remaining lifetime.
