# Robot Vacuum Technology Subsystems

> 本文件定义扫地机器人的技术评估维度。评估方法论见 `Frameworks/technology.md`。

---

## Subsystem Assessment Summary

| Subsystem | Assessment | Key Metrics to Assess |
|---|---|---|
| **Navigation** | | Technology type (LiDAR/vSLAM/dToF/hybrid), mapping speed, accuracy in dark rooms, recovery behavior |
| **Cleaning System** | | Main brush type (rubber/brush/combo), suction power (Pa), mopping type (vibrating/rotary/roller), edge cleaning coverage |
| **Sensor System** | | Obstacle avoidance type (3D structured light/line laser/RGB camera/IR), cliff sensors, dirt detection, carpet recognition accuracy |
| **Mapping & Software** | | Map precision, room segmentation, multi-floor support, virtual walls, app polish, voice assistant integration |
| **Base Station** | | Features (charge/empty/wash/dry/refill), dust bag capacity, water tank size, drying temperature, maintenance burden |
| **Firmware** | | RTOS/OS choice, navigation stack quality, OTA update cadence, algorithm efficiency |

> 定性标签：Leading / Competitive / Behind。

---

## Evaluation Dimensions (per Subsystem)

| Criterion | Weight | Robot Vacuum-Specific Assessment |
|---|---|---|
| **Performance** | 30% | Raw metrics vs segment peers at same price tier |
| **Innovation** | 20% | Self-developed navigation algorithm? Proprietary sensor? Unique mechanical design? |
| **Reliability** | 20% | Field failure rate, navigation errors, base station clogging, sensor failure |
| **Cost Efficiency** | 15% | Performance per BOM ¥ vs competitors |
| **Manufacturability** | 15% | Assembly complexity, sensor calibration burden, quality consistency at scale |

---

## Architecture Assessment

| Architecture Pattern | Navigation | Processing | Cost | Examples |
|---|---|---|---|---|
| **LDS Only (budget)** | Single LiDAR turret | MCU only | Low | Xiaomi E series, entry-level |
| **LDS + Structured Light** | LiDAR + IR laser/line laser | MCU + modest SoC | Medium | Roborock Qrevo series |
| **LDS + RGB Camera + LED** | LiDAR + visual obstacle | SoC with NPU | Medium-High | Roborock S8, Dreame L20 |
| **LDS + RGB + 3D dToF** | LiDAR + dual vision | SoC with NPU + ISP | High | Roborock S8 MaxV, Dreame X40 |
| **vSLAM Only** | Camera-only (no turret) | SoC with strong ISP | Medium | iRobot Roomba j9, budget Dreame |

---

## Key Engineering Tradeoffs (Robot Vacuum-Specific)

1. **LiDAR vs vSLAM** → LiDAR = fast mapping + works in dark, but mechanical turret is wear-prone; vSLAM = no moving parts + furniture detail, but needs light + lower precision
2. **Suction Power vs Battery Life** → Higher Pa = more power draw; most bots now throttle suction based on surface type
3. **Mopping Depth vs Maintenance** → Rotary mops clean better but need base station washing; vibrating mops simpler but less deep clean
4. **Base Station Features vs Size** → Full-feature stations (wash+dry+empty+refill) are >50cm tall; trade-off between features and home aesthetics
5. **Edge Cleaning vs Coverage Speed** → Rotating side brushes reach corners but fling debris; extending arms solve this but add mechanical complexity
6. **Obstacle Avoidance Sensitivity vs Completeness** → Over-aggressive avoidance leaves uncleaned areas; under-aggressive leads to cord tangling
7. **Cloud vs Edge AI** → Object recognition on-device = privacy + low latency; cloud = better models but latency + subscription dependency
