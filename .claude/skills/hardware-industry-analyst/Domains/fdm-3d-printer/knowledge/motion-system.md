# FDM Motion System

## Purpose

Analyze how printer kinematics, mechanical structure, drive components and moving mass determine accuracy, speed, acceleration and vibration behavior. This module consolidates motion architectures, quantitative reference ranges, mechanical elements, performance relationships and engineering trade-offs.

## Architectures

- Cartesian / Bedslinger
- CoreXY
- CoreXZ
- H-bot
- Delta
- IDEX
- tool-changing systems

## Mechanical Elements

- frame and gantry
- linear rails / rods / wheels
- belts and pulleys
- lead screws / ball screws
- stepper motors
- idlers and tensioning
- moving bed
- toolhead

## Performance Chain

```text
Kinematic Architecture
        ↓
Moving Mass + Stiffness
        ↓
Resonance / Mechanical Error
        ↓
Maximum Acceleration
        ↓
Motion Accuracy
        ↓
Layer Registration + Surface Quality
```

## Key Metrics

- positioning accuracy
- repeatability
- acceleration
- maximum usable velocity
- vibration / resonance frequency
- belt tension stability
- frame stiffness
- gantry alignment
- backlash
- orthogonality

## Architecture Reference Ranges

These ranges are research reference bands, not universal specifications. Preserve test conditions and distinguish vendor maximums from measured sustained performance.

### Bedslinger / Cartesian

**Examples:** Prusa MK4, Ender 3, Bambu A1 series

| Metric | Budget | Mid-Range |
|---|---:|---:|
| Max Speed | 150–250 mm/s | 300–500 mm/s |
| Max Acceleration | 2,000–5,000 mm/s² | 5,000–10,000 mm/s² |
| Build Volume | 220–300 mm class | 256–330 mm class |

**Advantages**
- Simple kinematics
- Low BOM cost
- Easy to manufacture and assemble
- Large community and modification ecosystem

**Constraints**
- Moving bed mass limits Y acceleration
- Tall prints can be more sensitive to wobble and inertia
- Practical speed ceiling is generally lower than high-performance CoreXY
- Requires bed travel space

### CoreXY

**Examples:** Bambu X1/P1/X2, Voron 2.4/Trident, Creality K1/K2, Prusa Core One

| Metric | Mid-Range | High-End |
|---|---:|---:|
| Max Speed | 300–600 mm/s | 600–1,000 mm/s |
| Max Acceleration | 10,000–20,000 mm/s² | 20,000–50,000 mm/s² |
| Build Volume | 220–300 mm class | 300–350 mm class |

**Advantages**
- Stationary bed reduces moving print mass
- High speed and acceleration potential
- Compact footprint for a given build volume
- Mature kinematic ecosystem

**Constraints**
- Longer belt paths and more routing components
- Belt tension and alignment are important
- More bearings / idlers / rails can increase BOM and assembly complexity
- Extreme-speed operation increases sensitivity to belt and structural dynamics

### CoreXZ

**Examples:** Creality Ender 5 Max, Voron Switchwire variants

| Metric | Reference Range |
|---|---:|
| Max Speed | 300–700 mm/s |
| Max Acceleration | 8,000–15,000 mm/s² |

**Advantages**
- Stationary bed in Y
- Lower bed-moving mass than Bedslinger
- Suitable for some large-format architectures

**Constraints**
- Coupled X/Z kinematics
- More complex belt / screw relationships
- Smaller ecosystem than CoreXY

### IDEX

**Examples:** Raise3D E2, Sovol SV04, Snapmaker J1

| Metric | Reference Range |
|---|---:|
| Max Speed | 150–350 mm/s |
| Max Acceleration | 3,000–8,000 mm/s² |

**Modes**
- Duplicate / mirror
- Independent
- Multi-material / dual-material

**Advantages**
- Independent toolheads
- Can avoid some purge waste in dual-tool workflows
- Duplicate / mirror mode can increase production output

**Constraints**
- Higher BOM and calibration burden
- Toolhead offset and alignment are critical
- Larger mechanical envelope
- Slicer and workflow complexity

### Delta

**Examples:** FLSUN SR/V400, Anycubic Predator

| Metric | Reference Range |
|---|---:|
| Max Speed | 300–1,000 mm/s |
| Max Acceleration | 10,000–30,000 mm/s² |

**Advantages**
- Low moving effector mass
- High-speed potential
- Tall cylindrical workspace

**Constraints**
- More complex kinematics
- Calibration sensitivity
- Workspace and accuracy vary across the build area

## Evaluation Matrix

| Architecture | BOM Cost | Speed Potential | Acceleration Potential | Reliability | Manufacturability | Typical Use |
|---|---|---|---|---|---|---|
| Bedslinger | Low | Low–Medium | Low–Medium | High | High | Entry-level, education |
| CoreXY | Medium | High | High | High | Medium | Prosumer, professional |
| CoreXZ | Medium | Medium–High | Medium | Medium | Medium | Large-format |
| IDEX | High | Medium | Medium | Medium | Low–Medium | Dual-tool / production |
| Delta | Medium | High | High | Medium | Low–Medium | Tall objects, speed |

## Architecture Trade-offs

| Architecture | Typical Strength | Typical Constraint |
|---|---|---|
| Bedslinger | simple, low cost | moving-bed inertia |
| CoreXY | high-speed potential | belt routing/alignment complexity |
| CoreXZ | compact motion | coupled motion architecture |
| Delta | high speed, light toolhead | workspace and calibration complexity |
| IDEX | independent toolheads | larger mechanical envelope |

## Research Rules

- Separate nominal axis speed from repeatable production speed.
- Do not use architecture labels alone to infer performance.
- Compare moving mass, stiffness, drive components, belt / screw behavior, calibration and control together.
- Treat the reference ranges as research starting points, not universal specifications.
