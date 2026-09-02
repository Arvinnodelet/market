# FDM Printing Principle

## Purpose

Explain the physical process that converts thermoplastic filament into a three-dimensional part, and provide the foundation for evaluating printer architecture and performance.

## Process Chain

```text
Filament → Feeding → Melting → Pressurization → Nozzle Flow → Deposition → Cooling → Layer Bonding → Part
```

## Core Concepts

- FDM / FFF additive manufacturing
- filament feeding and extrusion
- polymer melting and rheology
- nozzle flow
- line width
- layer height
- extrusion width
- volumetric flow
- deposition temperature
- cooling and solidification
- interlayer bonding
- shrinkage and warping

## Key Relationships

Approximate volumetric flow:

`Q ≈ v × h × w`

where `v` is print velocity, `h` is layer height, and `w` is effective line width.

The practical speed limit is therefore not simply the advertised motion speed. It is constrained by extrusion capacity, thermal capacity, material behavior, motion dynamics and cooling.

## Performance Chain

```text
Motion Speed
   + Layer Height
   + Line Width
        ↓
Required Volumetric Flow
        ↓
Extrusion / Melt Capacity
        ↓
Stable Material Deposition
        ↓
Cooling + Layer Bonding
        ↓
Final Part Quality
```

## Research Indicators

- maximum volumetric flow
- usable print speed rather than theoretical axis speed
- layer height range
- nozzle diameter
- extrusion width
- first-layer quality
- dimensional accuracy
- surface quality
- interlayer strength
- material compatibility

## Research Rules

Do not equate maximum motion speed with actual printing productivity. Distinguish vendor specifications, measured test results and engineering estimates.
