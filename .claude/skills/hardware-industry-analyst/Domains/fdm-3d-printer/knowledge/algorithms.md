# FDM Algorithms

## Purpose

Analyze software algorithms that convert printer state, sensor data and toolpath commands into higher-quality, more reliable physical output.

## Core Algorithms

- motion planning
- input shaping
- pressure advance / linear advance
- flow calibration
- bed mesh compensation
- Z-offset estimation
- PID tuning
- resonance identification
- first-layer optimization
- failure detection
- automatic machine calibration

## Input Shaping

```text
Motion Command → Resonance Model → Filtered Command → Reduced Excitation
```

Evaluate shaper type, measured resonance frequency, calibration method and residual vibration.

## Pressure Advance

```text
Velocity / Acceleration Change
          ↓
Predicted Melt Pressure Change
          ↓
Extruder Compensation
          ↓
More Consistent Flow
```

## Bed Compensation

Bed probing generates a surface model that modifies Z motion during printing. Evaluate probe accuracy, mesh resolution, interpolation, thermal state and compensation range.

## Vision / Failure Detection

Possible pipeline:

```text
Camera → Image Capture → Feature Extraction / Model → Classification → Alert / Pause / Recovery
```

Separate image monitoring from active closed-loop print correction.

## Key Evaluation Dimensions

- calibration accuracy
- computational cost
- material dependence
- machine dependence
- repeatability
- automatic vs manual operation
- failure modes
- measurable print-quality improvement

## Research Rules

Do not describe a calibration feature as AI or closed-loop control unless the actual sensing, algorithm and actuator path can be established.
