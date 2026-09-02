# FDM Software

## Purpose

Analyze the user-facing and networked software stack around the printer, including slicers, device management, monitoring and ecosystem integration.

## Stack

```text
3D Model
   ↓
Slicer
   ↓
Toolpath / G-code
   ↓
Host / Printer Software
   ↓
Firmware
   ↓
Hardware
```

Supporting services may include:

- web UI
- mobile app
- cloud platform
- model library
- camera streaming
- OTA update service
- fleet management
- API / automation

## Slicer

Evaluate:

- slicing engine
- profiles
- supports
- adaptive layer height
- infill generation
- speed / acceleration settings
- material profiles
- printer profiles
- multi-material handling
- calibration tools

## Device Software

Evaluate:

- local UI
- remote control
- job queue
- monitoring
- error reporting
- recovery
- firmware update
- user/account dependency

## Ecosystem Effect

```text
Printer Hardware
      ↕
Firmware
      ↕
Slicer
      ↕
Cloud / App
      ↕
Model / Material Ecosystem
```

Tight integration can reduce setup complexity and improve out-of-box performance, while increasing platform dependence.

## Research Indicators

- supported slicers
- proprietary slicer functions
- open APIs
- cloud dependence
- offline capability
- OTA mechanism
- model ecosystem
- multi-machine management

## Research Rules

Separate slicer capability, firmware capability and cloud capability. Do not attribute a feature to the printer hardware if it is actually implemented by the slicer or cloud service.
