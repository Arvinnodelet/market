# FDM Calibration Algorithms

## Purpose

Analyze automatic and semi-automatic procedures that characterize the printer and convert measurements into compensation parameters.

## Calibration Chain

```text
Machine State
   ↓
Measurement
   ↓
Model / Parameter Estimation
   ↓
Compensation Parameter
   ↓
Firmware / Slicer
   ↓
Improved Print Result
```

## Main Calibration Types

- Z offset
- bed mesh
- extrusion / flow ratio
- pressure advance
- input shaping / resonance
- PID tuning
- first-layer calibration
- toolhead / nozzle alignment
- belt or motion characterization

## Key Evaluation Dimensions

- measurement method
- repeatability
- calibration time
- temperature dependence
- material dependence
- automatic vs manual operation
- parameter scope
- persistence / per-material profiles

## Research Rules

A calibration feature should be decomposed into sensor, measurement procedure, algorithm, resulting parameter and where that parameter is applied. Avoid describing a wizard as "AI" unless an actual learned model is used.
