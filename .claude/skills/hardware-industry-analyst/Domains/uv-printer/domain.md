# UV Printer Domain Model

## Metadata

- **domain_id**: `uv-printer`
- **name_zh**: UV 打印机
- **name_en**: UV Printer
- **category**: Digital Printing / Fabrication Tool
- **scope**: Desktop / Prosumer / Professional UV Printing

---

## 1. Domain Definition

### Definition

UV Printer 是通过喷墨方式将 UV 固化型墨水沉积到基材表面，并利用 UV 光源即时或分阶段固化形成图文、颜色、纹理或表面效果的数字印刷设备。

研究时应区分：

- **Printer Capability**：打印机硬件与控制系统能够稳定实现什么
- **Ink Capability**：墨水在特定打印头、材料和 UV 条件下能够实现什么
- **Substrate Capability**：不同基材表面的附着、润湿和固化能力
- **Software Capability**：RIP、色彩管理、栅格化和通道控制能够实现什么
- **System Capability**：硬件、墨水、基材、软件和操作流程共同形成的实际结果

### Included

- Desktop UV printers
- A3/A4/A2/A1 class UV flatbed printers
- Prosumer and professional UV flatbed systems
- UV roll-to-roll / hybrid systems when relevant
- UV DTF when the printing process is part of the research scope
- Printhead, ink system, UV curing, motion, RIP, color management, sensors, electronics and reliability

### Excluded

- Traditional solvent / eco-solvent printers
- Pure UV curing equipment without printing
- Conventional FDM / SLA / DLP 3D printers unless used as comparison
- General industrial inkjet market outside the UV printing use case

---

## 2. Product Taxonomy

### Product Segments

| Segment | Product Type | Typical Differentiator | Primary User |
|---|---|---|---|
| Desktop | A4/A3 UV flatbed | Size / price / ease of use | Maker / small business |
| Prosumer | A2/A1 flatbed | Throughput / color / material range | Studio / print shop |
| Professional | Large-format UV | Productivity / reliability | Commercial printer |
| Hybrid | Flatbed + roll | Substrate flexibility | Sign / graphics business |
| UV DTF | Film transfer | Irregular surfaces / low setup | Customization business |

### Technology Axes

- Printhead architecture
- Ink channel configuration
- White / varnish / primer capability
- UV curing architecture
- Flatbed / roll-to-roll / hybrid media handling
- RIP / color-management stack
- Automation and inspection

> 产品分类回答“市场上有哪些产品”；Printhead、Ink、UV、Motion、RIP 等属于技术分类，不应与产品层级混为一谈。

---

## 3. Users & Use Cases

| User | Need | Workflow | Purchase Driver | Pain Point |
|---|---|---|---|---|
| Maker | Small custom objects | Design → print → cure | Ease of use | Calibration / maintenance |
| Small Business | On-demand customization | Artwork → RIP → print | Cost / throughput | Ink cost / downtime |
| Print Shop | Continuous production | RIP → print → inspection | Productivity / uptime | Nozzle / ink / service |
| Brand / Studio | Premium graphics | Color management → print | Color / texture / consistency | Repeatability |
| Sign / Graphics Business | Flexible substrates | Artwork → media setup → print | Work area / throughput | Media compatibility |

---

## 4. Domain Workflow

```text
Artwork / CAD
      ↓
Color Management / RIP
      ↓
Rasterization / Screening
      ↓
Printhead Jetting
      ↓
Ink Droplet Deposition
      ↓
Pinning / UV Exposure
      ↓
Full Curing
      ↓
Finished Surface
      ↓
Inspection / Maintenance / Recalibration
```

### Causal Chain

```text
Artwork
  ↓
RIP / Color Separation
  ↓
Jetting Parameters
  ↓
Droplet Formation
  ↓
Ink Wetting / Spreading
  ↓
UV Dose / Curing
  ↓
Surface / Adhesion / Color
  ↓
Final Print Quality
```

