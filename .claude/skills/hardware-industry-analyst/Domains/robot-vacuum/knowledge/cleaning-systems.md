# Cleaning Systems Knowledge Base

## Purpose

Evaluate the mechanical cleaning systems in robot vacuums — brush designs, suction systems, mopping mechanisms, and edge cleaning strategies. The cleaning system defines the robot's core functional performance.

---

# Main Brush (Primary Agitator)

## Brush Types

| Type | Debris Pickup | Hair Tangle | Carpet Agitation | Noise | Maintenance |
|---|---|---|---|---|---|
| **Bristle Brush** | Good | Very High | Good | Low | Frequent de-hairing |
| **Rubber Roller (single)** | Good | Low | Good | Medium | Wipe clean |
| **Dual Rubber Roller** | Excellent | Low | Very Good | Medium | Wipe clean |
| **Bristle + Rubber Combo** | Good | Medium | Good | Medium | Medium |
| **Blade-only (silicone)** | Medium | Very Low | Low | Low | Minimal |

## Key Innovation: Anti-Tangle Design

- **Roborock DuoRoller Riser**: Twin rubber rollers with spiral grooves, floating design
- **Dreame TriCut brush**: Three-blade silicone + comb structure that cuts hair
- **Ecovacs Anti-Tangle**: Reverse-rotation detection + auto-reverse to release tangles

## Evaluation Criteria

| Criterion | How to Assess |
|---|---|
| **Debris Pickup Rate** | % of test debris (sand/rice/cereal/pet hair) removed in 1 pass |
| **Hair Tangle** | Grams of hair wrapped after 100m² cleaning test |
| **Carpet Performance** | Deep-clean effectiveness on low/medium/high-pile carpet |
| **Hard Floor Performance** | Fine dust pickup, no debris scattering |
| **Brush Lifespan** | Hours before replacement recommended |

---

# Suction System

## Power Tiers

| Tier | Suction Power (Pa) | Typical Price Range | Example Products |
|---|---|---|---|
| **Budget** | 2,000–5,000 Pa | $150–300 | Xiaomi E series, entry-level |
| **Mid-Range** | 5,000–10,000 Pa | $400–700 | Roborock Qrevo, Dreame L10s |
| **Premium** | 10,000–18,000 Pa | $800–1,200 | Roborock S8, Dreame X40 |
| **Flagship** | 18,000–22,000 Pa | $1,200–1,800 | Roborock S8 MaxV, Ecovacs X5, Dreame X40 Ultra |

## Important Notes on Pa Ratings

> ⚠️ Pa (Pascal) ratings are marketing-dominant but not standardized across manufacturers. Actual cleaning effectiveness depends on airflow path design, nozzle geometry, and seal quality — not just raw Pa. A well-engineered 8,000 Pa system can outperform a poorly designed 12,000 Pa system.

## Airflow Path Design

| Component | Function | Key Design Considerations |
|---|---|---|
| Intake Nozzle | Floor-to-brush air seal | Floating/adjustable height for different floor types |
| Dust Channel | Brush to dustbin | Minimize turns/bends to reduce pressure loss |
| Filter | HEPA exhaust | H12/H13 grade; washable vs disposable |
| Fan/Motor | Suction generation | Brushless DC; 20,000–40,000 RPM |

---

# Mopping System

## Mopping Types

| Type | Cleaning Depth | Water Usage | Maintenance | Noise | Cost |
|---|---|---|---|---|---|
| **Passive Drag** | Very Low | Minimal | Wash pad | None | Very Low |
| **Vibrating Plate** | Medium | Medium | Wash pad | Low | Low-Medium |
| **Rotary Discs (2×)** | High | High | Base station washing | Medium | Medium-High |
| **Roller Mop** | Very High | High | Base station self-clean | Medium | High |

## Key Innovation: Mop Lifting

The ability to lift the mopping module when carpet is detected:

| Mechanism | Lift Height | Speed | Examples |
|---|---|---|---|
| **Mechanical lift (motor)** | 5–10mm | 1–2s | Roborock VibraRise, Dreame MopExtend |
| **Full module retraction** | 10–15mm | 2–3s | Ecovacs Ozmo, Narwal |
| **Dual module swap** | Full swap | N/A | Rare, experimental |

## Edge Mopping

- **Rotating mop extension**: Dreame's "MopExtend" arm swings a rotary mop out to reach edges
- **Robot body swing**: Some robots physically oscillate to press the mop against edges
- **Square body design**: Ecovacs X-series square front allows closer edge approach

---

# Side Brush

| Design | Edge Performance | Debris Scatter | Best For |
|---|---|---|---|
| **Single side brush (left)** | Good | Medium | Standard rooms |
| **Dual side brush** | Very Good | High | Large open areas |
| **No side brush** | Poor | None | Narrow spaces (small robots) |
| **Extendable arm** | Excellent | Low | Premium (Roborock G20S) |

---

# Evaluation Matrix

| Cleaning Subsystem | Performance Impact | Reliability Risk | Maintenance Burden | BOM Cost |
|---|---|---|---|---|
| **Main Brush** | 🔴 Critical | Medium (hair tangle) | Medium | $5–15 |
| **Suction Motor** | 🔴 Critical | Low (BLDC reliable) | Low | $10–30 |
| **Mopping** | 🟠 High (differentiator) | Medium (pump/valves) | High (pad washing) | $15–50 |
| **Side Brush** | 🟡 Medium | Low | Low | $2–5 |
| **Dustbin/Filter** | 🟡 Medium | Low | Medium (emptying) | $3–8 |

---

# Industry Trends (2024–2026)

- **Suction power arms race**: 22,000 Pa becoming flagship standard from 18,000 Pa
- **Hot water mopping**: Roborock and Dreame adding heated water (50–60°C) for grease removal
- **Edge cleaning as new battleground**: Extending arms, spinning mops, square bodies
- **Roller mops replacing discs**: Continuous roller mopping with self-cleaning becoming premium differentiator
- **Auto detergent dispensing**: Base stations adding automatic cleaning solution injection
- **Anti-tangle as marketing claim**: TriCut, DuoRoller, Anti-Tangle — every brand has a proprietary name
