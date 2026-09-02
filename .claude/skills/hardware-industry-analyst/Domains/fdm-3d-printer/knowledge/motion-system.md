# FDM Motion System

## Purpose

Analyze how printer kinematics, mechanical structure, drive components and moving mass determine accuracy, speed, acceleration and vibration behavior.

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

## Architecture Trade-offs

| Architecture | Typical Strength | Typical Constraint |
|---|---|---|
| Bedslinger | simple, low cost | moving-bed inertia |
| CoreXY | high-speed potential | belt routing/alignment complexity |
| CoreXZ | compact motion | coupled motion architecture |
| Delta | high speed, light toolhead | workspace and calibration complexity |
| IDEX | independent toolheads | larger mechanical envelope |

## Research Rules

Separate nominal axis speed from repeatable production speed. When comparing architectures, evaluate the complete mechanical system rather than the kinematic label alone.
