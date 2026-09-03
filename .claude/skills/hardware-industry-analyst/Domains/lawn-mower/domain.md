# Robot Lawn Mower Domain Model

## Metadata

- **domain_id**: `lawn-mower`
- **name_zh**: 割草机器人
- **name_en**: Robot Lawn Mower
- **category**: Outdoor Service Robot
- **scope**: Consumer/prosumer autonomous lawn mowing systems and their navigation, cutting, safety, charging and software subsystems.
- **status**: Scaffold

## 1. Domain Definition

### Definition
Robot lawn mowers autonomously navigate outdoor grass areas and repeatedly cut vegetation according to user-defined zones, schedules and constraints.

### Included
- Boundary-wire and wire-free navigation
- GNSS/RTK, vision, IMU and other localization/perception systems
- Cutting, propulsion, battery, charging and safety systems
- App, mapping, scheduling and fleet/zone management

### Excluded
- Manual walk-behind or ride-on mowers
- Commercial autonomous agricultural machinery except as benchmarks

## 2. Product Taxonomy

| Segment | Product Type | Primary User | Main Differentiator |
|---|---|---|---|
| Entry | Boundary-wire mower | Small lawn owner | Low cost |
| Mid | Wire-free navigation mower | Residential user | Installation convenience |
| Premium | RTK / vision mower | Large / complex lawn | Navigation accuracy |
| Flagship | Advanced AWD / multi-zone | High-end user | Terrain handling + automation |

## 3. Users & Use Cases

| User | Need | Main Purchase Driver | Pain Point |
|---|---|---|---|
| Residential | Routine mowing | Convenience | Boundary setup |
| Large-lawn owner | Multi-zone autonomy | Coverage / runtime | Localization failures |
| Complex-yard owner | Slopes / obstacles | Terrain capability | Recovery / safety |

## 4. Domain Workflow

```text
Lawn / User Map
      ↓
Zone + Schedule Planning
      ↓
Localization + Perception
      ↓
Path Planning
      ↓
Propulsion + Cutting
      ↓
Grass / Terrain Interaction
      ↓
Return to Dock / Charge
      ↓
Next Scheduled Cycle
```

## 5. Key Technology / Subsystems

| Order | Subsystem | What It Does | Key Metrics | Knowledge Status |
|---|---|---|---|---|
| 1 | Navigation & Localization | Determines position and route | accuracy, availability, recovery | Planned |
| 2 | Cutting System | Cuts and manages grass | cut quality, width, height | Planned |
| 3 | Sensors & Safety | Detects obstacles and unsafe states | detection, false negatives, response | Planned |
| 4 | Power & Propulsion | Drives robot and cutting system | runtime, slope, traction | Planned |
| 5 | Docking | Enables autonomous charging | docking success, charge time | Planned |
| 6 | App & Software | Maps, zones, schedules and alerts | usability, recovery | Planned |

## 6. Domain-Specific Benchmarks

| Dimension | Core Metrics | Notes |
|---|---|---|
| Navigation | position accuracy, route efficiency, recovery | Test under trees, open sky and boundary conditions |
| Terrain | slope, wet grass, uneven ground | Include traction and wheel-slip behavior |
| Cutting | cut quality, width, height consistency | Standardize grass height and density |
| Safety | lift/tilt, obstacle, blade stop response | Hardware safety path must be distinguished from app behavior |
| Runtime | mowing time / area per charge | Include terrain and cutting load |
| Docking | autonomous return / docking success | Repeat across starting positions |
| UX | installation, map setup, scheduling | Wire-free products shift burden into calibration |

## 7. Technology Questions

- Boundary wire vs RTK vs vision: how does each constrain the operating envelope?
- How are localization failures detected and recovered?
- How does traction affect path accuracy and cutting coverage?
- Which safety functions are independent of software?
- How does terrain, grass condition and weather change power consumption?

## 8. Industry Media & Data Sources

1. Manufacturer technical documentation
2. Safety / regulatory information
3. Professional outdoor robotics reviews
4. Engineering communities
5. Controlled lawn-mowing tests

## 9. Terminology

| English | 中文 | Definition |
|---|---|---|
| RTK GNSS | RTK 高精度卫星定位 | Differential GNSS technique for high-accuracy positioning |
| Boundary Wire | 边界线 | Physical perimeter signal used to constrain robot area |
| Virtual Boundary | 虚拟边界 | Software-defined operating boundary |
| AWD | 四轮驱动 | Drive architecture improving traction |
| Geofence | 电子围栏 | Geographic constraint for operation / anti-theft |
| Docking | 回充 | Autonomous return and charging |

## 10. Notation & Units

- Lawn area: `m²`
- Positioning error: `cm` / `m`
- Speed: `m/s`
- Battery: `Wh`
- Cutting width: `mm`
- Slope: `°` or `%`

## 11. Key Players

| Player | Role | Notes |
|---|---|---|
| Husqvarna | Established leader | Broad autonomous mower portfolio |
| Segway Navimow | Wire-free challenger | RTK-oriented systems |
| Mammotion | Premium challenger | RTK / terrain-oriented systems |
| Worx | Value player | LANDROID ecosystem |
| ECOVACS | Emerging entrant | Robotics platform extension |

名单用于研究入口，不代表实时市场排名。

## 12. Common Technical Trade-offs

| Trade-off | Option A | Option B | Impact |
|---|---|---|---|
| Localization | Boundary wire | Wire-free | Installation burden vs infrastructure complexity |
| Positioning | GNSS / RTK | Vision / hybrid | Outdoor availability vs perception complexity |
| Drive | 2WD | AWD | Cost vs terrain capability |
| Cutting | Single blade | Multi-disc / multi-blade | Simplicity vs cutting width / redundancy |
| Dock | Manual return | Autonomous dock | User effort vs navigation complexity |

## 13. Research Boundaries

```text
Lawn / Terrain
   ↓
Localization + Perception
   ↓
Planning
   ↓
Propulsion + Cutting
   ↓
Coverage / Cut Quality
   ↓
Safety / Charging / Maintenance
   ↓
User Outcome
```

## 14. Knowledge Map

```text
Navigation / Localization
Cutting
Sensors / Safety
Power / Propulsion
Docking
Software / App
Materials / Environment
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
repeatable terrain / navigation benchmarks
```

## Research Status

- Domain Model: Scaffold
- Technology Model: Not yet created
- Knowledge Coverage: Not yet created
