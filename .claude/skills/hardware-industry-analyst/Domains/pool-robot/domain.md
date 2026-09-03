# Pool Robot Domain Model

## Metadata

- **domain_id**: `pool-robot`
- **name_zh**: 泳池清洁机器人
- **name_en**: Pool Robot
- **category**: Outdoor Service Robot
- **scope**: Consumer/prosumer autonomous pool-cleaning robots, including cordless and corded systems and their charging, filtration and navigation technologies.
- **status**: Scaffold

## 1. Domain Definition

### Definition
Pool-cleaning robots autonomously move through a swimming pool while removing debris, brushing surfaces and, in some architectures, cleaning the waterline.

### Included
- Cordless and corded pool-cleaning robots
- Navigation, propulsion, brushing, filtration and water handling
- Battery, waterproofing, charging and docking/retrieval
- Safety, controls and user software where applicable

### Excluded
- Fixed pool filtration equipment as a standalone system
- Commercial pool-cleaning equipment except as benchmarks

## 2. Product Taxonomy

| Segment | Product Type | Primary User | Main Differentiator |
|---|---|---|---|
| Entry | Floor cleaner | Residential | Simplicity / price |
| Mid | Floor + wall cleaner | Residential | Surface coverage |
| Premium | Waterline / cordless system | High-end residential | Autonomy |
| Flagship | Advanced navigation + multi-surface | Large / complex pool | Coverage + recovery |

## 3. Users & Use Cases

| User | Need | Main Purchase Driver | Pain Point |
|---|---|---|---|
| Pool owner | Routine debris removal | Convenience | Manual retrieval |
| Large-pool owner | Full-surface cleaning | Coverage / runtime | Navigation reliability |
| High-end user | Minimal intervention | Cordless + docking | Docking / waterproofing complexity |

## 4. Domain Workflow

```text
Pool / Cleaning Task
      ↓
Launch / Start
      ↓
Localization + Surface Detection
      ↓
Path Planning
      ↓
Propulsion + Brush + Filtration
      ↓
Debris Collection / Surface Cleaning
      ↓
Return / Stop / Retrieval
      ↓
Charge + Filter Maintenance
```

## 5. Key Technology / Subsystems

| Order | Subsystem | What It Does | Key Metrics | Knowledge Status |
|---|---|---|---|---|
| 1 | Navigation | Determines movement and coverage | coverage, wall handling, recovery | Planned |
| 2 | Cleaning System | Collects debris and cleans surfaces | pickup, brushing, filtration | Planned |
| 3 | Power & Propulsion | Drives robot and cleaning mechanisms | runtime, traction, efficiency | Planned |
| 4 | Waterproofing | Protects electronics and battery | sealing, pressure, corrosion | Planned |
| 5 | Docking / Charging | Supports autonomous recovery where available | docking success, charge time | Planned |
| 6 | Sensors & Control | Detects orientation, surfaces and faults | accuracy, response, false detection | Planned |

## 6. Domain-Specific Benchmarks

| Dimension | Core Metrics | Notes |
|---|---|---|
| Cleaning | debris pickup, brushing, filtration | Standardize debris, water and pool surface |
| Coverage | floor/wall/waterline coverage | Repeat runs from different starting points |
| Navigation | route efficiency, recovery, wall handling | Pool geometry materially affects results |
| Runtime | cleaning time / pool area | Include filtration load and propulsion |
| Waterproofing | leakage / pressure-cycle robustness | Safety-critical subsystem |
| Retrieval | return-to-edge / retrieval effort | Cordless and corded architectures differ |
| UX | setup, cleaning cycle, filter service | Include underwater handling burden |

## 7. Technology Questions

- How is position estimated without reliable GNSS indoors/underwater?
- How are walls, waterline and pool geometry detected?
- How do propulsion and brush geometry affect cleaning coverage?
- How is waterproofing implemented for repeated immersion and pressure cycles?
- How do battery, filtration load and propulsion determine runtime?
- Which functions are autonomous versus user-assisted?

## 8. Industry Media & Data Sources

1. Manufacturer technical documentation
2. Safety / certification information
3. Professional pool-equipment reviews
4. Engineering communities and teardown reports
5. Controlled pool-cleaning tests

## 9. Terminology

| English | 中文 | Definition |
|---|---|---|
| Waterline Cleaning | 水线清洁 | Cleaning the transition area near the water surface |
| Filtration | 过滤 | Capturing debris from pool water |
| Propulsion | 推进 | Motor-driven movement through water |
| Waterproofing | 防水密封 | Protection of electronics against water ingress |
| Cordless | 无线 | Battery-powered without a tether cable |
| Docking | 回充/回收 | Autonomous return or charging/retrieval mechanism |

## 10. Notation & Units

- Pool area: `m²`
- Pool depth: `m`
- Runtime: `min` / `h`
- Battery: `Wh`
- Flow rate: `L/min`
- Speed: `m/s`
- Pressure: `Pa` where relevant to fluidic systems

## 11. Key Players

| Player | Role | Notes |
|---|---|---|
| Aiper | Major cordless player | Consumer cordless pool robots |
| Beatbot | Premium challenger | Advanced cordless systems |
| Maytronics / Dolphin | Established leader | Broad pool-cleaning portfolio |
| Polaris / Fluidra | Established player | Multiple pool-cleaning architectures |
| WYBOT | Value / challenger | Consumer pool robots |

名单用于研究入口，不代表实时市场排名。

## 12. Common Technical Trade-offs

| Trade-off | Option A | Option B | Impact |
|---|---|---|---|
| Power | Corded | Cordless | Runtime / autonomy vs cable management |
| Navigation | Reactive | Model-based / sensor-rich | Cost vs coverage reliability |
| Propulsion | Wheel / track | Specialized water drive | Surface handling vs complexity |
| Filtration | High capture | Low restriction | Cleaning quality vs energy / flow |
| Charging | Manual | Autonomous dock | User effort vs waterproof docking complexity |

## 13. Research Boundaries

```text
Pool Environment
   ↓
Localization / Perception
   ↓
Planning
   ↓
Propulsion + Cleaning
   ↓
Debris / Surface Result
   ↓
Retrieval / Charging / Maintenance
   ↓
User Outcome
```

## 14. Knowledge Map

```text
Navigation
Cleaning / Filtration
Power / Propulsion
Waterproofing
Sensors / Control
Docking / Charging
Software
Reliability / Manufacturing
```

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
repeatable pool / surface benchmarks
```

## Research Status

- Domain Model: Scaffold
- Technology Model: Not yet created
- Knowledge Coverage: Not yet created
