# Firmware Knowledge Base


## Purpose

Evaluate firmware architectures, motion planning capabilities, and ecosystem dynamics in desktop 3D printing.

---

# Open-Source Firmware

## Marlin

**Architecture**: Single MCU (STM32 / ATmega), all-in-one firmware

**Advantages**:
- Most mature ecosystem (10+ years)
- Huge community & documentation
- Runs on low-cost hardware (ATmega2560, STM32F1)
- G-code standard compliance

**Disadvantages**:
- Limited motion planning (no native input shaping)
- Single-MCU ceiling on speed (~250 mm/s practical max)
- No built-in network/cloud support
- Step-rate limited on 8-bit platforms

**Typical Use**: Ender 3 stock, CR-10, budget printers

---

## Klipper

**Architecture**: Linux Host (RPi / SoC) + MCU (STM32 / RP2040 / GD32)

```
Linux Host (Raspberry Pi / SoC)
│
├── Kinematics & Motion Planning (Python)
│   ├── Input Shaping          ← Vibration compensation
│   ├── Pressure Advance       ← Linear advance for extrusion
│   ├── Smooth Pressure Advance ← Improved PA algorithm
│   └── Resonance Compensation  ← Per-axis frequency tuning
│
├── G-code Parsing
│
└── MCU Interface (SPI / USB)
    │
    ▼
MCU (STM32 / RP2040)
└── Step generation (real-time)
```

**Key Features**:
- **Input Shaping** — Eliminates ringing/ghosting at high acceleration. Requires accelerometer calibration (ADXL345). Supports MZV, ZV, EI, 2HUMP_EI shapers.
- **Pressure Advance** — Compensates extruder pressure lag during acceleration changes. Prevents corner bulging and under-extrusion.
- **Smooth Pressure Advance** — Improved PA that reduces extruder motor stress
- **Resonance Compensation** — Per-axis frequency analysis for frame-specific tuning
- **High Step Rate** — 300k+ steps/sec via dedicated MCU, enables 600+ mm/s
- **Web Interface** — Mainsail / Fluidd for remote control & webcam
- **Multi-MCU** — Supports distributed control (toolhead boards via CAN)

**Advantages**:
- Best speed/quality balance (input shaping + pressure advance)
- Flexible development (Python kinematics, easy to modify)
- Remote management built-in (web UI, API)
- Multi-MCU for distributed architectures

**Disadvantages**:
- Requires Linux host (adds cost, complexity)
- Not beginner-friendly (config files, calibration)
- SPI/USB latency between host and MCU

**Typical Use**: Voron, Creality Ender 3 V3 KE/Plus, RatRig, custom builds

---

## RepRapFirmware (RRF)

**Architecture**: Duet3D boards (STM32 / SAME5x), RTOS-based

**Advantages**:
- Industrial-grade motion planning (jerk, acceleration control)
- Built-in web interface (DWC — Duet Web Control)
- CAN-FD expansion for toolheads & expansion boards
- Excellent delta kinematics support

**Disadvantages**:
- Smaller community than Marlin/Klipper
- Proprietary Duet hardware (cost premium)
- Limited MCU platform support

**Typical Use**: Delta printers, high-end DIY, industrial conversions

---

# Consumer Closed-Source Firmware

## Bambu Lab OS (拓竹)

**Architecture**: Linux (RV1126) + dual MCU (ESP32 + Spintrol SPC2168/SPC1168)

```
AP (RV1126 Linux)
├── Bambu Studio communication
├── AI inference (NPU): spaghetti detection, first-layer analysis
├── HMS (Health Management System): 40+ error codes
├── OTA update engine
└── Communication proxy

MC (SPC2168, dual M4F@200MHz)     TH (SPC1168, M4F@200MHz)
├── Real-time motion planning       ├── Motor control
├── CoreXY kinematics               ├── Sensor sampling (eddy current)
├── Vibration compensation          ├── Heater PID
├── PMSM servo control              └── Filament handling
└── Bambu-Bus communication
```

**Key Features**:
- **Proprietary motion planning** — Optimized CoreXY trajectories, vibration compensation tuned per-machine
- **Eddy current sensor fusion** — Hardware-level integration for calibration + flow compensation + clump detection
- **AI on NPU** — On-chip inference for spaghetti detection, first-layer inspection
- **HMS** — Structured error reporting with human-readable descriptions and fix suggestions
- **OTA Updates** — Firmware + software updates over WiFi
- **Security** — Encrypted firmware, signed updates, cloud auth

---

## Creality OS (创想三维)

**Architecture**: Linux SoC (dual-core Cortex-A7) running Creality OS

**Key Features**:
- Based on Klipper core with Creality modifications
- Integrated with Creality Cloud (remote control, AI monitoring)
- CFS communication protocol (CAN bus)
- RFID filament auto-detection
- AI camera integration (spaghetti detection, flow calibration)
- Creality Print slicer integration

**Compared to Bambu Lab OS**:
- More open (Klipper heritage allows community modifications)
- Less polished motion planning (fewer hardware-specific optimizations)
- AI features are cloud-dependent (vs Bambu's on-device NPU)

---

# Firmware Comparison Matrix

| Firmware | Performance | Flexibility | Community | Learning Curve | HW Cost | Closed/Open |
|---|---|---|---|---|---|---|
| **Marlin** | Medium | High | Very High | Low | Low | Open |
| **Klipper** | High | Very High | High | Medium | Medium | Open |
| **RRF** | High | High | Medium | Medium | High | Open |
| **Bambu Lab OS** | Very High | Low | — | Low (user) | Included | Closed |
| **Creality OS** | Medium-High | Medium | Medium | Low (user) | Included | Semi-closed |

---

# Industry Trends (2024–2026)

- **Klipper dominance in open-source**: 80%+ of new DIY/custom builds use Klipper
- **Closed-source vertical integration**: Bambu Lab proves tight HW+FW integration produces the best out-of-box experience
- **AI moving to firmware layer**: Spaghetti detection, flow calibration, and print monitoring becoming standard FW features
- **Distributed architectures**: CAN toolhead boards enable modular, serviceable designs
- **Cloud connectivity as baseline**: WiFi + cloud app control is now expected, not premium
- **Security becoming critical**: Encrypted firmware, signed updates, platform authentication
