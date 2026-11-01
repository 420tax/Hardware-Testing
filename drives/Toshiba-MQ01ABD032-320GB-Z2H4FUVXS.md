# Toshiba MQ01ABD032 320GB — Z2H4FUVXS

Testing: 2026-10-31 through 2026-11-01 (America/New_York).

## Disposition

PASS for bench reuse under the streamlined procedure. Extended internal self-test and H2testw write-and-verify completed without errors. Reallocated, pending, uncorrectable-sector and CRC counters stayed at zero. No additional surface scan required unless new errors or symptoms appear. No CrystalDiskMark result was supplied for this drive; the benchmark for serial Z2H4FUWES belongs to the other Toshiba. Passing tests do not guarantee future reliability.

## Identity and setup

| Field | Value |
|---|---|
| Type | Mechanical HDD |
| Model | TOSHIBA MQ01ABD032 |
| Serial | Z2H4FUVXS |
| WWN | 5 000039 47690603d |
| Firmware | AX001A |
| Capacity | 320,072,933,376 bytes |
| Form factor | 2.5 inches |
| Rotation | 5400 RPM |
| Sector sizes | 512 bytes logical / 4096 bytes physical |
| Interface / negotiated link | SATA 3 Gb/s / 3 Gb/s |
| Buffer (CrystalDiskInfo) | 8192 KB |
| Host | Dell Precision T3600, Windows 10 Pro 22H2 |
| Controller | Intel C600 SATA AHCI |
| Volume | D:, existing partition of 320,070,483,968 bytes |

Windows identified the drive as non-boot/non-system Disk 1. Root inspection showed only $RECYCLE.BIN and System Volume Information. Existing filesystem was used for testing. No clearing or reformatting operation is recorded for this session. Disk numbers and drive letters can change; identify by serial.

No firmware update was performed or verified as available.

## SMART comparison

Baseline: smartctl identity/attributes/self-test output, 2026-10-31 10:41:55.
Final: smartctl attributes pasted after H2testw, and CrystalDiskInfo_20261101152850.txt.

| Metric | Before | After |
|---|---:|---:|
| Power-on hours | 12,535 | 12,565 |
| Start/stop count | 342 | 342 |
| Power cycles | 269 | 269 |
| Reallocated sectors | 0 | 0 |
| Reallocation events | 0 | 0 |
| Pending sectors | 0 | 0 |
| Offline uncorrectable sectors | 0 | 0 |
| Read error raw count | 0 | 0 |
| Seek error raw count | 0 | 0 |
| Spin retries | 0 | 0 |
| UDMA CRC errors | 0 | 0 |
| G-Sense raw count | 13,210 | 13,210 |
| Power-off retract count | 34 | 34 |
| Load/unload cycles (smartctl samples) | 160,078 | 160,702 |
| Loaded hours | 7,239 | 7,245 |
| Current temperature | 21 C | 27 C |

Historical temperature range: 18–59 C.
Final CrystalDiskInfo health: Good. Its load-cycle raw value 0x273BF is 160,703, one cycle above the preceding smartctl sample; this is a later observation, not a media-error counter. Final firmware remains AX001A. APM is enabled at 0080h.

Historical G-Sense and load-cycle counts are recorded for context; they do not on their own establish a current failure.

## Internal self-tests

Log retrieved 2026-11-01 13:12:12 EST:

| Test | Result | Remaining | Lifetime hours | Failing LBA |
|---|---|---:|---:|---|
| Extended offline | Completed without error | 0% | 12,536 | None |
| Earlier short captive | Completed without error | 0% | 12,477 | None |

Extended test initiated through Hard Disk Sentinel. Result retrieved through smartctl without repeating the test.

## H2testw 1.4

All available space, Write + Verify, D: volume.

| Measurement | Result |
|---|---|
| Tested | 305,139 of 305,242 MByte (H2testw units) |
| Result | Test finished without errors |
| Write speed | 79.2 MByte/s |
| Read speed | 80.2 MByte/s |

This verifies the tested available file space, not every reserved sector or inaccessible remapped location. The 103 MiB untested difference is recorded explicitly. No separate surface-test pass is claimed.

## Evidence supplied

- CrystalDiskInfo_20261031104137.txt — baseline export
- smartctl baseline identity, attributes and earlier self-test log pasted in conversation
- smartctl completed extended self-test log pasted in conversation
- H2testw completion text pasted in conversation
- smartctl post-H2testw attributes pasted in conversation
- CrystalDiskInfo_20261101152850.txt — final confirmation

These filenames identify user-supplied evidence; binary attachments are not uploaded by this Markdown entry.

## Reuse notes

Testing complete for bench reuse. Retain the zero sector/CRC counts as the comparison baseline for future monitoring. H2testw files can be deleted after results are retained. Calendar manufacturing date has not been verified for this specific unit.
