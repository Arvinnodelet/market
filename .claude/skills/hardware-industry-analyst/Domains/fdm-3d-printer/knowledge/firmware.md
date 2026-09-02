# FDM Firmware Knowledge

## Purpose

研究 FDM 3D 打印机固件如何连接上层软件与底层实时控制，并分析其对运动、挤出、热控、传感器、自动化和生态的影响。

---

## 1. Firmware Position in System

```text
Slicer / Cloud / UI
        ↓
G-code / Commands
        ↓
Firmware
 ├── Parser
 ├── Motion Planner
 ├── Kinematics
 ├── Extrusion Control
 ├── Thermal Control
 ├── Sensor Processing
 ├── Calibration
 └── Safety / Fault Handling
        ↓
MCU / Distributed Controllers
        ↓
Drivers / Heaters / Sensors
```

固件不是简单的“电机驱动程序”，而是整机实时控制层。

---

## 2. Firmware Architectures

### MCU-Centric

典型：Marlin。

- Planner、运动、热控和 I/O 主要运行在 MCU
- BOM 低
- 架构成熟
- 受 MCU 运算、内存和实时任务限制

### Host + MCU

典型：Klipper。

```text
Linux Host
 ├── G-code processing
 ├── Kinematics
 ├── Motion planning
 ├── Input shaping
 └── API / Web interface
          ↓
       MCU
 ├── Step generation
 ├── ADC / sensors
 ├── Heater control
 └── GPIO
```

### Distributed

多个 MCU 分担工具头、主板、热床和传感器任务，适合高集成、高速、多工具系统。

---

## 3. Major Firmware Families

| Firmware | Architecture | Strength | Limitation | Typical Position |
|---|---|---|---|---|
| Marlin | MCU-centric | Mature / low cost | Compute ceiling | Budget / traditional |
| Klipper | Linux + MCU | Flexible / high-performance | Requires host | DIY / prosumer |
| RepRapFirmware | MCU / distributed | Strong kinematics / web control | Smaller ecosystem | Premium DIY |
| Vendor Firmware | Integrated HW/SW | OOBE / optimization | Less transparent | Consumer systems |

---

## 4. Motion Functions

重点分析：

- Kinematics
- Acceleration / velocity planning
- Junction / corner handling
- Step generation
- Input shaping
- Resonance compensation
- Pressure advance / linear advance
- Synchronization between axes

### Important distinction

`Maximum speed` is a machine specification; firmware capability is only one limiting factor.

实际可用速度还受到：

```text
Firmware
 + Motor / Driver
 + Belt / Pulley
 + Frame
 + Toolhead Mass
 + Hotend Flow
 + Cooling
 + Material
```

共同限制。

---

## 5. Thermal Control

固件负责：

- Heater PWM
- PID control
- Temperature sampling
- Thermal runaway protection
- Bed / nozzle / chamber coordination
- Heating state management

研究时关注：

- PID tuning strategy
- Sampling rate
- Sensor type
- Protection thresholds
- Fault recovery

---

## 6. Sensor Integration

```text
Sensor
  ↓
ADC / Bus
  ↓
Firmware Driver
  ↓
Filtering / Validation
  ↓
State / Measurement
  ↓
Calibration / Control / Alert
```

必须确认传感器数据最终进入哪个功能：

- Calibration
- Motion control
- Thermal control
- Material handling
- Failure detection
- User alert

**传感器存在 ≠ 闭环控制。**

---

## 7. Calibration Functions

常见固件校准：

- Z-offset
- Bed mesh
- PID tuning
- Flow calibration
- Pressure advance
- Input shaping
- Motor / belt characterization
- Toolhead / nozzle alignment

自动校准研究应拆成：

```text
Measurement → Estimation → Parameter → Application
```

---

## 8. Safety & Fault Handling

固件应覆盖：

- Thermal runaway
- Sensor disconnect
- Over-temperature
- Endstop fault
- Motor fault
- Filament runout
- Door / enclosure state
- Power-loss recovery
- Print pause / resume

研究重点不是功能列表，而是：**检测 → 判定 → 动作 → 恢复**。

---

## 9. Open vs Closed Firmware

### Open

优势：

- 可修改
- 社区生态
- 硬件兼容性
- 易于二次开发

代价：

- 用户配置复杂
- HW/SW 优化不一定充分
- 版本兼容需要管理

### Closed / Integrated

优势：

- 硬件、固件、算法协同优化
- 更好的 OOBE
- 更容易实现统一自动化

代价：

- 可见性低
- 生态锁定
- 第三方修改能力有限

---

## 10. Firmware Evaluation Framework

| Dimension | Questions |
|---|---|
| Performance | planner / step generation 是否满足整机需求？ |
| Control | 是否支持关键控制回路？ |
| Automation | 自动校准覆盖程度？ |
| Reliability | 故障检测与恢复能力？ |
| Openness | 源码、配置、API 是否开放？ |
| Ecosystem | 社区、插件、工具链？ |
| Integration | HW/FW/Software 是否协同？ |
| Security | OTA、签名、认证和访问控制？ |

---

## 11. Evidence Rules

对厂商宣称的“AI、闭环、智能校准、高速”等功能，应追踪到：

`Sensor → Data → Algorithm → Parameter/Command → Machine Response`

如果只能证明存在摄像头、加速度计或其他传感器，应标记为 **Reported / Confirmed sensor capability**，而不能直接升级为 **closed-loop control**。
