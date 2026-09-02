# Firmware & Electronics Knowledge Base

## Purpose

Evaluate the embedded software and electronics architecture that powers robot vacuums — real-time OS choices, navigation stack, processor selection, motor control, and OTA update capability.

---

# Processor Architecture

## Architecture Tiers

| Tier | Processor(s) | Performance | AI Capability | Cost | Examples |
|---|---|---|---|---|---|
| **MCU Only** | STM32 / GD32 (Cortex-M4) | Limited | No | Very Low | Budget < $200 |
| **MCU + Basic SoC** | MCU + Allwinner/MediaTek A-series | Medium | Cloud-dependent | Low-Medium | Mid-range |
| **MCU + SoC + NPU** | MCU + Qualcomm/MediaTek + NPU | High | On-device AI | Medium-High | Premium |
| **MCU + SoC + ISP + NPU** | Dedicated sensor processor + NPU | Very High | Full on-device AI | High | Flagship |

## Common Processors

| Processor | Type | Key Features | Used By |
|---|---|---|---|
| **STM32F4/GD32** | Cortex-M4 MCU | Real-time motor control, sensor polling | All robots (MCU layer) |
| **Allwinner V/A-series** | Cortex-A7 SoC | Low-cost Linux host, basic ISP | Mid-range bots |
| **MediaTek Genio** | Cortex-A55 + NPU | Integrated NPU for AI, ISP for camera | Dreame mid/premium |
| **Qualcomm QCS/QCM** | Kryo + Hexagon NPU | High-end AI + ISP, 5G optional | Roborock S8 MaxV |
| **Rockchip RV series** | Cortex-A + NPU | Cost-effective AI, 2.0 TOPS NPU | Ecovacs, some Dreame |

---

# Real-Time Control Architecture

```
Application Processor (Linux/Android)
├── Navigation SLAM stack
├── AI Inference (obstacle detection, room recognition)
├── Map management
├── App communication (WiFi/BLE)
├── OTA update agent
├── Voice assistant interface
└── Cloud sync

            │ (UART/SPI/CAN)
            ▼

Real-Time MCU (Bare-metal / RTOS)
├── Motor control (BLDC FOC — 6+ motors)
│   ├── Left wheel
│   ├── Right wheel
│   ├── Main brush
│   ├── Side brush
│   ├── Suction fan
│   └── Mop lift / Mop motor
├── Sensor polling (100–1000 Hz)
│   ├── Cliff sensors
│   ├── Ultrasonic
│   ├── IR bumper
│   └── Wheel encoders
├── Battery management (fuel gauge, charging)
├── Emergency stop (bumper hit, cliff, tilt)
└── Power management (sleep/wake)
```

---

# Motor Control

## Motor Types by Function

| Function | Motor Type | Control Method | Key Requirement |
|---|---|---|---|
| **Drive Wheels** | BLDC with encoder | FOC + odometry | Precise speed control for mapping |
| **Main Brush** | BLDC | FOC with current sensing | Carpet detection via current spike |
| **Side Brush** | DC/BLDC | PWM | Simple speed control |
| **Suction Fan** | High-RPM BLDC | FOC | 20,000–40,000 RPM; carpet boost |
| **Mop Lift** | Stepper / DC gearmotor | Position control | Precise lift height |
| **LDS Turret Motor** | BLDC | Constant speed | Stable RPM for scan sync |
| **Base Station Vacuum** | High-power BLDC | FOC | 1,000–1,500W peak for auto-empty |

---

# Navigation Software Stack

```
┌─────────────────────────────────┐
│         Application Layer       │
│  Room Mgmt │ Scheduling │ API  │
├─────────────────────────────────┤
│          SLAM Backend           │
│  Cartographer │ GMapping │ Custom│
├─────────────────────────────────┤
│         Sensor Fusion           │
│   EKF/UKF │ Particle Filter     │
├─────────────────────────────────┤
│        Sensor Drivers           │
│  LDS │ Camera │ IMU │ Odom │ Cliff│
├─────────────────────────────────┤
│          RTOS / Kernel          │
│    FreeRTOS │ Linux │ RT-Thread │
└─────────────────────────────────┘
```

## SLAM Stack Comparison

| Approach | Maturity | Compute | Accuracy | Flexibility | Used By |
|---|---|---|---|---|---|
| **Google Cartographer** (open) | High | Medium | High | Medium | Custom builds, early Dreame |
| **GMapping** (open) | Very High | Low | Medium | Low | Legacy, budget |
| **Proprietary (Roborock)** | Very High | High | Very High | Low (closed) | Roborock |
| **Proprietary (Dreame)** | High | High | High | Low (closed) | Dreame |
| **Proprietary (iRobot)** | Very High | Medium | Medium | Low (closed) | iRobot |

---

# OTA & Software Update Architecture

| Aspect | Budget | Mid | Premium |
|---|---|---|---|
| **Update Frequency** | Rare (never) | Quarterly | Monthly |
| **A/B Partition** | No | Sometimes | Yes (safe update) |
| **Firmware Size** | <1 MB | 10–50 MB | 50–200 MB |
| **Rollback** | No | Manual only | Automatic if failure |
| **Delta Updates** | No | Sometimes | Yes |
| **Feature Updates** | Rare | Bug fixes only | New features + improvements |

---

# Voice Assistant Integration

| Integration | Description | Examples |
|---|---|---|
| **Alexa Skill** | Amazon cloud integration | "Alexa, tell Roomba to clean the kitchen" |
| **Google Home Action** | Google cloud integration | "Hey Google, start vacuuming" |
| **Siri Shortcuts** | Apple integration (limited) | Custom voice commands |
| **On-Device Voice** | Local keyword spotting (no cloud) | "Hello Roborock, clean here" |
| **Xiaomi XiaoAi** | Xiaomi ecosystem voice | Chinese market |

---

# Evaluation Matrix

| Electronics Aspect | Performance Impact | BOM Cost | Development Complexity | Competitive Moat |
|---|---|---|---|---|
| **SoC + NPU Choice** | 🔴 Critical | $15–50 | High | Strong (custom AI models) |
| **SLAM Algorithm** | 🔴 Critical | $0 (R&D) | Very High | Strong (years of data) |
| **Motor FOC Control** | 🟠 High | $3–8 | Medium | Weak (standard) |
| **OTA Infrastructure** | 🟡 Medium | $0 (cloud cost) | Medium | Medium |
| **Sensor Drivers** | 🟠 High | $0 (R&D) | Medium | Weak |
| **Battery Management** | 🟡 Medium | $2–5 | Low | None |

---

# Industry Trends (2024–2026)

- **Qualcomm/MediaTek entering robot vacuum market**: Mobile SoC vendors offering robotics-specific SDKs
- **On-device AI as privacy premium**: Apple/Google-level data privacy as differentiator
- **RT-Thread gaining over FreeRTOS in Chinese brands**: Open-source Chinese RTOS with better ecosystem
- **Matter protocol for robot vacuums**: Cross-platform smart home standard
- **Fleet learning**: Aggregated navigation data improving SLAM for all users
- **Energy efficiency**: Dynamic voltage/frequency scaling on high-end SoCs
