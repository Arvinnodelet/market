# Sensor Systems Knowledge Base

## Purpose

Evaluate sensor technologies used in robot vacuums — obstacle avoidance, cliff detection, dirt sensing, carpet recognition, and environmental perception. Sensor capability directly determines navigation quality and collision avoidance performance.

---

# Obstacle Avoidance Systems

## Technology Comparison

| Technology | Detection Range | Object Resolution | Dark Performance | BOM Cost | Examples |
|---|---|---|---|---|---|
| **IR Bumper (contact)** | 0–5 cm | Binary (hit/no-hit) | N/A | Very Low | Budget < $200 |
| **Ultrasonic** | 5–50 cm | Low (size estimate) | Good | Low | Mid-range |
| **Line Laser (1D)** | 5–100 cm | Medium (contour) | Good | Medium | Mid-range + LDS |
| **3D Structured Light** | 5–200 cm | High (3D depth map) | Good (IR projected) | Medium-High | Dreame, Roborock mid |
| **RGB Camera + AI** | 10–500 cm | Very High (object ID) | Poor (needs light) | Medium | Camera-equipped |
| **dToF + RGB Fusion** | 5–300 cm | Very High | Excellent | High | Roborock S8 MaxV |
| **Stereo Camera + IR** | 10–400 cm | High | Good (IR illuminator) | High | iRobot j9 |

## Object Recognition Capability

| Object | Detection Rate (2024 Premium) | Detection Rate (2026 Premium) | Importance |
|---|---|---|---|
| Cables/Wires | 70–85% | 85–95% | 🔴 Critical (tangle risk) |
| Pet Waste | 80–90% | 90–95% | 🔴 Critical (disaster scenario) |
| Socks/Clothing | 80–90% | 90–95% | 🟠 High |
| Shoes/Slippers | 90–95% | 95–99% | 🟠 High |
| Pet Bowls | 85–90% | 90–95% | 🟡 Medium |
| Scale/Weighing Scale | 70–80% | 80–90% | 🟡 Medium |

---

# Cliff Sensors

## Principle

Downward-facing infrared proximity sensors detect sudden distance increase (stairs/ledges). Typically 3–6 sensors mounted around the robot perimeter.

## Specifications

| Metric | Entry | Premium |
|---|---|---|
| Sensor Count | 3–4 | 6 |
| Detection Range | 5–15 cm | 5–20 cm |
| False Positive Rate | Medium (dark floors) | Low (multi-wavelength) |

## Challenges

- **Dark/black floors**: Absorb IR — can cause false cliff triggers (robot refuses to clean)
- **Highly reflective floors**: Mirror reflection can saturate sensor — false safe signal
- **Glass floors/stairs**: Transparent — IR passes through, no detection

---

# Dirt Detection

| Technology | Principle | Accuracy | Cost |
|---|---|---|---|
| **Acoustic (microphone)** | Listen for debris impact sound | Medium | Low |
| **Optical (IR beam break)** | IR beam across intake — debris breaks beam | Medium | Low |
| **Piezoelectric** | Vibration sensor on intake — debris impact | High | Medium |
| **Vision-based** | Camera detects floor texture change | High (in development) | High |

---

# Carpet Recognition

| Method | Accuracy | Response Time | Cost |
|---|---|---|---|
| **Ultrasonic echo** | Medium (80–90%) | 1–2s | Low |
| **Current draw spike** | Medium (brush motor load change) | 0.5–1s | Very Low |
| **Optical floor sensor** | High (95–98%) | <0.5s | Medium |
| **Camera + AI** | Very High (98%+) | <0.5s | High |

---

# Sensor Fusion Architecture (Typical Premium Robot)

```
                    ┌─────────────────────┐
                    │   Application SoC   │
                    │  (Navigation + AI)  │
                    └──────┬───┬──────────┘
                           │   │
              ┌────────────┘   └────────────┐
              ▼                              ▼
    ┌─────────────────┐            ┌─────────────────┐
    │   Sensor Hub    │            │    ISP/NPU      │
    │  (MCU realtime) │            │ (Camera + AI)   │
    └───┬───┬───┬─────┘            └────┬────────────┘
        │   │   │                       │
   ┌────┘   │   └────┐           ┌─────┘
   ▼        ▼        ▼           ▼
┌─────┐ ┌─────┐ ┌──────┐   ┌─────────┐
│Cliff│ │Ultr-│ │  IR  │   │  RGB    │
│ ×6  │ │asonic│ │Bumper│   │ Camera  │
└─────┘ └─────┘ └──────┘   └─────────┘
```

---

# Evaluation Matrix

| Sensor | Navigation Impact | Safety Impact | BOM Cost | Reliability | Adoption (2026) |
|---|---|---|---|---|---|
| **LDS Turret** | 🔴 Critical | 🟡 Low | $8–15 | Medium | 70% of mid+ |
| **dToF/3D Structured Light** | 🟠 High | 🟠 High | $15–30 | High | 40% of premium |
| **RGB Camera** | 🟡 Medium | 🔴 Critical | $5–12 | High | 60% of mid+ |
| **Cliff Sensors** | 🟢 None | 🔴 Critical | $1–3 | High | 100% |
| **Dirt Detection** | 🟢 None | 🟢 None | $1–5 | Medium | 50% |
| **Carpet Sensor** | 🟡 Medium | 🟢 None | $2–8 | Medium-High | 80% of mid+ |

---

# Industry Trends (2024–2026)

- **RGB camera becoming standard on $500+**: Obstacle recognition + video calls + remote monitoring
- **Pet waste detection as flagship feature**: AI models specifically trained for this high-stakes scenario
- **dToF replacing IR bumper**: Solid-state depth sensing for proactive (not reactive) avoidance
- **Sensor miniaturization**: Fewer external bumps — sensors integrated into body/bumper
- **Privacy-focused on-device AI**: Camera processing entirely on-device; no cloud upload
- **Multi-spectral cliff sensors**: Dual-wavelength IR to handle dark floor false positives