该流程用于定位研究问题：任何产品能力都应尽量落到具体流程节点、硬件、控制、算法、软件、墨水或基材机制上。

---

## 5. Key Technology / Subsystems

| Order | Subsystem | What It Does | Key Metrics | Knowledge Module |
|---|---|---|---|---|
| 1 | Printhead | Generates ink droplets | nozzle count, drop size, frequency, grayscale | `printhead.md` |
| 2 | Ink System | Stores, filters and supplies ink | pressure, filtration, circulation, degassing | `ink-system.md`, `uv-ink.md` |
| 3 | UV Curing | Polymerizes UV ink | wavelength, irradiance, dose, curing speed | `uv-curing.md` |
| 4 | Motion System | Positions printhead / substrate | accuracy, repeatability, speed, synchronization | `motion-system.md` |
| 5 | Media / Vacuum Platform | Holds substrate flat | flatness, vacuum, work area, height control | `substrate-materials.md` |
| 6 | RIP / Color Management | Converts artwork to jetting data | ICC, screening, channel control | `color-management.md`, `software.md` |
| 7 | Control Electronics | Drives printhead, motion and UV | timing, synchronization, interfaces | `electronics.md`, `control-system.md` |
| 8 | Sensors | Monitor position, ink, temperature and safety | resolution, repeatability, sampling | `sensors.md` |
| 9 | Algorithms | Optimize jetting, compensation and image quality | nozzle compensation, screening, calibration | `algorithms.md` |
| 10 | Reliability / Service | Maintains stable production | nozzle health, cleaning, recovery, uptime | `reliability.md` |

---

## 6. Domain-Specific Benchmarks

| Dimension | Core Metrics | Measurement / Comparison Notes |
|---|---|---|
| Image Quality | apparent resolution, fine detail, edge quality, banding, dot placement | DPI alone does not equal optical image resolution |
| Color | gamut, ΔE, density, repeatability, white opacity | Must specify ink, substrate, profile and measurement method |
| Productivity | usable speed, pass count, throughput, uptime | Vendor speed ≠ production throughput |
| Printhead | drop size, firing frequency, nozzle count, grayscale capability | Compare actual operating conditions |
| UV Curing | wavelength, irradiance, dose, curing speed | Wavelength alone does not prove curing performance |
| Ink | viscosity, surface tension, adhesion, curing response | Ink compatibility ≠ validated substrate capability |
| White Ink | opacity, circulation, settling, reliability | White channel presence ≠ reliable white printing |
| Material | substrate range, adhesion, scratch resistance, surface compatibility | Test substrate and pretreatment must be specified |
| Automation | nozzle detection, compensation, height sensing, collision protection | Sensor presence ≠ closed-loop control |
| UX | setup time, RIP workflow, maintenance, calibration | Evaluate complete workflow, not UI alone |
| Reliability | nozzle health, cleaning interval, recovery, serviceability | Long-term operation is more valuable than demo output |
| Economics | ASP, ink cost, waste, service cost, consumables | BOM / cost estimates must show evidence grade |

### Benchmark Rules

- **DPI ≠ actual optical image resolution**
- **Print speed ≠ production throughput**
- **UV wavelength ≠ curing performance**
- **Ink compatibility ≠ validated substrate capability**
- **White ink channel ≠ reliable white printing**
- **ICC profile ≠ guaranteed color accuracy**
- **High drop frequency ≠ high usable productivity**

Cross-product comparison should, where possible, standardize substrate, ink, print mode, pass count, resolution, curing condition, artwork and measurement method.

---

## 7. Technology Questions

### Printhead / Jetting

- Piezo inkjet or another jetting architecture? Why?
- Which printhead family and what replacement strategy?
- Fixed or variable drop / grayscale jetting?
- What are the actual operating frequency and drop-volume ranges?
- How are nozzle defects detected and compensated?

### Ink / Fluidics

