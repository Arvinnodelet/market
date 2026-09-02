# Base Station Knowledge Base

## Purpose

Evaluate the multifunction base station — the docking and maintenance hub that has become a key differentiator in premium robot vacuums. The base station determines the robot's autonomy ceiling and ongoing maintenance burden.

---

# Base Station Functions

## Feature Stack by Tier

| Function | Budget | Mid | Premium | Flagship |
|---|---|---|---|---|
| **Charging** | ✅ | ✅ | ✅ | ✅ |
| **Auto-Empty (dust)** | ❌ | ✅ | ✅ | ✅ |
| **Mop Washing** | ❌ | ❌ | ✅ | ✅ |
| **Hot Air Drying** | ❌ | ❌ | ✅ (40–45°C) | ✅ (50–60°C) |
| **Water Tank Refill** | ❌ | ❌ | ❌ | ✅ |
| **Detergent Dispensing** | ❌ | ❌ | ❌ | ✅ |
| **Hot Water Mop Wash** | ❌ | ❌ | ❌ | ✅ (50–60°C) |
| **UV Sterilization** | ❌ | ❌ | ❌ | Optional |

---

# Auto-Empty System

## Architecture

```
Robot Dustbin (~300–400ml)
    │
    ▼  (docking: suction port aligns)
Base Station Motor (high-power BLDC)
    │
    ▼  (airflow carries dust)
Dust Bag (2.5–3.5L, HEPA-filtered exhaust)
```

## Key Specifications

| Metric | Entry | Premium | Notes |
|---|---|---|---|
| **Suction Power** | 15,000–20,000 Pa | 25,000–35,000 Pa | Base station vacuum motor |
| **Dust Bag Capacity** | 2.0–2.5 L | 3.0–3.5 L | ~60–90 days between replacements |
| **Empty Time** | 10–15s | 5–10s | Faster = less noise exposure |
| **Empty Success Rate** | 85–95% | 95–99% | % of dustbin contents transferred |
| **Noise During Empty** | 70–80 dB | 65–75 dB | Brief but loud — door-closing preference |

## Dust Bag Design

| Type | Capacity | Cost/bag | Replacement Interval | Environmental |
|---|---|---|---|---|
| **Paper Bag** | 2.5–3.0 L | $2–4 | 60–90 days | Biodegradable |
| **Non-woven Fabric** | 3.0–3.5 L | $3–5 | 60–90 days | Not biodegradable |
| **Bagless (cyclone)** | Unlimited | None (wash) | Monthly wash | Best — but rare (Xiaomi) |

---

# Mop Washing System

## Washing Methods

| Method | Clean Quality | Water Usage | Noise | Reliability |
|---|---|---|---|---|
| **Cold Water Scrubbing** | Medium | Medium | Medium | High |
| **Hot Water Scrubbing (50–60°C)** | High | Medium | Medium | Medium (heater failure risk) |
| **Ultrasonic Cleaning** | Experimental | Low | Low | Unknown |

## Washing Mechanism

| Mechanism | Description | Examples |
|---|---|---|
| **Rotary disc on textured plate** | Mop pads rotate against textured washboard | Roborock Qrevo, Dreame L20 |
| **Rolling brush self-clean** | Internal roller mop cleans itself against water spray | Narwal, Dreame roller models |
| **Stationary mop with water jets** | Vibrating mop pad washed by water spray | Older Roborock S-series |

---

# Drying System

| Method | Temperature | Duration | Power | Effectiveness |
|---|---|---|---|---|
| **Passive Air Dry** | Ambient | 4–6 hours | 0W | Low (mold risk in humid climates) |
| **Warm Air (40–45°C)** | 40–45°C | 2–4 hours | 30–50W | Medium |
| **Hot Air (50–60°C)** | 50–60°C | 1.5–3 hours | 50–80W | High |
| **Dual-zone Hot Air** | 55–65°C | 1–2 hours | 60–100W | Very High |

---

# Water Management

## Tank Configurations

| Configuration | Clean Water | Dirty Water | Refill/Drain Frequency | Examples |
|---|---|---|---|---|
| **Dual Onboard (no station)** | 200–300ml | 200–300ml | Every 1–2 cleans | Budget mopping bots |
| **Station Dual Tank** | 3–5 L | 3–5 L | Every 1–4 weeks | Roborock Qrevo, Dreame |
| **Plumbed (direct water)** | ∞ (plumbed) | ∞ (drain) | Never | Roborock S8 MaxV Ultra (plumbing kit) |

## Key Innovation: Plumbing Kit

Direct connection to household water supply + drain:
- **Advantages**: Zero user intervention for water management
- **Disadvantages**: Requires professional installation; not rental-friendly; higher upfront cost
- **Adoption**: Roborock and Ecovacs offer optional plumbing kits for flagship models

---

# Maintenance Burden

| Component | Task | Frequency | User Pain |
|---|---|---|---|
| **Dust Bag** | Replace | 60–90 days | Low |
| **Clean Water Tank** | Refill | 1–4 weeks | Medium (heavy when full) |
| **Dirty Water Tank** | Empty + rinse | 1–2 weeks | Medium (odor) |
| **Mop Pads** | Replace | 3–6 months | Low |
| **Base Station Tray** | Clean | Monthly | Medium (debris buildup) |
| **Sensors/Contacts** | Wipe | Monthly | Low |

---

# Evaluation Matrix

| Base Station Feature | User Value | BOM Cost | Reliability Risk | Noise Impact |
|---|---|---|---|---|
| **Auto-Empty** | 🔴 Critical | $20–40 | Low | High (brief) |
| **Mop Washing** | 🔴 Critical | $25–50 | Medium (pump/valves) | Medium |
| **Hot Air Drying** | 🟠 High | $10–20 | Low | Low (quiet fan) |
| **Water Refill** | 🟡 Medium | $15–30 | Medium | Low |
| **Detergent Auto-Dispense** | 🟡 Medium | $5–10 | Low | None |
| **Hot Water Wash** | 🟡 Medium | $10–15 | Medium | Medium |
| **UV Sterilization** | 🟢 Low (questionable efficacy) | $5–10 | Low | None |
| **Plumbing Kit** | 🟠 High (for homeowners) | $30–50 (optional accessory) | Medium (leak risk) | None |

---

# Industry Trends (2024–2026)

- **Heat as premium differentiator**: Hot water wash + hot air dry becoming flagship standard
- **Plumbing integration**: Direct water connection moving from niche to premium option
- **Bagless auto-empty**: Xiaomi-style cyclone separation as eco-friendly alternative
- **Base station miniaturization**: Smaller footprint for apartments — folding/retractable designs
- **Detergent ecosystem lock-in**: Proprietary detergent cartridges (recurring revenue play)
- **Self-cleaning base stations**: Auto-cleaning washboards and drain filters
