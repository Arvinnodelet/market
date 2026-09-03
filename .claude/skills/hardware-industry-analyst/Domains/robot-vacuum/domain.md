# Robot Vacuum Domain Model

## Metadata

- **domain_id**: `robot-vacuum`
- **name_zh**: 扫地机器人
- **name_en**: Robot Vacuum
- **category**: Home Service Robot
- **scope**: Consumer and prosumer autonomous floor-cleaning robots, including robot vacuum/mop systems and multifunction docking stations.

## 1. Domain Definition

### Definition
Robot vacuum systems combine autonomous navigation, floor cleaning, sensing, control, software and often a multifunction base station to perform recurring household cleaning with limited user intervention.

### Included
- Robot vacuum and vacuum-mop products
- Navigation, localization, mapping and obstacle avoidance
- Vacuuming, brushing, mopping and carpet handling
- Sensors, perception, control, firmware and app/cloud software
- Multifunction base stations, charging and consumable management

### Excluded
- Cordless stick vacuums and handheld vacuums without autonomous navigation
- Commercial cleaning robots for industrial environments
- General-purpose mobile robots not designed primarily for floor cleaning

## 2. Product Taxonomy

| Segment | Product Type | Primary User | Main Differentiator |
|---|---|---|---|
| Entry | Basic robot vacuum | Price-sensitive household | Low cost, simple navigation |
| Mid | Vacuum + mop robot | Mainstream household | Balanced cleaning and automation |
| Premium | Advanced vacuum-mop | Tech-oriented household | Better perception, mopping and automation |
| Flagship | Multifunction robot + dock | High-automation household | Self-emptying, washing, drying, refill and advanced navigation |

Technology taxonomy should separately distinguish navigation architecture, cleaning architecture, sensing stack and base-station architecture.

## 3. Users & Use Cases

| User | Need | Workflow | Purchase Driver | Pain Point |
|---|---|---|---|---|
| Mainstream household | Routine floor cleaning | Schedule → clean → return → charge | Convenience | Missed areas / maintenance |
| Pet household | Hair and debris handling | Frequent vacuuming | Brush/suction performance | Hair tangling / odor |
| Multi-room home | Reliable autonomous navigation | Map → plan → clean zones | Navigation reliability | Stuck / missed rooms |
| High-automation user | Minimal intervention | Clean → dock service → resume | Dock automation | Dock size / consumables |

## 4. Domain Workflow

```text
User / Schedule
      ↓
Map / Task Planning
      ↓
Localization + Navigation
      ↓
Obstacle / Surface Perception
      ↓
Motion + Vacuuming + Mopping
      ↓
Return / Docking
      ↓
Auto-Empty / Mop Wash / Dry / Refill
      ↓
Status Feedback / Maintenance
      ↑
Sensors + Software + User Input
```

## 5. Key Technology / Subsystems

| Order | Subsystem | What It Does | Key Metrics | Knowledge Module |
|---|---|---|---|---|
| 1 | Navigation | Localization, path planning and coverage | localization error, coverage, recovery | `knowledge/navigation.md` |
| 2 | Cleaning System | Vacuuming, brushing and mopping | pickup, edge cleaning, hair handling, water use | `knowledge/cleaning-systems.md` |
| 3 | Sensors | Perception and machine-state sensing | detection range, accuracy, false positives | `knowledge/sensors.md` |
| 4 | Mapping & Software | Maps, task logic, UI and cloud functions | map stability, usability, automation | `knowledge/mapping.md` |
| 5 | Base Station | Charging and maintenance automation | empty/wash/dry/refill effectiveness | `knowledge/base-station.md` |
| 6 | Firmware | Real-time control and system orchestration | response, recovery, OTA/serviceability | `knowledge/firmware.md` |

## 6. Domain-Specific Benchmarks

| Dimension | Core Metrics | Measurement / Comparison Notes |
|---|---|---|
| Navigation | localization, coverage, route efficiency | Test by room layout, obstacles and repeated runs |
| Cleaning | debris pickup, edge cleaning, hair handling | Use standardized debris, floor and moisture conditions |
| Mopping | stain removal, water use, carpet handling | Separate pad/roller design from software behavior |
| Perception | obstacle detection, classification, avoidance | Distinguish sensing hardware from actual avoidance performance |
| Docking | docking success, empty/wash/dry effectiveness | Include dirty conditions and repeated cycles |
| Reliability | stuck rate, missed tasks, component failures | Measure over repeated autonomous cycles |
| UX | setup, map editing, scheduling, maintenance | Include app and physical maintenance workflow |
| Economics | street price, consumables, service burden | Compare total ownership cost, not only robot price |

> Pa、DPI-like component specifications, sensor counts and advertised AI features must not be treated as direct system-performance equivalents. Test conditions and workload must be stated.

## 7. Technology Questions

### Core Technology
- Which navigation architecture is used and what limits its operating envelope?
- How are coverage planning, obstacle avoidance and recovery coupled?

### Hardware
- How are drive, brush, fan, pump and mopping mechanisms architected?
- What design choices determine cleaning performance and energy consumption?

