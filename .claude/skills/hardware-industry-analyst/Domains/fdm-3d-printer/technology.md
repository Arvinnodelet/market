# FDM 3D Printer Technology Subsystems

> 本文件定义 FDM 3D 打印机的技术评估维度。评估方法论见 `Frameworks/technology.md`。

---

## Subsystem Assessment Summary

| Subsystem | Assessment | Key Metrics to Assess |
|---|---|---|
| **Motion System** | | Kinematics type, max speed (mm/s), max accel (mm/s²), rigidity, vibration control, belt/pulley quality |
| **Extrusion System** | | Extruder type (Bowden/DD/Dual-Gear/Servo), grip reliability, retraction quality, closed-loop capability |
| **Hotend System** | | Max flow rate (mm³/s), max temp (°C), heat-up time, clog resistance, nozzle swap ease, heater technology |
| **Sensor System** | | Bed leveling method, Z-offset, filament sensors, AI camera, calibration automation, sensor fusion |
| **Electronics** | | MCU architecture (single/dual/3-layer), step rate, connectivity, custom silicon, motor driver quality |
| **Firmware** | | Performance, flexibility, update cadence, input shaping, pressure advance, closed/open source |
| **Software Ecosystem** | | Slicer quality, mobile app, cloud platform, content marketplace, API/SDK |

> 详细评估标准见各 Knowledge 模块。定性标签：Leading / Competitive / Behind。

---

## Evaluation Dimensions (per Subsystem)

对每个子系统评估：

| Criterion | Weight | 3DP-Specific Assessment |
|---|---|---|
| **Performance** | 30% | Raw metrics vs segment peers at same price tier |
| **Innovation** | 20% | Self-developed (moat) vs off-the-shelf (copyable) |
| **Reliability** | 20% | Field failure rate, known clog/jam/calibration issues |
| **Cost Efficiency** | 15% | Performance per BOM ¥ vs competitors |
| **Manufacturability** | 15% | Assembly complexity, calibration burden, automation potential |

---

## Architecture Assessment

| Architecture Pattern | MCU | Speed | AI Capable | Cost | Examples |
|---|---|---|---|---|---|
| **MCU Only (8-bit)** | ATmega2560 | ≤100K steps/s | No | Very Low | Ender 3 (classic) |
| **MCU Only (32-bit)** | STM32/GD32 | ≤150K steps/s | No | Low | Ender 3 V2, budget |
| **Linux SoC + MCU** | Allwinner/RPi + STM32 | 300K+ steps/s | Cloud-dependent | Medium | Klipper, Creality K1 |
| **AP + MC + TH (3-layer)** | RV1126 + SPC2168 + SPC1168 | 300K+ steps/s | Edge NPU | High | Bambu Lab |

---

## Key Engineering Tradeoffs (3DP-Specific)

1. **Speed vs Quality** → Higher speed (600+ mm/s) requires input shaping + pressure advance + rigid frame; neglected = ghosting
2. **Open vs Closed Ecosystem** → Open (Klipper/Marlin) = community mods, lower lock-in; Closed (Bambu OS) = better OOBE, higher lock-in
3. **Multi-Material vs Waste** → AMS/CFS enable 16-color but produce 50–200g purge waste per color change; IDEX = zero waste but 2× hotend cost
4. **Flow Rate vs Material Range** → Higher flow (40+ mm³/s) needs higher wattage (100W+) and bigger melt zone; risk of filament degradation at low speeds
5. **Build Volume vs Footprint** → CoreXY is compact; Bedslinger needs 2× Y depth; larger volume = lower rigidity unless frame upgraded
6. **Self-Developed vs Off-the-Shelf** → Custom chips (Bambu Spintrol) = moat + optimization; off-the-shelf STM32 = faster time-to-market + easier to copy
