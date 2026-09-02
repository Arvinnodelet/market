# Motion Systems Knowledge Base


## Purpose

This document summarizes motion architectures used in FDM additive manufacturing systems with quantitative performance ranges and engineering tradeoffs.

---

# Bedslinger (Cartesian, Moving Bed Y-Axis)

**Examples**: Prusa MK4, Ender 3, Bambu A1 series

**Typical Specs**:
| Metric | Budget | Mid-Range |
|---|---|---|
| Max Speed | 150–250 mm/s | 300–500 mm/s |
| Max Acceleration | 2,000–5,000 mm/s² | 5,000–10,000 mm/s² |
| Build Volume | 220–300³ mm | 256–330³ mm |

**Advantages**:
- Simplest kinematics (3 independent axes)
- Lowest BOM cost
- Easiest to manufacture & assemble
- Large community & modding ecosystem

**Disadvantages**:
- Moving bed mass limits Y acceleration (entire print + bed moves)
- Tall prints prone to wobble (center of mass rises)
- Speed ceiling lower than CoreXY (practical: ~500 mm/s)
- Requires more desk depth (bed travel × 2)

**Suitable For**: Entry-level products, budget builds, education

---

# CoreXY

**Examples**: Bambu X1/P1/X2, Voron 2.4/Trident, Creality K1/K2, Prusa Core One

**Typical Specs**:
| Metric | Mid-Range | High-End |
|---|---|---|
| Max Speed | 300–600 mm/s | 600–1,000 mm/s |
| Max Acceleration | 10,000–20,000 mm/s² | 20,000–50,000 mm/s² |
| Build Volume | 220–300³ mm | 300–350³ mm |

**Advantages**:
- Stationary bed — print mass doesn't limit acceleration
- Highest speed/acceleration of consumer architectures
- Compact footprint for given build volume
- Dual-motor XY spreads load, enabling high torque
- Well-understood kinematics (Voron community, Klipper support)

**Disadvantages**:
- Long belt paths (~2× Cartesian) — wear, tension maintenance
- Belt routing complexity — assembly errors cause skew
- Higher BOM cost (more bearings, idlers, linear rails)
- Belt stretch at extreme speeds requires compensation

**Suitable For**: Prosumer, professional, print farms, high-speed printing

---

# CoreXZ

**Examples**: Creality Ender 5 Max, Voron Switchwire variants

**Typical Specs**:
| Metric | Range |
|---|---|
| Max Speed | 300–700 mm/s |
| Max Acceleration | 8,000–15,000 mm/s² |

**Advantages**:
- Stationary bed in Y (only Z moves with print)
- Lower bed-moving mass than Bedslinger
- Can achieve large build volumes (400³+)
- Good XY rigidity

**Disadvantages**:
- More complex Z kinematics (belt + leadscrew hybrid)
- Less community support than CoreXY
- Limited adoption — fewer reference designs

**Suitable For**: Large-format consumer printers, research platforms

---

# IDEX (Independent Dual Extruder)

**Examples**: Raise3D E2, Sovol SV04, Snapmaker J1

**Typical Specs**:
| Metric | Range |
|---|---|
| Max Speed | 150–350 mm/s |
| Max Acceleration | 3,000–8,000 mm/s² |

**Modes**:
- **Duplicate/Mirror**: Both toolheads print same object simultaneously (doubles throughput)
- **Independent**: Two different objects printed side-by-side
- **Multi-material**: Soluble supports or two colors (no purge waste)

**Advantages**:
- True multi-material without purge waste
- Mirror/duplicate mode doubles farm output
- No cross-contamination between materials

**Disadvantages**:
- Highest BOM cost (2× extruders, hotends, drivers)
- X-axis alignment critical — mismatch ruins prints
- Added moving mass (second toolhead)
- Limited slicer support
- Second toolhead can drag on print if offset calibration drifts

**Suitable For**: Print farms (mirror mode), soluble support applications, education

---

# Delta

**Examples**: FLSUN SR/V400, Anycubic Predator

**Typical Specs**:
| Metric | Range |
|---|---|
| Max Speed | 300–1,000 mm/s |
| Max Acceleration | 10,000–30,000 mm/s² |

**Advantages**:
- Very fast vertical movement (3 arms share load)
- Tall cylindrical build volume (good for vases/figures)
- Light effector (no heavy toolhead carriage)
- Visually impressive

**Disadvantages**:
- Complex kinematics (3-arm trigonometric transforms)
- Difficult calibration (tower alignment, delta radius)
- Effective build area shrinks with height (cone-shaped)
- Poor XY accuracy at edges
- Limited community support vs Cartesian

**Suitable For**: Tall objects, high-speed prototyping, cosmetic prints

---

# Evaluation Matrix

| Architecture | BOM Cost | Speed | Acceleration | Reliability | Manufacturability | Best For |
|---|---|---|---|---|---|---|
| **Bedslinger** | Low ($) | 150–500 mm/s | 2k–10k mm/s² | High | High | Entry-level, education |
| **CoreXY** | Medium ($$) | 300–1,000 mm/s | 10k–50k mm/s² | High | Medium | Prosumer, professional |
| **CoreXZ** | Medium ($$) | 300–700 mm/s | 8k–15k mm/s² | Medium | Medium | Large-format |
| **IDEX** | High ($$$) | 150–350 mm/s | 3k–8k mm/s² | Medium | Low | Multi-material, farms |
| **Delta** | Medium ($$) | 300–1,000 mm/s | 10k–30k mm/s² | Medium | Low | Tall objects, speed |
