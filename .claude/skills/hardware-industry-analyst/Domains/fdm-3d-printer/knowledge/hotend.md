# FDM Hotend

## Purpose

Analyze the thermal and fluidic subsystem that melts filament and delivers stable polymer flow.

## Architecture

- heat sink
- heat break
- heat block
- heater
- temperature sensor
- nozzle
- cooling fan

## Key Parameters

- maximum operating temperature
- thermal response time
- melt-zone length
- thermal isolation
- maximum stable volumetric flow
- nozzle diameter
- nozzle material
- wear resistance

## Flow Capacity

Hotend capability is better evaluated by stable volumetric flow than by maximum temperature alone.

```text
Heater Power
   ↓
Thermal Capacity
   ↓
Melt Rate
   ↓
Volumetric Flow
   ↓
Maximum Useful Print Speed
```

## Materials

Evaluate compatibility with PLA, PETG, ABS, ASA, TPU, PA, PC and abrasive-filled materials according to temperature, wear and chamber requirements.

## Failure Modes

- clogging
- heat creep
- leakage
- thermal runaway
- nozzle wear
- temperature instability

## Research Indicators

- rated temperature
- measured flow capacity
- heater architecture
- nozzle ecosystem
- thermal sensor type
- maintenance procedure
- material compatibility

## Research Rules

Maximum temperature is not equivalent to maximum flow. Treat vendor flow claims and independent measured flow as separate evidence.
