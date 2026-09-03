# Laser Engraver Domain Model

## Metadata

- **domain_id**: `laser-engraver`
- **name_zh**: 激光雕刻机
- **name_en**: Laser Engraver
- **category**: Fabrication Tool
- **scope**: Consumer and prosumer laser engraving/cutting systems, including diode, CO2 and fiber-based products where relevant.
- **status**: Scaffold

## 1. Domain Definition

### Definition
Laser fabrication systems use a focused optical beam to mark, engrave or cut a substrate through controlled energy deposition.

### Included
- Diode, CO2 and fiber laser systems
- Laser source, optics, motion, focus and material interaction
- Safety, enclosure, extraction, controls and fabrication software

### Excluded
- Industrial laser processing systems outside the target consumer/prosumer segment unless used as a benchmark
- Non-laser CNC fabrication tools

## 2. Product Taxonomy

| Segment | Product Type | Primary User | Main Differentiator |
|---|---|---|---|
| Entry | Open-frame diode | Maker | Low cost / compactness |
| Consumer | Enclosed diode | Maker / small business | Safety + ease of use |
| Prosumer | High-power diode / CO2 | Small business | Throughput / material range |
| Specialist | Fiber / galvo | Marking users | Metal marking / speed |

## 3. Users & Use Cases

| User | Need | Main Purchase Driver | Pain Point |
|---|---|---|---|
| Maker | Engraving / small cutting | Flexibility | Setup / safety |
| Creator | Personalized products | Workflow efficiency | Material tuning |
| Small business | Repeatable production | Throughput / reliability | Fume extraction / calibration |
| Marking business | Metal marking | Beam quality / source | Material compatibility |

## 4. Domain Workflow

```text
Artwork / CAD
     ↓
CAM / Parameter Setup
     ↓
Motion Planning
     ↓
Laser Power + Pulse / Modulation
     ↓
Optical Delivery + Focus
     ↓
Material Interaction
     ↓
Engraving / Cutting
     ↓
Inspection / Cleaning / Extraction
```

## 5. Key Technology / Subsystems

| Order | Subsystem | What It Does | Key Metrics | Knowledge Status |
|---|---|---|---|---|
| 1 | Laser Source | Generates processing energy | wavelength, optical power, stability | Planned |
| 2 | Motion System | Positions beam/workpiece | speed, acceleration, repeatability | Planned |
| 3 | Optics & Focus | Delivers and focuses beam | spot size, focus range, beam quality | Planned |
| 4 | Safety | Limits exposure and fire risk | interlock, enclosure, detection | Planned |
| 5 | Control & Software | Converts artwork into machine actions | workflow, control resolution | Planned |
| 6 | Materials | Determines process window | absorption, thickness, cut/mark quality | Planned |

## 6. Domain-Specific Benchmarks

| Dimension | Core Metrics | Notes |
|---|---|---|
| Processing | usable engraving/cutting speed | Test with defined material and quality target |
| Quality | line width, edge quality, detail | Spot size and focus must be considered |
| Power | optical output vs electrical input | Do not equate rated electrical input with optical power |
| Materials | thickness / substrate range | Validate actual process window |
| Safety | enclosure/interlock/fire response | Safety is a system property |
| UX | setup, focusing, software workflow | Include calibration burden |
| Reliability | source life, motion and extraction failures | Repeated-cycle testing preferred |

## 7. Technology Questions

- Diode vs CO2 vs fiber: which material/process envelope does each enable?
- How do beam quality, spot size, focus and power density determine results?
- Which motion architecture limits throughput?
- Which safety functions are hardware-enforced versus software-only?
- How do software parameters map to actual energy delivered to the material?

## 8. Industry Media & Data Sources

1. Manufacturer technical documentation
2. Laser safety / certification information
3. Professional fabrication reviews and teardowns
4. Engineering communities
5. Material-processing references

## 9. Terminology

| English | 中文 | Definition |
|---|---|---|
| Optical Power | 光功率 | Laser output power delivered optically |
| Wavelength | 波长 | Determines material absorption and optical system requirements |
| Spot Size | 光斑尺寸 | Effective focused beam size |
| Focus | 焦距/焦点 | Optical condition controlling energy density |
| Galvo | 振镜 | Fast angular beam steering architecture |
| Interlock | 联锁 | Safety mechanism preventing hazardous operation |

## 10. Notation & Units

- Optical power: `W`
- Wavelength: `nm`
- Speed: `mm/s` or `mm/min`
- Positioning: `mm`
- Material thickness: `mm`

## 11. Key Players

| Player | Role | Notes |
|---|---|---|
| xTool | Major consumer player | Broad diode / CO2 portfolio |
| LaserPecker | Portable / compact player | Portable engraving focus |
| Creality Falcon | Consumer / value player | Diode-focused portfolio |
| Glowforge | Premium consumer player | Enclosed workflow |
| Ortur | Value player | Budget diode systems |

名单用于研究入口，不代表实时市场排名。

## 12. Common Technical Trade-offs

| Trade-off | Option A | Option B | Impact |
|---|---|---|---|
| Source | Diode | CO2 / Fiber | Material envelope vs cost |
| Motion | Gantry | Galvo | Work area vs speed |
| Safety | Open frame | Enclosed | Accessibility vs risk control |
| Power | Higher | Lower | Throughput vs heat / cost |
| Focus | Fixed | Autofocus | Simplicity vs material flexibility |

## 13. Research Boundaries

```text
Artwork / CAD
   ↓
CAM / Control
   ↓
Motion + Optical Energy
   ↓
Material Interaction
   ↓
Mark / Cut Quality
   ↓
Safety / Reliability / Production Outcome
```

## 14. Knowledge Map

```text
Laser Source
Optics / Focus
Motion
Safety
Control / Software
Materials
Reliability / Manufacturing
```

Knowledge modules should be created only when repeated research shows that the subsystem materially affects conclusions.

## 15. Progressive Knowledge Build-Up

```text
domain.md
   ↓
technology-model.md
   ↓
first product research
   ↓
validated knowledge modules
   ↓
repeatable benchmark set
```

## Research Status

- Domain Model: Scaffold
- Technology Model: Not yet created
- Knowledge Coverage: Not yet created