- What viscosity and surface-tension window is required?
- How is pressure regulated?
- Is white ink continuously circulated, periodically agitated or purged?
- How are filtration, bubbles and contamination managed?
- What ink/substrate combinations are actually validated?

### UV Curing

- What wavelength range and UV source architecture are used?
- Is the system pinning, full curing, or staged curing?
- How do irradiance, dose and carriage speed interact?
- How does curing affect adhesion, gloss, brittleness and surface appearance?

### Motion / Media

- How is printhead motion synchronized with firing?
- What is the actual positioning repeatability?
- How is substrate flatness maintained?
- Is vacuum used? How is media height detected?
- What happens when substrate thickness varies?

### RIP / Color / Algorithms

- Which RIP and color-management pipeline is used?
- How are ICC profiles created and applied?
- How are screening, pass count, dot placement and channel density controlled?
- Are nozzle maps, color calibration or media profiles stored per machine/material?
- Is a claimed AI feature monitoring, classification, prediction or actual control?

### Reliability / Manufacturing

- What are the dominant nozzle, ink and UV failure modes?
- How frequently is cleaning required?
- What components are field-replaceable?
- How much calibration is performed during manufacturing vs by the user?
- Which subsystems dominate BOM cost and service cost?

---

## 8. Industry Media & Data Sources

1. Manufacturer product pages, technical specifications and manuals
2. Printhead manufacturer documentation
3. Ink manufacturer technical data sheets and SDS/TDS where relevant
4. RIP / color-management software documentation
5. UV LED / curing component manufacturer documentation
6. Professional printing industry media and trade publications
7. Professional reviews, long-term tests and teardowns
8. Engineering forums and service communities
9. Distributor / service documentation
10. Supply-chain and OEM information

> Search-engine results are discovery tools, not high-confidence final evidence.

---

## 9. Terminology

| English | 中文 | Definition | Research Notes |
|---|---|---|---|
| UV Ink | UV 墨水 | UV 固化型喷墨墨水 | Must distinguish formulation and substrate compatibility |
| Printhead | 打印头 | 喷射墨滴的核心器件 | Manufacturer/model matters |
| Drop Size | 墨滴大小 | 单个墨滴体积 | Usually pL; may be variable |
| Grayscale | 灰度喷墨 | 通过改变墨滴体积实现不同覆盖量 | Not the same as image grayscale |
| White Ink | 白墨 | 用于底色、遮盖或多层打印 | Settling is a key reliability issue |
| Varnish | 光油 | 用于表面光泽、纹理和局部效果 | Often an additional channel |
| UV Curing | UV 固化 | 通过紫外光引发墨水聚合固化 | Dose and spectrum matter |
| Pinning | 预固化 | 使墨滴先部分固定，控制扩散 | Can affect gloss and adhesion |
| RIP | 光栅图像处理 | 将设计文件转换为打印数据 | Includes screening/channel management |
| ICC Profile | ICC 色彩配置文件 | 描述设备色彩特性的配置文件 | Profile ≠ independent color accuracy proof |
| Pass | 打印遍数 | 打印头相对介质完成一次覆盖 | Strongly affects speed and quality |
| Irradiance | 辐照度 | 单位面积接收的光功率 | `mW/cm²` |
| UV Dose | UV 剂量 | 单位面积累计 UV 能量 | `mJ/cm²` |

---

## 10. Notation & Units

- Length / work area: `mm`, `mm²`
- Print speed / carriage speed: `mm/s`, `m/min`
- Throughput: `m²/h`, `units/h`
- Resolution: `dpi`
- Drop volume: `pL`
- Ink viscosity: `mPa·s` / `cP`
- Surface tension: `mN/m`
- UV wavelength: `nm`
- UV irradiance: `mW/cm²`
- UV dose: `mJ/cm²`
- Temperature: `°C`
- Color difference: `ΔE`
- Ink consumption: `mL/m²` or `mL/job`

### Unit Rules

