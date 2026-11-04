# XFX GeForce 8800 GTS 640MB

Status: **Passed bench screening; suitable for reuse.**
Test evidence collected November 3–4, 2026 on the Dell Precision T3600 (Intel Xeon E5-2670).

## Physical identification

| Field | Observed value |
|---|---|
| Manufacturer | XFX / Pine Group |
| Ordering code | PV-T80G-THF4 |
| Revision | V2.0 |
| Serial number | I8F043376 |
| Label description | GF 8800GTS 500M 640MB DDR3 DUAL DVI TV |
| BIOS sticker | 60.80.13.00.80 |
| Additional barcode | 0063007351901 |
| PCB label | 600-10356-0001-151 F |
| Assembly label | 900-10356-0001-152 G |

Six supplied photographs document the front, rear, and identifying labels. Cooler has XFX dog artwork. “Alpha Dog Edition” is not established by the identifying label and is not used as the confirmed model designation. The TechPowerUp profile for the XFX 8800 GT XXX Alpha Dog Edition (PVT88PYDD4, G92, 512MB, 256-bit) describes a different card and must not be used for this inventory item.

## GPU-Z observations

| Field | Observed value |
|---|---|
| GPU | NVIDIA G80, revision A3 |
| Shader cores | 96 |
| TMUs / ROPs | 48 / 20 |
| Memory | 640MB GDDR3 |
| Memory bus | 320-bit |
| Memory bandwidth | 63.4GB/s |
| Core / shader / memory clocks | 513 / 1188 / 792MHz |
| Effective memory rate | 1584Mb/s |
| PCIe interface | PCIe 1.1 x16, operating at x16 1.1 |
| BIOS | 60.80.13.00.80 |
| Device ID | 10DE 0193 – 1682 2251 |
| Driver | NVIDIA 342.01; 21.21.13.4201 |
| DirectX hardware capability | DirectX 10 |
| OpenGL reported | 3.3 |

Clocks matched GPU-Z defaults; no overclock was applied. Physical label says 500M; GPU-Z reported 513MHz. These are retained as separate label and measured observations.

## Completed tests

### GPU-Z render check

Approximately 30 seconds completed without a crash or visible artifacts, as confirmed by the user.

### OCCT VRAM

- OCCT Personal 17.1.10.
- Completed 15:00 of 15:00; schedule completed.
- **No errors detected.**
- GPU temperature: minimum 51°C, average 52.42°C, maximum 57°C.
- Core 513MHz, shader 1188MHz, memory 792MHz.
- Fan reported 60%.
- Peak GPU memory allocated: 595MB; peak reported memory usage 92.90%.
- Screenshot: OCCT-26113-044209.png.
- Memory allocation and overall usage do not independently establish the exact number of bytes tested.

### UNIGINE Heaven 4.0

| Metric | Result |
|---|---|
| Score | 651 |
| Average FPS | 25.8 |
| Minimum FPS | 7.7 |
| Maximum FPS | 43.1 |
| Renderer | Direct3D 9 |
| Resolution | 1280 × 720, windowed |
| Preset | Custom |
| Quality | Medium |
| Tessellation | Disabled |
| Temperature visible in result screenshot | 76°C |

Benchmark completed without visual corruption or driver crashes, explicitly confirmed by the user. The 76°C reading is a screenshot observation, not a logged maximum. Anti-aliasing setting and elapsed duration are not established by the result screenshot.

Evidence: Unigine Benchmarki.PNG.

## Compatibility limitations

- FurMark 2.4.3.0 failed to open; no completed FurMark test.
- OCCT 3D Adaptive reported “no gpus supporting 3d rendering have been found”; no completed OCCT 3D test.
- These application compatibility limitations are separate from the successful Heaven rendering and OCCT memory results.

## Disposition and evidence scope

Passed the selected bench screening: GPU-Z rendering, 15-minute OCCT VRAM test, and Heaven benchmark. No additional surface or GPU stress test is required for this screening workflow. These results establish observed operation during the tests, not a prediction of remaining lifetime.

Source captures: 8800GTS GPU-Z 1.gif; 8800GTS GPU-Z 2.gif; OCCT-26113-044209.png; Unigine Benchmarki.PNG; six physical-card photographs supplied November 4, 2026. This record transcribes their results; the image binaries are not included in this commit.

The user-supplied overview lists a 143W maximum power specification. It was not independently verified here and is not measured test consumption.