### Sensors & Control
- Which sensors are used for localization, obstacle avoidance, cliff detection and surface recognition?
- Which signals affect control decisions versus simple monitoring?

### Algorithms / Software
- How are maps built, segmented and persisted?
- How are route planning, obstacle classification and task recovery implemented?

### Materials / Environment
- How do floor type, carpet, thresholds, hair and moisture affect performance?
- How do brush, filter and mop materials affect service intervals?

### Manufacturing / Reliability
- How are dust/water paths, sealing, motors, pumps and docking interfaces designed for repeated cycles?
- Which modules are consumable, serviceable or high-risk failure points?

## 8. Industry Media & Data Sources

1. Official manufacturer documentation and service information
2. Regulatory / certification databases
3. Professional reviews and controlled cleaning tests
4. Robot-vacuum specialist media and teardown sources
5. Engineering communities and user reports
6. Supply-chain sources when independently corroborated

## 9. Terminology

| English | 中文 | Definition | Notes |
|---|---|---|---|
| LiDAR SLAM | 激光 SLAM | Laser range sensing combined with localization and mapping | Do not equate sensor presence with navigation quality |
| vSLAM | 视觉 SLAM | Camera-based visual localization and mapping | Sensitive to lighting / texture |
| dToF | 直接飞行时间 | Time-of-flight depth measurement | Do not call it structured light by default |
| LDS | 激光测距系统 | Laser distance sensing, often used in rotating LiDAR assemblies | Naming varies by vendor |
| Obstacle Avoidance | 避障 | Detecting and avoiding objects during motion | Requires sensing + perception + planning + control |
| Base Station | 基站 | Dock providing charging and optional maintenance functions | Function set varies by model |
| Auto-Empty | 自动集尘 | Transfers dust from robot to station | Effectiveness depends on airflow/path design |
| Mop Lifting | 拖布抬升 | Raises mop assembly when carpet is detected | Hardware and control both matter |

## 10. Notation & Units

- Cleaning area: `m²`
- Suction pressure: `Pa` — treat as a vendor/component metric, not a standalone cleaning-performance metric
- Battery energy: `Wh`; capacity may also be reported as `mAh` with voltage context
- Noise: `dB(A)`
- Water volume: `mL` / `L`
- Navigation / sensor distances: `mm` / `m`

## 11. Key Players

| Player | Chinese Name | Role | Main Products |
|---|---|---|---|
| Roborock | 石头科技 | Premium leader / major player | S, Qrevo and related systems |
| Ecovacs | 科沃斯 | Major player | DEEBOT |
| Dreame | 追觅 | Major player | X, L and related systems |
| iRobot | — | Established incumbent | Roomba |
| Narwal | 云鲸 | Mopping-focused player | Freo |
| Xiaomi | 小米 | Value / ecosystem player | Robot vacuum ecosystem |
| Samsung | 三星 | Premium niche player | Jet Bot |
| SharkNinja | — | Major US-market player | Shark robot vacuum lines |

名单用于研究入口，不代表实时市场份额或排名。

## 12. Common Technical Trade-offs

| Trade-off | Option A | Option B | Impact |
|---|---|---|---|
| Navigation | LiDAR-heavy | Vision / hybrid | Cost, lighting robustness, obstacle perception |
| Cleaning | High suction | Lower power / optimized airflow | Pickup vs energy/noise |
| Mopping | Rotary pads | Roller / vibrating systems | Stain handling vs complexity |
| Dock | Compact | Full-service dock | Footprint vs autonomy |
| Perception | More sensors | Fewer sensors + stronger algorithms | BOM vs software complexity |
| Battery | Larger | Smaller / faster charging | Runtime vs weight / charge time |

## 13. Research Boundaries

```text
Home Environment
      ↓
Perception / Localization
      ↓
Mapping / Planning
      ↓
Motion + Cleaning Actuation
      ↓
Cleaning Result
      ↓
Docking / Maintenance
      ↓
User Outcome / Ownership Cost
```

Adjacent domains such as generic batteries, motors, semiconductor components and cloud infrastructure should be treated as supporting technologies unless they materially change product capability.

## 14. Knowledge Map

```text
Navigation
├── Localization / SLAM
├── Mapping / Planning
└── Recovery

Cleaning
├── Vacuum / Airflow
├── Brush / Hair Handling
└── Mopping / Water Management

Perception & Control
├── Sensors
├── Obstacle Avoidance
└── Firmware

Dock
├── Auto-Empty
├── Mop Washing / Drying
└── Water Management

Software
└── App / Map / Cloud / OTA
```

## 15. Progressive Knowledge Build-Up

```text
domain.md
   ↓
technology-model.md
   ↓
knowledge modules
   ↓
product reports / validation
   ↓
update technical benchmarks and failure modes
```

Promote only reusable and sufficiently validated information into long-term knowledge.

## Research Status

- Domain Model: Active
- Technology Model: Active
- Knowledge Coverage: Core subsystems covered; continue deepening perception, actuation and reliability as needed.
