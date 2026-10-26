# WD Blue SATA SSD 250 GB — 203703A017D1

Record date: October 26, 2026 (EDT).

## Status

**Baseline captured; screening not complete.** No H2testw completion result or post-test SMART report has been supplied for this SATA drive. Do not confuse it with the WD SN550 NVMe drives recorded on the NVME branch.

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

## Preparation and remaining work

User authorized erasing the test drives. Instructions were supplied to clean this drive, initialize GPT, and create a full-size NTFS E: volume labeled TEST-WD-SATA. Formatting output was not supplied.

- [ ] H2testw all available space, Write + Verify; save result.
- [ ] Final SMART; compare media errors, grown/reassigned blocks, CRC and other counters.
- [ ] Record disposition and intended reuse.

[Shared screening procedure](https://github.com/420tax/Hardware-Testing/blob/main/procedures/STREAMLINED-DISK-TESTING.md)
