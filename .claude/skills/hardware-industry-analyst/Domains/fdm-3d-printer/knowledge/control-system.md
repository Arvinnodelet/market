# FDM Control System

## Purpose

Connect sensing, motion, extrusion and thermal control into one system-level model.

## Architecture

```text
Host / UI / Slicer
        ↓
Firmware / Planner
        ↓
┌──────────────┬──────────────┬──────────────┐
Motion         Extrusion      Thermal
Control        Control        Control
↓              ↓              ↓
Motors         Extruder       Heaters/Fans
↓              ↓              ↓
Mechanics      Melt Flow      Temperature
```

## Critical Synchronization

Print quality depends on synchronization between:

- XY motion
- Z motion
- extrusion
- hotend temperature
- cooling
- bed position
- probing / compensation

## Feedback Loops

### Thermal

`Target → Controller → Heater → Temperature → Sensor → Controller`

### Bed Compensation

`Probe → Surface Model → Z Correction → Motion`

### Motion

`Command → Motor → Mechanical Motion → Encoder/Diagnostic Feedback`

### Vision

`Print → Camera → Detection → Alert/Pause/Recovery`

The last chain is monitoring unless the system demonstrably changes machine commands.

## Performance Model

```text
Print Quality = Motion + Flow + Thermal + Material + Calibration

Productivity = Speed × Deposition Rate × Uptime
```

## Research Checklist

- control architecture
- real-time scheduling
- motion/extrusion synchronization
- thermal control
- sensor feedback
- calibration loops
- fault detection
- safety interlocks
- recovery strategy

## Research Rules

Evaluate the complete control loop rather than isolated features. A sensor, algorithm or servo motor only creates system-level value when its data is integrated into a useful control or calibration path.
