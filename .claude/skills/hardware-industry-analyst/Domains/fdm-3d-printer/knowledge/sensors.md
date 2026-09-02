# FDM Sensors

## Purpose

Map sensing technologies to physical variables, feedback loops and automation functions. Evaluate the sensor as part of a system, not as an isolated component.

## Sensor Categories

### Motion / Position
- endstops
- hall sensors
- rotary encoders
- motor position feedback

### Bed / Z Sensing
- inductive
- capacitive
- eddy current
- load cell
- strain gauge
- contact probes

### Material
- filament runout
- filament motion
- filament diameter
- material / spool identification

### Thermal
- thermistor
- PT100 / PT1000
- thermocouple
- chamber temperature

### Vision / Ranging
- camera
- LiDAR / laser ranging
- depth sensing
- AI image analysis

## Sensor-to-Function Map

| Sensor | Variable | Typical Function |
|---|---|---|
| Endstop | position/contact | homing |
| Inductive | distance to metal | bed probing |
| Eddy current | conductive-surface distance | Z / bed sensing |
| Load cell | force | nozzle contact / probing |
| Thermistor | temperature | thermal control |
| Encoder | rotation/position | motion feedback |
| Camera | image | monitoring / failure detection |

## Feedback Architecture

```text
Physical Variable → Sensor → Conditioning → Controller → Decision → Actuator
                                      ↑                         │
                                      └──────── Feedback ────────┘
```

## Key Evaluation Dimensions

- sensing principle
- target material dependence
- accuracy / repeatability
- sampling rate
- noise
- temperature sensitivity
- calibration requirement
- integration complexity
- cost
- failure behavior

## Research Rules

The presence of a sensor does not prove closed-loop control. Identify what is measured, where it is measured, how often it is sampled, how the firmware uses it, and what actuator or calibration result changes afterward.
