# FDM Electronics

## Purpose

Analyze the electrical architecture connecting computation, sensing, motion, extrusion, heating, communication and safety.

## Layered Architecture

```text
Application Processor / Host
        ↓
Motion Controller / MCU
        ↓
┌──────────┬──────────┬──────────┬──────────┐
Motion   Extrusion   Thermal    Sensors   Network
Drivers   Driver     Drivers     I/O       I/O
```

Modern architectures may separate application processing, real-time motion control and toolhead control.

## Architecture Patterns

### MCU-only

Typical of legacy Marlin systems. Low cost and simple, but application processing and real-time control share resources.

### Linux SoC + MCU

Linux handles UI, networking, camera and higher-level planning while an MCU performs deterministic real-time control. Common in Klipper-class architectures.

### AP + Motion MCU + Toolhead MCU

A further separation used by some integrated systems: application processor, dedicated motion controller and distributed toolhead controller.

## Components

- MCU / application processor
- stepper drivers
- FOC / servo drivers
- heater MOSFETs / drivers
- temperature interfaces
- Z / force / motion sensor interfaces
- fans
- power supply
- USB / CAN / UART / SPI / I²C / Ethernet / Wi-Fi interfaces

## Electrical Design Topics

- current capacity
- thermal management
- power distribution
- EMI / EMC
- signal integrity
- grounding
- connector reliability
- protection circuits
- cable management
- emergency-stop behavior

## Communication

Common buses include UART, SPI, I²C, USB, CAN/CAN-FD and Ethernet. Evaluate bandwidth, determinism, topology, wiring complexity and fault isolation rather than bus speed alone.

## Research Indicators

- controller architecture
- MCU / SoC family
- motor-driver architecture
- heater power
- PSU capacity
- communication buses
- distributed controller architecture
- sensor interfaces
- safety protection
- expansion capability

## Evidence Rules

Identify components from official documentation, board documentation, teardown evidence or clear board photographs. Do not infer the complete architecture from one chip model or a marketing term such as "servo" or "AI".
