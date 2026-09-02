# Electronics Knowledge Base


## Purpose

Evaluate control architectures, MCU selection, motor drivers, and communication buses used in desktop 3D printer electronics.

---

# Control Architecture

## MCU Only (Single-Chip)

**Architecture**: One MCU handles everything — G-code parsing, motion planning, step generation, heater control

**Examples**:
- Marlin on STM32F103 (Ender 3 V2, CR-10)
- Marlin on ATmega2560 (Ender 3 original, RAMPS)

**Advantages**: Low cost, simple, mature
**Disadvantages**: Limited performance (no input shaping, step rate ceiling ~100k steps/s)

**Common MCUs**:
| Chip | Core | Speed | Flash/RAM | Used In |
|---|---|---|---|---|
| ATmega2560 | 8-bit AVR | 16 MHz | 256KB/8KB | RAMPS 1.4, Ender 3 (classic) |
| STM32F103 (Blue Pill) | Cortex-M3 | 72 MHz | 64–128KB/20KB | Creality 4.2.x boards |
| STM32F407 | Cortex-M4F | 168 MHz | 1MB/192KB | BTT SKR 2, high-end Marlin |

---

## Linux SoC + MCU (Dual-Chip / Klipper)

**Architecture**: Linux application processor + real-time MCU

```
Linux SoC (Application)
├── Klipper Host (Python kinematics + planning)
├── Web UI (Mainsail / Fluidd)
├── Camera streaming
├── WiFi / Ethernet stack
└── SPI/USB → MCU

MCU (Real-time)
├── Step generation (300k+ steps/s)
├── Heater PID control
├── Sensor polling
└── Emergency stop
```

**Common SoCs**:
| SoC | Cores | Speed | GPU/NPU | Used In |
|---|---|---|---|---|
| Raspberry Pi 3B+ | 4× Cortex-A53 | 1.4 GHz | VideoCore IV | Klipper host (DIY) |
| Raspberry Pi 4 | 4× Cortex-A72 | 1.8 GHz | VideoCore VI | Klipper host (DIY) |
| Rockchip RV1126 | 4× Cortex-A7 | 1.5 GHz | **NPU 2.0 TOPS** | Bambu Lab AP board |
| Allwinner H-Series | 2–4× Cortex-A7 | 1.0–1.5 GHz | Basic GPU | Creality K1/K2, budget Klipper |
| BTT Pi | 4× Cortex-A53 | 1.5 GHz | Basic GPU | BTT Pad 7, integrated Klipper |

---

## Dual MCU + Dedicated Toolhead Controller (3-Layer)

**Architecture (Bambu Lab)**:
```
AP (Application Processor)  — RV1126, Linux, AI + HMS + Cloud
MC (Motion Controller)      — Spintrol SPC2168, dual M4F@200MHz, RTOS
TH (Toolhead Controller)    — Spintrol SPC1168, M4F@200MHz, RTOS
```

| Chip | Role | Key Specs |
|---|---|---|
| **Rockchip RV1126** | AP — AI inference, networking, UI | 4× Cortex-A7, 2.0 TOPS NPU, 2GB DDR4 |
| **Espressif ESP32** | AP (budget) — WiFi, cloud, basic UI | Xtensa LX6 dual-core, 240 MHz, WiFi/BT |
| **Spintrol SPC2168** | MC — Real-time motion control | Dual M4F@200MHz, 512KB SRAM, CAN-FD |
| **Spintrol SPC1168** | TH — Toolhead sensor & motor control | Single M4F@200MHz, 256KB SRAM |

---

# MCU Comparison

| MCU Family | Architecture | Max Speed | Flash/RAM | Key Advantage | Typical Use |
|---|---|---|---|---|---|
| **ATmega2560** | 8-bit AVR | 16 MHz | 256KB/8KB | Ultra low cost | Legacy Marlin |
| **STM32F1 (F103)** | Cortex-M3 | 72 MHz | 64–128KB/20KB | Mature ecosystem | Ender 3 V2, budget |
| **STM32F4 (F407)** | Cortex-M4F | 168 MHz | 1MB/192KB | FPU + DSP | High-end Marlin, RRF |
| **GD32F303** | Cortex-M4F | 120 MHz | 256–512KB/64KB | Cost-effective STM32 alt | BTT SKR Mini E3 |
| **RP2040** | Dual M0+ | 133 MHz | 2MB ext./264KB | PIO (flexible I/O) | Klipper MCU, CAN toolhead |
| **ESP32** | Xtensa LX6 | 240 MHz | 4–16MB/520KB | WiFi+BT integrated | Bambu A1 AP, IoT boards |
| **Spintrol SPC2168** | Dual M4F | 200 MHz | 512KB/— | Real-time RTOS, CAN-FD | Bambu Lab MC (proprietary) |

---

# Motor Drivers

| Driver | Peak Current | Microstepping | Key Feature | Noise | Used In |
|---|---|---|---|---|---|
| **A4988** | 2A | 1/16 | Ultra low cost | Loud | Legacy budget printers |
| **TMC2208** | 1.4A | 1/256 | StealthChop2 (silent) | Silent | Ender 3 V2, most mid-range |
| **TMC2209** | 2A | 1/256 | StealthChop2 + StallGuard | Silent | Prusa MK4, Klipper builds |
| **TMC5160** | 3A | 1/256 | StealthChop2 + external MOSFETs | Silent | Voron, high-power builds |
| **TMC2130** | 1.4A | 1/256 | SPI config + StallGuard | Silent | Prusa MK3, advanced Marlin |
| **FOC Servo** (Creality) | Varies | — | Closed-loop current+position | Silent | K2 Plus/Hi (step-servo hybrid) |
| **PMSM Servo** (Bambu) | Varies | — | 20 kHz closed-loop FOC | Silent | P2S/A2L/H2/X2D (true servo) |

---

# Communication Buses

| Bus | Speed | Topology | Use Case | Used By |
|---|---|---|---|---|
| **UART** | ≤ 1 Mbps | Point-to-point | MCU ↔ driver, debug | Universal |
| **SPI** | ≤ 50 Mbps | Master-slave | Host ↔ MCU (Klipper), sensor ICs | Klipper, TMC2130 |
| **CAN / CAN-FD** | 1 Mbps / 8 Mbps | Multi-drop bus | Toolhead ↔ MC, multi-MCU | Bambu-Bus, Klipper CAN toolhead, CFS |
| **I²C** | ≤ 400 kbps | Multi-drop | Temperature sensors, OLED | Universal |
| **USB** | 480 Mbps (2.0) | Point-to-point | Printer ↔ PC, Klipper host ↔ MCU | Universal |
| **Ethernet** | 100/1000 Mbps | Network | Wired connectivity | Bambu X1E, industrial printers |
| **RS-485** | ≤ 10 Mbps | Multi-drop | Industrial control, CFS | Creality CFS, Prusa XL |

---

# Industry Trends (2024–2026)

- **32-bit ARM universal**: 8-bit ATmega fully deprecated in new designs
- **Linux + MCU as standard for mid-range+**: Enables AI, cloud, advanced planning
- **CAN toolhead boards**: Modular, serviceable, reduces wiring harness complexity
- **FOC / PMSM servo extruders replacing open-loop steppers**: Enables clog detection, active flow control
- **Edge AI (NPU) on printer**: Bambu RV1126 NPU sets precedent for on-device inference
- **WiFi as baseline**: No longer a premium feature — expected even in $200 segment
- **Closed-loop steppers becoming affordable**: Creality K2 Plus FOC servo path
