# FDM Motion Control

## Purpose

Explain how toolpath commands become coordinated motor motion, and how planning, resonance compensation and feedback affect speed and print quality.

## Control Chain

```text
Slicer Toolpath
      ↓
Motion Planner
      ↓
Velocity / Acceleration Profile
      ↓
Input Shaping / Compensation
      ↓
Step Generation
      ↓
Motor Driver
      ↓
Motor + Mechanics
      ↓
Actual Motion
```

## Core Functions

- interpolation
- velocity planning
- acceleration control
- corner transition handling
- step generation
- motor-current control
- resonance compensation
- homing
- position feedback where available

## Motion Planning

Traditional trapezoidal planning is simple and widely used. More advanced systems may use smoother acceleration profiles and optimized cornering to reduce vibration while preserving throughput.

## Input Shaping

Input shaping filters motion commands based on measured or estimated mechanical resonances.

```text
Command → Resonance Model → Filter → Motor Command
```

Evaluate shaper type, resonance identification, calibration process and residual vibration.

## Closed Loop

Encoder or servo feedback can compare commanded and actual motion. Evaluate where the feedback is closed: motor current, rotor position, axis position, or final print geometry. These are not equivalent.

## Key Metrics

- usable acceleration
- usable velocity
- resonance frequency
- ringing amplitude
- positioning error
- repeatability
- homing repeatability
- motor temperature

## Research Rules

Do not treat advertised maximum speed as motion-system performance. Always connect motion control to moving mass, stiffness, resonance, extrusion capacity and cooling.
