# FDM Extrusion System

## Purpose

Analyze the material transport chain from filament entry to nozzle deposition.

## Architecture

```text
Filament → Drive Gears → Extruder → Heat Break → Melt Zone → Nozzle
```

## Extruder Types

- Direct Drive
- Bowden
- single gear
- dual gear
- geared extruder
- planetary gear systems

## Key Variables

- extrusion force
- gear ratio
- filament grip
- filament path constraint
- retraction distance and speed
- extrusion accuracy
- maximum volumetric flow
- filament diameter tolerance

## Pressure Model

The extruder must overcome friction and melt resistance while establishing nozzle pressure. During acceleration and deceleration, pressure does not change instantaneously, creating flow lag.

```text
Motion Command → Extruder Response → Melt Pressure → Nozzle Flow
```

This is the physical basis for pressure/flow compensation algorithms.

## Failure Modes

- grinding
- slipping
- clogging
- heat creep
- under-extrusion
- inconsistent flow
- filament path friction
- retraction-related defects

## Research Indicators

- extruder architecture
- drive torque
- gear ratio
- filament compatibility
- maximum flow
- retraction behavior
- sensor integration
- serviceability

## Research Rules

Do not infer extrusion performance from motor or extruder branding alone. Validate the complete extruder-hotend-material combination.
