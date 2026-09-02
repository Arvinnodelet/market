# FDM 3D Printer Technology Model

> 本文件定义 FDM 3D 打印机的技术架构与关键性能关系。具体知识见 `knowledge/`；通用研究方法见 `Frameworks/technology.md`。

---

## 1. End-to-End Technology Chain

```text
Digital Model
    ↓
Slicer / Toolpath
    ↓
Firmware / Planner
    ↓
Motion + Extrusion + Thermal Control
    ↓
Mechanics + Motors + Heaters
    ↓
Filament → Extruder → Hotend → Nozzle
    ↓
Material Deposition
    ↓
Cooling + Layer Bonding
    ↓
Final Part
    ↑
Sensors / Vision / Calibration Feedback
```

核心研究逻辑不是孤立比较零部件，而是判断各层如何共同决定最终打印结果。

---

## 2. Technology Layers

| Layer | Modules | Core Question |
|---|---|---|
| Printing Principle | `printing-principle.md` | 材料如何稳定形成连续线材与层间结构？ |
| Motion | `motion-system.md`, `motion-control.md` | 机器能否高速、低振动、准确运动？ |
| Extrusion | `extrusion-system.md`, `hotend.md` | 能否稳定建立压力并提供所需体积流量？ |
| Thermal | `thermal-system.md` | 温度能否快速、稳定、均匀地控制？ |
| Mechanical | `mechanical-structure.md`, `build-platform.md` | 结构刚度、平面度和热床稳定性是否足够？ |
| Sensors | `sensors.md`, `vision-systems.md` | 能否测量机器状态并形成有效反馈？ |
| Electronics | `electronics.md` | 控制计算、驱动、电源和通信如何组织？ |
| Control | `motion-control.md`, `control-system.md` | 控制器如何将目标转化为实时执行？ |
| Algorithms | `algorithms.md`, `calibration-algorithms.md` | 如何补偿共振、压力、几何误差和工艺变化？ |
| Firmware / Software | `firmware.md`, `software.md`, `slicer.md` | 软件栈如何形成完整工作流？ |
| Materials | `materials.md` | 材料能力边界在哪里？ |
| Reliability | `reliability.md` | 长时间运行和异常状态下是否稳定？ |

---

## 3. Performance Causal Model

### Print Quality

```text
Motion Accuracy ─┐
Motion Vibration ├─→ Toolpath Execution ─┐
Extrusion Flow ──┤                       │
Thermal Stability┤                       ├→ Printed Geometry / Surface
Material Behavior┘                       │
Cooling / Adhesion ──────────────────────┘
```

### Productivity

```text
Usable Speed
     ×
Printable Area
     ×
Pass Efficiency
     ×
Machine Uptime
     ↓
Effective Throughput
```

不要直接使用厂商最大速度作为生产率结论。

---

## 4. Key Engineering Models

### Volumetric Flow

`Q ≈ v × h × w`

其中：

- `Q` = volumetric flow, mm³/s
- `v` = print speed, mm/s
- `h` = layer height, mm
- `w` = effective line width, mm

因此高速打印的真正瓶颈通常需要同时研究：

- Hotend melt capacity
- Nozzle geometry
- Filament rheology
- Extruder force
- Thermal power
- Motion acceleration
- Cooling

### Dynamic Motion

```text
Target Toolpath
      ↓
Motion Planner
      ↓
Acceleration / Velocity Limits
      ↓
Input Shaping
      ↓
Step Generation
      ↓
Motor / Belt / Lead Screw
      ↓
Actual Toolhead Motion
```

---

## 5. Subsystem Assessment

| Subsystem | Primary Metrics | Secondary Questions |
|---|---|---|
| Motion | usable speed, acceleration, positioning, resonance | CoreXY/Bedslinger/Delta/IDEX architecture |
| Extrusion | max stable flow, extrusion force, pressure response | DD/Bowden, gear ratio, sensor feedback |
| Hotend | max stable flow, temperature range, thermal response | heater power, heat break, nozzle material |
| Thermal | heat-up time, stability, uniformity | bed/chamber thermal architecture |
| Structure | stiffness, alignment, vibration | frame material, gantry support, bed mounting |
| Sensors | measurement accuracy, repeatability, sampling | open-loop vs feedback use |
| Electronics | processing, step rate, driver capability | MCU/AP architecture, buses |
| Control | loop stability, synchronization | motion/thermal/system coordination |
| Algorithms | compensation effectiveness | input shaping, PA, calibration, detection |
| Software | workflow quality, automation | slicer, app, cloud, API |
| Materials | supported material envelope | temperature, chamber, abrasion, moisture |
| Reliability | uptime, failure rate, serviceability | maintenance and recovery |

---

## 6. System Architecture Patterns

### Traditional MCU-Centric

```text
Slicer / Host
      ↓
MCU Firmware
 ├── Planner
 ├── Motion
 ├── Thermal
 └── Sensors
      ↓
Drivers / Actuators
```

特点：低成本、简单、成熟；计算与联网能力有限。

### Linux + MCU

```text
Linux SoC
 ├── UI / API
 ├── G-code processing
 └── Motion planning
          ↓
        MCU
 ├── Real-time step generation
 ├── Heater control
 └── Sensor acquisition
```

特点：更强的软件能力与联网能力，同时保留 MCU 实时控制。

### Distributed Control

```text
Linux / Application Processor
            ↓
       Main Controller
       ↙      ↓       ↘
 Toolhead MCU  Bed MCU  Sensor / I/O
```

适合高速、多传感器、多工具头和模块化机器。

---

## 7. Automation Stack

```text
Sensor
  ↓
Measurement
  ↓
State Estimation
  ↓
Algorithm / Model
  ↓
Parameter / Command
  ↓
Firmware / Control
  ↓
Machine Response
```

只有当反馈真正改变参数或控制命令时，才应将其描述为闭环控制或自动校正。

---

## 8. Technical Trade-offs

1. **Speed vs Quality** — 高速要求更高刚度、更高流量、更好的运动补偿
2. **Flow vs Thermal Margin** — 更高流量会压缩热传递和材料停留时间裕量
3. **Build Volume vs Rigidity** — 体积扩大通常增加结构和运动控制难度
4. **Open vs Integrated** — 开放生态更灵活，垂直整合更容易实现一致体验
5. **Automation vs Complexity** — 更多传感器与自动化增加硬件、软件和故障诊断复杂度
6. **Multi-Material vs Waste** — 自动换料提升便利性，但可能增加 purge、切换时间和材料损耗
7. **High-Temperature Capability vs Cost** — 更高温度通常需要更高等级热端、热床、腔体和安全设计

---

## 9. Research Rules

- 不把单个组件规格直接等同于整机能力。
- `600 mm/s`、`40 mm³/s` 等宣传指标必须确认测试条件。
- 最大喷嘴温度不能单独证明高温材料能力。
- 传感器存在不等于闭环控制。
- 摄像头监控不等于机器视觉闭环。
- 软件功能、固件功能、云端功能必须分开记录。
- 材料“支持”应区分官方支持、推荐配置、可打印和稳定量产。
- 对未知参数保留 `Unknown`，不要用行业常识替代证据。
