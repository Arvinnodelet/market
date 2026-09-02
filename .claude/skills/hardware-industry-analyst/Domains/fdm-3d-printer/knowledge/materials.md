# Materials Knowledge Base


## Purpose

Evaluate FDM filament materials by mechanical properties, thermal performance, printability, cost, and application fit. Used for assessing printer material compatibility and ecosystem strategy.

---

# Material Profiles

## PLA (Polylactic Acid)

| Property | Value |
|---|---|
| Nozzle Temp | 190–220°C |
| Bed Temp | 0–60°C (optional) |
| Print Speed | 30–600 mm/s |
| Tensile Strength | 50–60 MPa |
| Heat Deflection (HDT) | ~55°C |
| Density | 1.24 g/cm³ |

**Advantages**: Easiest to print, low warp, no enclosure needed, biodegradable, wide color range, low odor
**Disadvantages**: Low heat resistance (deforms in car/ dishwasher), brittle under impact, poor UV resistance
**Best For**: Decorative, prototyping, education, low-stress parts
**Not For**: Outdoor, high-temp, load-bearing

---

## PETG (Polyethylene Terephthalate Glycol)

| Property | Value |
|---|---|
| Nozzle Temp | 220–250°C |
| Bed Temp | 70–85°C |
| Print Speed | 40–120 mm/s |
| Tensile Strength | 45–55 MPa |
| HDT | ~70°C |
| Density | 1.27 g/cm³ |

**Advantages**: Tough (impact-resistant), chemical-resistant, good layer adhesion, less warp than ABS, food-safe grades available
**Disadvantages**: Stringing/oozing, hygroscopic (needs drying: 65°C × 4h), glossy surface shows imperfections, poor bridging
**Best For**: Functional parts, mechanical components, outdoor (with UV additives), containers
**Not For**: High-temp (>70°C), high-speed printing

---

## ABS (Acrylonitrile Butadiene Styrene)

| Property | Value |
|---|---|
| Nozzle Temp | 230–260°C |
| Bed Temp | 90–110°C |
| Chamber Temp | 40–60°C recommended |
| Print Speed | 40–100 mm/s |
| Tensile Strength | 35–45 MPa |
| HDT | ~95°C |
| Density | 1.04 g/cm³ |

**Advantages**: Engineering-grade, good heat resistance, sandable/paintable, acetone vapor smoothing, durable
**Disadvantages**: Significant warping (requires enclosure), strong fumes (VOCs — requires ventilation), UV-sensitive, hygroscopic
**Best For**: Functional prototypes, automotive parts, enclosures, post-processed parts
**Not For**: Open-frame printers, food contact, outdoor without coating

---

## ASA (Acrylonitrile Styrene Acrylate)

| Property | Value |
|---|---|
| Nozzle Temp | 240–260°C |
| Bed Temp | 90–110°C |
| Chamber Temp | 40–60°C recommended |
| Print Speed | 40–100 mm/s |
| Tensile Strength | 40–50 MPa |
| HDT | ~95°C |
| Density | 1.07 g/cm³ |

**Advantages**: UV-resistant (best outdoor FDM material), same mechanicals as ABS, less warping than ABS, good chemical resistance
**Disadvantages**: Still needs enclosure, fumes (less than ABS but present), more expensive than ABS, hygroscopic
**Best For**: Outdoor functional parts, automotive trim, garden/agriculture, drone/RC parts
**Not For**: Open-frame, budget builds

---

## TPU (Thermoplastic Polyurethane)

| Property | Value |
|---|---|
| Nozzle Temp | 210–250°C |
| Bed Temp | 30–60°C |
| Print Speed | 20–40 mm/s (slow!) |
| Shore Hardness | 60A–95A (flexible) / 55D–75D (rigid-flex) |
| Tensile Strength | 25–50 MPa |
| Elongation | 300–600% |
| Density | 1.20 g/cm³ |

**Advantages**: Flexible, impact-absorbing, excellent layer adhesion, chemical/abrasion resistant
**Disadvantages**: Very slow printing, stringing, moisture-sensitive (dry at 55°C × 4h), NOT compatible with AMS/CFS/MMU multi-material systems, Bowden extruders struggle
**Best For**: Gaskets, phone cases, drone bumpers, shoe soles, vibration dampeners
**Not For**: Multi-color systems, Bowden setups, high-speed printing

---

## PA (Nylon)

| Property | Value |
|---|---|
| Nozzle Temp | 250–280°C |
| Bed Temp | 80–100°C |
| Chamber Temp | 40–60°C recommended |
| Print Speed | 30–70 mm/s |
| Tensile Strength | 60–80 MPa |
| HDT | ~100–180°C |
| Density | 1.14 g/cm³ |

**Advantages**: Strong, tough, wear-resistant, high heat resistance, low friction (gear applications), chemical-resistant
**Disadvantages**: Extremely hygroscopic (must dry: 80°C × 6h, print from dry box), warping, enclosure required, expensive, abrasive to brass nozzles
**Best For**: Gears, bearings, functional mechanical parts, high-stress components
**Not For**: Open printers, budget builds, beginners

