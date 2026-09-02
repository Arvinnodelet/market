# FDM 3D Printer Domain Model

## Metadata

- **domain_id**: `fdm-3d-printer`
- **name_zh**: 桌面 FDM 3D 打印机
- **name_en**: Desktop FDM 3D Printer
- **category**: Additive Manufacturing / Desktop Fabrication
- **scope**: Consumer / Prosumer / Professional Desktop FDM/FFF

---

## 1. Domain Definition

FDM/FFF 通过将热塑性聚合物加热至可流动状态，并按照数字模型生成的路径逐层沉积，形成三维实体。

研究时应区分：

- **打印机能力**：机器本体能够稳定实现什么
- **材料能力**：耗材在特定热、运动、环境条件下能够实现什么
- **软件能力**：切片、校准、监测和算法能够补偿什么
- **系统能力**：硬件、固件、软件、材料和用户工作流共同形成的实际体验

---

## 2. Product Taxonomy

### Motion Architecture

- Bedslinger / Cartesian
- CoreXY
- CoreXZ
- H-bot
- Delta
- IDEX
- Toolchanger / multi-tool

### Product Segments

- Entry / Budget
- Consumer
- Prosumer
- Engineering Desktop
- High-temperature / enclosed
- Multi-material / multi-color
- Print-farm / fleet

### Material Capability

- PLA / PETG
- ABS / ASA
- TPU / flexible
- PA / PC
- CF/GF composites
- PPA / PPS / PEI / other high-performance polymers

---

## 3. End-to-End Workflow

```text
3D Model
   ↓
Slicer / Profile
   ↓
G-code / Toolpath
   ↓
Firmware / Motion Planner
   ↓
Motion + Extrusion + Thermal Control
   ↓
Filament → Extruder → Hotend → Nozzle
   ↓
Layer Deposition
   ↓
Cooling / Layer Bonding
   ↓
3D Part
   ↓
Inspection / Calibration / Feedback
```

---

## 4. Layered Technology Model

```text
Domain
  ↓
Technology
  ↓
Core Technology
  ├── Printing Principle
  ├── Motion System
  ├── Extrusion System
  └── Thermal System
  ↓
Hardware
  ├── Mechanical Structure
  ├── Hotend
  ├── Extruder
  ├── Build Platform
  └── Electronics
  ↓
Sensors
  ├── Position / Motion
  ├── Bed / Z
  ├── Filament
  ├── Thermal
  └── Vision / Ranging
  ↓
Control
  ├── Motion Control
  ├── Thermal Control
  └── System Control
  ↓
Algorithms
  ├── Input Shaping
  ├── Pressure Advance
  ├── Flow Control
  ├── Calibration
  └── Failure Detection
  ↓
Firmware / Software
  ├── Firmware
  ├── Slicer
  ├── Device Software
  └── Cloud / App
  ↓
Materials
  ↓
Reliability / Service
```

The knowledge modules are domain-specific. A domain does not need to reproduce an identical file set; modules should exist when they materially affect product performance or research conclusions.

---

## 5. Key Research Questions

### Printing Performance

- What limits usable print speed?
- What limits volumetric flow?
- How are ringing, ghosting, layer shift and extrusion artifacts controlled?
- How stable is first-layer performance?

### Material Capability

- Which materials are officially supported?
- What nozzle, hotend, bed and chamber conditions are required?
- Does the machine support abrasive and hygroscopic materials?

### Automation

- Which calibrations are automatic?
- Which sensors are used?
- Is sensing only monitoring, or does it change machine parameters?

### Ecosystem

- Open or closed filament ecosystem?
- Open or closed firmware?
- Slicer compatibility?
- Cloud / app dependency?
- Multi-material strategy?

### Manufacturing

- Frame and motion integration
- Toolhead integration
- Calibration burden
- Assembly complexity
- Vertical integration vs commodity components

---

## 6. Domain-Specific Benchmarks

| Dimension | Core Metrics |
|---|---|
| Print Quality | dimensional accuracy, surface quality, ringing, layer adhesion |
| Productivity | usable speed, acceleration, volumetric flow, uptime |
| Thermal | nozzle temperature, bed temperature, chamber capability, stability |
| Motion | kinematics, rigidity, resonance, positioning accuracy |
| Extrusion | max flow, pressure response, retraction, filament handling |
| Automation | calibration coverage, sensing, failure detection |
| Materials | supported temperature/material envelope |
| UX | setup time, calibration effort, maintenance, software workflow |
| Reliability | failure modes, service intervals, recovery behavior |
| Economics | ASP, BOM, consumables, service cost, ecosystem revenue |

---

## 7. Common Engineering Trade-offs

1. Speed vs print quality
2. Flow rate vs melt stability
3. Frame stiffness vs weight and cost
4. Build volume vs rigidity and footprint
5. Enclosure vs thermal management and cost
6. Multi-material convenience vs purge waste and feed complexity
7. Open ecosystem vs integrated UX
8. Sensor coverage vs BOM and calibration complexity
9. Automation vs diagnosability / serviceability
10. Proprietary integration vs component standardization

---

## 8. Terminology

| English | 中文 | Research Meaning |
|---|---|---|
| FDM / FFF | 熔融沉积制造 | 热塑性材料逐层挤出成形 |
| CoreXY | CoreXY 运动系统 | XY 联动、平台通常固定 |
| Bedslinger | 平台移动式 | Y 轴带动打印平台移动 |
| Hotend | 热端 | 熔化并挤出材料的组件 |
| Heat Break | 隔热管 | 热端冷热区之间的热隔离部件 |
| Nozzle | 喷嘴 | 材料最终出口 |
| Extruder | 挤出机 | 驱动丝材进给的机构 |
| Volumetric Flow | 体积流量 | `mm³/s`，评价熔化与挤出能力的重要指标 |
| Input Shaping | 输入整形 | 对运动指令进行预处理以降低共振激励 |
| Pressure Advance | 压力提前 | 补偿挤出压力动态 |
| Bed Mesh | 热床网格 | 描述打印面高度变化的补偿模型 |
| Multi-Material | 多材料 | 自动切换不同材料或颜色 |

---

## 9. Key Players

重点关注：

- Bambu Lab
- Creality
- Prusa Research
- Anycubic
- Elegoo
- QIDI
- Snapmaker
- Voron ecosystem
- UltiMaker
- Raise3D

名单用于研究入口，不代表市场排名；排名与市场份额必须通过证据单独验证。

---

## 10. Evidence Requirements

对技术能力的判断应优先使用：

1. 官方产品页、技术规格、Wiki、用户手册
2. 官方固件 / 软件文档与更新记录
3. 认证、专利、拆机及专业测试
4. 高质量长期评测和用户反馈
5. 社区讨论与供应链信息

特别注意区分：

- Advertised speed ≠ usable sustained speed
- Maximum nozzle temperature ≠ practical material capability
- Sensor presence ≠ closed-loop control
- AI monitoring ≠ autonomous control
- Supported material ≠ validated engineering-material workflow
