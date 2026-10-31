# Toshiba MQ01ABD032 320GB — Z2H4FUWES

Testing: 2026-10-30 through 2026-10-31 (America/New_York)

## Disposition

PASS for bench reuse under the streamlined testing procedure. Extended SMART self-test and H2testw write-and-verify completed without errors; post-test media error counters remained zero and the historical CRC counter remained at one. CrystalDiskMark completed. No additional surface scan required unless new errors or symptoms appear. Test results do not guarantee future reliability.

## Identity

| Field | Value |
|---|---|
| Device type | Mechanical HDD |
| Model | TOSHIBA MQ01ABD032 |
| Serial | Z2H4FUWES |
| Manufacturing date | 2012-12-17, printed on label |
| Capacity | 320,072,933,376 bytes |
| Form factor | 2.5 inches |
| Rotation speed | 5400 RPM |
| Firmware | AX001A |
| Interface / negotiated link | SATA 3 Gb/s / 3 Gb/s |
| Sector sizes | 512 bytes logical / 4096 bytes physical (512e) |
| Buffer | 8192 KB, reported by CrystalDiskInfo |
| Test host | Dell Precision T3600, Windows 10 Pro 22H2 |
| Controller | Intel C600 SATA AHCI |
| Test volume | D:, NTFS, approximately 298 GiB |

Firmware update availability has not been verified. The Toshiba utility support list supplied by the owner did not include this model. No firmware update was performed.

## Preparation

Windows identified the Toshiba as non-boot/non-system Disk 1. Existing GPT layout: reserved partition 16,759,808 bytes; basic partition 320,054,755,328 bytes. The basic partition was mounted as D: and reported healthy NTFS. Root listing showed only System Volume Information; the offline Windows SOFTWARE hive path was absent. The existing filesystem was used without reformatting.

Disk numbers and drive letters may change; identify by serial before destructive actions. The final CrystalDiskInfo export contains no drive letter, although H2testw and CrystalDiskMark were run on the identified D: volume during this session.

## SMART baseline and comparisons

| Metric | Baseline Oct 30 | After extended test | After H2testw / final CDI |
|---|---:|---:|---:|
| Power-on hours | 19,158 | 19,169 | 19,171 |
| Power cycles | 415 | 415 | 415 |
| Start/stop count | 415 | 415 | 415 |
| Read error raw count | 0 | 0 | 0 |
| Seek error raw count | 0 | 0 | 0 |
| Reallocated sectors | 0 | 0 | 0 |
| Reallocation events | 0 | 0 | 0 |
| Pending sectors | 0 | 0 | 0 |
| Offline uncorrectable sectors | 0 | 0 | 0 |
| Spin retries | 0 | 0 | 0 |
| UDMA CRC errors | 1 | 1 | 1 |
| G-Sense raw count | 6946 | 6946 | 6946 |
| Power-off retract count | 48 | 48 | 48 |
| Load/unload cycle count | 167121 | 167121 | 167121 |
| Current temperature | 23 C | 23 C | 27 C |
| Loaded hours | 9781 | 9792 | 9794 |

Recorded temperature minimum/maximum: 18 / 64 C. CrystalDiskInfo health: Good. Hard Disk Sentinel baseline: 100% health and 100% performance. Sentinel's estimated remaining lifetime is a software estimate, not a warranty or lifespan prediction.

One historical CRC event was present before testing and did not increase. The earlier Sentinel Overview's general statement of no transfer errors should not override this raw counter. G-Sense and load-cycle counts are retained as historical context; their raw counts alone do not establish media failure.

## Internal self-tests

Log retrieved 2026-10-31 08:13:42:

| Test | Result | Remaining | Lifetime hours | First failing LBA |
|---|---|---:|---:|---|
| Extended offline (latest) | Completed without error | 0% | 19,159 | None |
| Extended offline (earlier attempt) | Aborted by host | 90% | 19,158 | None reported |
| Short captive (historical) | Completed without error | 0% | 19,156 | None |

The completed extended test was initiated through Hard Disk Sentinel with an estimated 82-minute duration. The earlier interrupted attempt is not a pass; a subsequent completed pass is recorded.

## H2testw 1.4

All available space, Write + Verify.

| Measurement | Result |
|---|---|
| Tested | 305,124 of 305,227 MByte (H2testw units) |
| Result | Test finished without errors |
| Write speed | 77.7 MByte/s |
| Read speed | 78.5 MByte/s |

The test verifies available file space; it is not a claim to have tested every physical sector, reserved area or inaccessible remapped location.

## CrystalDiskMark 9.0.3 x64

2026-10-31 10:34:57. Default profile, 1 GiB x3, D: 0% used (0/298 GiB), administrator mode, 5-second measurement / 5-second interval.

| Test | Read MB/s | Write MB/s |
|---|---:|---:|
| Sequential 1 MiB, Q8 T1 | 97.522 | 97.128 |
| Sequential 128 KiB, Q32 T1 | 97.623 | 97.174 |
| Random 4 KiB, Q32 T16 | 0.982 | 1.043 |
| Random 4 KiB, Q1 T1 | 0.485 | 1.060 |

| Random test | Read IOPS | Write IOPS |
|---|---:|---:|
| 4 KiB, Q32 T16 | 239.7 | 254.6 |
| 4 KiB, Q1 T1 | 118.4 | 258.8 |

The benchmark export does not include a model/serial; attribution follows the identified D: Toshiba volume in this test session. Small random I/O is substantially slower than the tested SSDs; integrity results and performance suitability are separate judgments.

## Evidence supplied

- Drive-label photograph: image-1793407065331.jpg
- CaptureT1.PNG — Hard Disk Sentinel Overview
- Capturet2.PNG — Hard Disk Sentinel SMART
- CrystalDiskInfo_20261030205038.txt — baseline
- smartctl identity/self-test log and subsequent SMART outputs pasted in conversation
- H2testw completion text pasted in conversation
- CrystalDiskInfo_20261031102932.txt — final SMART confirmation
- CrystalDiskMark_20261031103453.txt

These filenames identify supplied evidence. Binary attachments are not uploaded by this Markdown record.

## Reuse notes

Suitable for bench experiments or bulk-file storage based on these completed checks. Its low random-I/O throughput makes it a poor performance choice for an OS, applications or active VMs. Continue monitoring SMART, especially sector counters and changes from the CRC baseline of one. H2testw files may be deleted after the results are retained.