- Do not compare DPI without checking whether it is addressable, native, interpolated or marketing resolution.
- Do not compare throughput without print mode, pass count and substrate assumptions.
- Do not infer curing quality from wavelength alone.
- Do not infer color accuracy from ICC profile existence alone.

---

## 11. Key Players

| Player | Representative Role |
|---|---|
| Roland DG | Professional UV printing systems |
| Mimaki | Professional / industrial UV printing |
| Mutoh | Large-format UV printing |
| Epson | Industrial inkjet and professional printing technologies |
| Canon | Professional / industrial digital printing |
| Ricoh | Industrial printheads and printing systems |
| Fujifilm | Industrial inkjet / UV printing |
| xTool | Desktop / maker-oriented printing ecosystem |
| Procolored | Desktop UV printing |
| Anycubic | Consumer / maker digital fabrication ecosystem |

> Key-player lists are starting points for research, not evidence of equivalent product positioning.

---

## 12. Common Technical Trade-offs

| Trade-off | Option A | Option B | Impact |
|---|---|---|---|
| Speed vs quality | Fewer passes | More passes | Throughput vs detail / banding |
| UV dose vs surface appearance | Strong cure | Lower / staged cure | Cure completeness vs gloss / adhesion |
| White ink | Continuous circulation | Agitation / periodic purge | Reliability vs complexity / waste |
| Drop size | Fixed | Variable / grayscale | Simplicity vs image quality |
| Printhead | Lower cost | Higher performance | BOM vs productivity |
| Work area | Larger | Smaller | Capability vs machine size |
| Ink viscosity | Higher | Lower | Material window vs jetting stability |
| Vacuum | Stronger | Weaker / none | Media flatness vs energy / complexity |
| Pinning | Earlier / stronger | Later / weaker | Dot gain vs adhesion / gloss |
| Color channels | CMYK | CMYK + W + varnish / spot | Gamut / effects vs cost / maintenance |

---

## 13. Research Boundaries

UV Printer research should distinguish at least five layers:

```text
Printer Hardware
      ↓
Printhead / Ink / UV Curing
      ↓
RIP / Color Management / Algorithms
      ↓
Substrate / Surface Interaction
      ↓
Final Print Quality / Production Outcome
```

### Capability Boundary

```text
Machine Capability
      ↓
Ink / Printhead Capability
      ↓
Process Capability
      ↓
Substrate Capability
      ↓
Print Quality
      ↓
Production / Business Outcome
```

### Out-of-scope Warning

Do not silently expand a UV printer report into a generic digital-printing market report unless the research objective explicitly requires it.

---

## 14. Knowledge Map

```text
UV Printer Domain
├── Printing Principle
├── Printhead
├── Ink System
│   └── UV Ink
├── UV Curing
├── Motion System
├── Substrate / Materials
├── Sensors
├── Electronics
├── Control System
├── Algorithms
├── RIP / Color Management
├── Software
└── Reliability
```

### Causal Knowledge Chain

```text
Substrate
  ↕
Ink Properties
  ↓
Printhead Jetting
  ↓
Droplet Formation
  ↓
Ink Spreading / Wetting
  ↓
Pinning / UV Curing
  ↓
Surface Properties
  ↓
Color / Detail / Adhesion / Durability
```

Research should follow causal relationships rather than simply collecting specification fields.

---

## 15. Progressive Knowledge Build-Up

### Level 1 — Domain Basics

Understand UV inkjet workflow, product categories, terminology and major players.

### Level 2 — System Architecture

Understand printhead, ink path, UV curing, motion, substrate platform, electronics and RIP architecture.

### Level 3 — Performance Mechanisms

Understand drop formation, wetting, curing dose, pass count, screening, color management and material interaction.

### Level 4 — Engineering Evaluation

Evaluate print quality, productivity, reliability, calibration, maintenance, BOM and manufacturing trade-offs.

### Level 5 — Competitive / Strategic Analysis

Compare product architectures, technology differentiation, ecosystem lock-in, supply-chain choices, cost structure and roadmap.