---

## Carbon Fiber Filled (PLA-CF / PETG-CF / PA-CF / PAHT-CF)

| Property | PLA-CF | PETG-CF | PA-CF | PAHT-CF |
|---|---|---|---|---|
| Nozzle Temp | 200–230°C | 230–260°C | 260–290°C | 280–320°C |
| Bed Temp | 50–60°C | 70–85°C | 80–100°C | 100–120°C |
| Strength Gain vs Unfilled | +20% stiffness | +30% stiffness | +50% stiffness | +60% stiffness |
| HDT | ~60°C | ~75°C | ~140°C | ~180°C |
| Cost (per kg) | $25–35 | $30–45 | $50–80 | $80–120 |

**Advantages**: High stiffness-to-weight, low warp (CF reduces shrinkage), matte surface finish, dimensional stability
**Disadvantages**: Abrasive (REQUIRES hardened steel or better nozzle), brittle (lower impact strength than unfilled), more expensive, nozzle clog risk with high CF%
**Best For**: Structural brackets, drone frames, jigs & fixtures, cosmetic parts (matte finish)
**Not For**: Brass nozzles (will destroy in hours), impact applications

---

## High-Performance (PPA-CF / PPS / PEI)

| Property | PPA-CF | PPS | PEI (Ultem) |
|---|---|---|---|
| Nozzle Temp | 280–320°C | 300–350°C | 350–380°C |
| Bed Temp | 100–120°C | 100–140°C | 140–160°C |
| Chamber Temp | 50–60°C | 60–80°C | 80–120°C |
| HDT | ~180°C | ~220°C | ~200°C |
| Cost (per kg) | $80–120 | $100–200 | $200–400 |
| Printer Required | K2 Plus / H2D / Industrial | H2D+ / Industrial | Industrial only |
| Applications | Aerospace, under-hood | Chemical processing | Aerospace, medical |

---

# Material Selection Matrix

| Requirement | Best Material | Acceptable | Avoid |
|---|---|---|---|
| Easiest to print | PLA | PETG | ABS, PA, TPU |
| Heat resistance >100°C | PA-CF, PPA-CF | ABS, ASA | PLA, PETG |
| Outdoor / UV | ASA | PETG (UV grade) | PLA, ABS |
| Flexible / impact | TPU | — | PLA, CF-filled |
| Strength + stiffness | PA-CF, PPA-CF | PA, PETG-CF | PLA, TPU |
| Food contact | PETG (food-grade) | PLA (food-grade) | ABS, ASA, PA |
| Chemical resistance | PA, PP | PETG | PLA, ABS |
| Low cost | PLA ($15–25/kg) | PETG ($18–28/kg) | PA-CF, PEEK |
| Multi-color system | PLA, PETG, ABS | ASA, PA | TPU (jams AMS/CFS) |
| Print farm throughput | PLA, PETG (fast) | ABS (slow) | TPU (very slow) |

---

# Multi-Material System Compatibility

| Material | AMS (Bambu) | CFS (Creality) | MMU3 (Prusa) | Notes |
|---|---|---|---|---|
| PLA | ✅ | ✅ | ✅ | Best for multi-color |
| PETG | ✅ | ✅ | ✅ | Stringing increases waste |
| ABS | ✅ | ✅ | ⚠️ | Purge temps differ |
| ASA | ✅ | ✅ | ⚠️ | Similar to ABS |
| PA | ⚠️ | ⚠️ | ⚠️ | Moisture absorption in unit |
| TPU | ❌ | ❌ | ❌ | Flexible — jams feed path |
| CF-filled | ⚠️ | ⚠️ | ⚠️ | Abrasive to cutter; hardened nozzle only |
| PVA (support) | ✅ | ✅ | ✅ | Water-soluble interface |

---

# Filament Ecosystem Strategy

| Strategy | Description | Examples | Advantage | Disadvantage |
|---|---|---|---|---|
| **Open** | Any brand, no RFID | Prusa, Voron | Freedom, price competition | Manual setup per spool |
| **RFID Closed** | Proprietary RFID spools only | Bambu AMS, Creality CFS | Auto-detect, preset profiles | Higher cost, vendor lock-in |
| **Certified** | "Recommended" but not required | Prusa, UltiMaker | Quality assurance + flexibility | Certification cost |

---

# Industry Trends (2024–2026)

- **CF/GF composites going mainstream**: PLA-CF and PETG-CF now standard in mid-range printers
- **Engineering materials reaching consumer**: PPA-CF and PPS printable on $1,500 printers (K2 Plus, H2D)
- **RFID lock-in battle**: Bambu RFID vs Creality RFID ecosystems competing for filament recurring revenue
- **High-speed formulations**: Hyper PLA, High-speed PETG, Rapid ABS — tuned for 300–600 mm/s
- **Recycled / sustainable filaments**: rPLA, rPETG gaining traction; still niche
- **Multi-material support materials**: PVA/BVOH for soluble supports, breakaway PLA for easy removal
