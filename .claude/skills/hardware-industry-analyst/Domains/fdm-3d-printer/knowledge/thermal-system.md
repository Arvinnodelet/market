# FDM Thermal System

## Purpose

Analyze heating, temperature sensing, heat transfer and cooling across hotend, bed and chamber.

## Subsystems

- hotend heater
- hotend temperature sensor
- heat sink and fan
- heated bed
- bed temperature sensor
- chamber heater
- chamber circulation
- electronics cooling

## Control Chain

```text
Target Temperature
      ↓
Controller
      ↓
Heater Power
      ↓
Thermal Response
      ↓
Temperature Sensor
      └──────── feedback ────────┘
```

## Key Metrics

- maximum temperature
- heating time
- temperature stability
- spatial temperature uniformity
- thermal overshoot
- chamber temperature
- heater power
- cooling capacity

## Material Relationship

High-temperature and engineering materials may require higher nozzle temperature, heated bed temperature, controlled chamber temperature and lower thermal gradients.

## Failure Modes

- thermal runaway
- sensor failure
- heater failure
- heat creep
- insufficient cooling
- bed temperature non-uniformity
- warping from thermal gradients

## Research Rules

Separate setpoint range from actual usable temperature and distinguish chamber temperature from local toolhead or enclosure temperature.
