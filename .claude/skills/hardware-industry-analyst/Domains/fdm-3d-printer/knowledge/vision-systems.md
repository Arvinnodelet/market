# Vision Systems

## Purpose

This document summarizes machine vision systems used in modern 3D printers.

Focus on architecture, capabilities, limitations, and engineering tradeoffs.

---

# Camera Monitoring

## Functions

- Remote monitoring
- Timelapse
- Failure observation

## Advantages

- Low cost
- Easy deployment

## Limitations

- Human interpretation required

---

# First Layer Inspection

## Purpose

Detect:

- Adhesion issues
- Missing extrusion
- Warping
- Surface defects

## Typical Vendors

- Bambu Lab
- Formlabs

## Engineering Challenges

- Lighting consistency
- Surface reflection
- Print-bed variation

---

# Spaghetti Detection

## Principle

Computer vision identifies abnormal filament structures.

## Advantages

- Prevents wasted print time

## Challenges

- False positives
- Model variability

---

# AI Failure Detection

## Architecture

Camera
→ ISP
→ CNN Model
→ Defect Classification
→ User Alert

## Typical Defects

- Spaghetti
- Layer shift
- Detachment
- Missing layers

---

# Edge AI vs Cloud AI

| Dimension | Edge | Cloud |
|------------|--------|--------|
| Latency | Low | High |
| Privacy | High | Low |
| Cost | Higher Hardware | Higher Server |
| Reliability | High | Network Dependent |

---

# Industry Trend

2020-2022

- Basic monitoring cameras

2022-2025

- AI spaghetti detection

2025+

- Sensor fusion
- Vision-guided calibration
- Closed-loop printing