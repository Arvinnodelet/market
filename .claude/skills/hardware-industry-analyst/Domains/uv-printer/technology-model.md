# UV Printer Technology Model

> 本文件定义 UV Printer 的领域技术架构、性能关系和工程问题。具体知识见 `knowledge/`；通用技术分析方法见 `Frameworks/technology.md`。

## System Architecture

```text
                    User / Artwork
                          ↓
                    RIP / Software
                          ↓
                Controller / Electronics
                          │
          ┌───────────────┼────────────────┐
          ↓               ↓                ↓
     Printhead        Motion System      UV Curing
          ↑               ↓                ↓
      Ink System      Media Platform       UV Dose
          └───────────────┴────────────────┘
                          ↓
                    Printed Output
```

## 1. Print Engine

核心指标：

| Metric | Why it matters |
|---|---|
| Nozzle count | Potential throughput |
| Native resolution | Spatial sampling capability |
| Drop volume | Ink deposition control |
| Jetting frequency | Throughput |
| Variable drop | Tone / coverage control |
| Nozzle reliability | Production stability |
| Head lifetime | Maintenance cost |

分析时必须区分厂商标称 DPI、实际 pass、墨滴体积和最终图像质量。

## 2. Ink System

重点分析：

- Ink tank architecture
- Positive / negative pressure
- Filtration
- Degassing
- White ink circulation
- Ink temperature control
- Purging / capping
- Waste ink handling

白墨通常是维护复杂度和长期可靠性的重点，应单独分析沉降、循环、过滤、喷头堵塞和 purge 机制。

## 3. UV Curing

```text
UV LED
  ↓
Optics / Reflector
  ↓
Ink Surface
  ↓
Photoinitiator activation
  ↓
Polymerization
  ↓
Solidified ink film
```

关键参数：

- Wavelength
- Irradiance
- Exposure time
- Energy dose
- Cooling
- LED lifetime
- Curing position relative to printhead

需要区分 pinning 与 full cure，以及 UV dose 对附着力、表面效果、层间结合和黄变等因素的影响。

## 4. Motion System

重点研究：

- X/Y/Z architecture
- Linear guide / belt / screw
- Servo / stepper motor
- Encoder
- Printhead-to-media distance
- Motion accuracy / repeatability
- Synchronization between motion and jetting

打印头喷墨和运动必须进行严格时序同步；单独比较运动速度不能代表实际打印 throughput。

## 5. RIP & Color Pipeline

```text
Artwork
  ↓
RIP
  ↓
Color Management / ICC
  ↓
Screening / Halftone
  ↓
Channel Separation
  ↓
White / Color / Varnish Layers
  ↓
Jetting waveform / raster data
  ↓
Printhead
```

重点研究：

- ICC profile
- Gamut
- Screening algorithm
- Channel ordering
- White underbase
- Varnish / texture layers
- Multi-pass strategy
- Bidirectional compensation
- Nozzle compensation

## 6. Material Interaction

打印质量不是纯粹由打印机决定，还取决于：

- Surface energy
- Roughness
- Absorption
- Coating
- Adhesion
- Material temperature
- Ink chemistry
- UV dose

典型基材包括 acrylic、glass、metal、wood、plastic、leather-like materials、coated products 等。研究报告必须说明材料条件。

## 7. Reliability

重点失效模式：

| Failure mode | Possible cause |
|---|---|
| Nozzle clogging | Ink drying / contamination |
| White ink sedimentation | Insufficient circulation |
| Banding | Nozzle loss / motion / pass strategy |
| Poor adhesion | Material / ink / UV mismatch |
| Over-cure | Excessive UV dose |
| Under-cure | Insufficient UV dose |
| Color drift | Ink / temperature / calibration |
| Head strike | Incorrect head height / media flatness |

## 8. Benchmarking Rules

跨品牌比较时至少记录：

- Print area
- Ink channels
- Printhead model if public
- Drop volume if public
- Resolution
- Pass count
- Print speed condition
- Ink type
- UV wavelength
- UV curing configuration
- Substrate
- RIP/software
- Price

禁止只使用厂商最大 DPI 或最高速度作为性能结论。

## 9. Engineering Questions

每次 UV Printer 技术研究至少回答：

1. 打印头是什么架构？
2. 墨滴如何形成和控制？
3. 白墨如何避免沉降？
4. UV 如何与喷墨时序同步？
5. 如何控制墨滴扩散？
6. 如何实现多 pass / 双向打印？
7. 如何进行 nozzle compensation？
8. 色彩管理链路在哪里？
9. 不同材料为什么需要不同参数？
10. 哪些模块决定 BOM、可靠性和维护成本？
