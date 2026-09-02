# <Domain Name> Domain Model

> 新领域模板。复制本目录后，先完成 `domain.md`，再逐步补全 `technology.md` 与 `knowledge/`。Domain Model 定义“研究什么”，Knowledge 定义“深入理解什么”。

## Metadata

- **domain_id**: `<kebab-case-id>`
- **name_zh**: `<中文名称>`
- **name_en**: `<English Name>`
- **category**: `<Consumer Hardware / Fabrication Tool / Home Robot / Outdoor Robot / Sensor / Other>`
- **scope**: `<研究边界>`

## 1. Domain Definition

### Definition
- 

### Included
- 

### Excluded
- 

## 2. Product Taxonomy

| Segment | Product Type | Typical Price | Primary User | Main Differentiator |
|---|---|---:|---|---|
| | | | | |

> 产品分类与技术分类分开。这里回答“市场上有什么产品”，不要把知识模块直接当作产品分类。

## 3. Users & Use Cases

| User | Need | Workflow | Purchase Driver | Pain Point |
|---|---|---|---|---|
| | | | | |

## 4. Domain Workflow

```text
Input
  ↓
Preparation
  ↓
Core Process
  ↓
Control / Sensing
  ↓
Output
  ↓
Inspection / Maintenance / Service
```

Replace the generic flow with the actual end-to-end domain workflow.

## 5. Key Technology / Subsystems

| Order | Subsystem | What It Does | Key Metrics | Knowledge Module |
|---|---|---|---|---|
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |
| 4 | | | | |
| 5 | | | | |
| 6 | | | | |

## 6. Domain-Specific Benchmarks

| Dimension | Core Metrics | Measurement / Comparison Notes |
|---|---|---|
| Performance | | |
| Quality | | |
| Reliability | | |
| Automation | | |
| Materials / Environment | | |
| UX | | |
| Economics | | |

> 明确区分厂商宣传指标与可比、可复现的实际性能。必要时定义测试条件、工作负载与口径。

## 7. Technology Questions

### Core Technology
- 

### Hardware
- 

### Sensors & Control
- 

### Algorithms / Software
- 

### Materials / Environment
- 

### Manufacturing / Reliability
- 

## 8. Industry Media & Data Sources

1. Official manufacturer documentation
2. Regulatory / certification databases
3. Professional industry media
4. Engineering communities
5. Specialist reviews / teardowns
6. Supply-chain sources

> 搜索引擎结果和聚合站主要用于发现来源，不作为高置信度事实的最终证据。

## 9. Terminology

| English | 中文 | Definition | Notes |
|---|---|---|---|
| | | | |

## 10. Notation & Units

- Length: `<unit>`
- Mass: `<unit>`
- Speed: `<unit>`
- Power: `<unit>`
- Other domain-specific units: `<unit>`

## 11. Key Players

| Player | Chinese Name | Role | Main Products |
|---|---|---|---|
| | | | |

> 名单用于研究入口，不代表市场排名；市场份额与排名必须通过证据单独验证。

## 12. Common Technical Trade-offs

| Trade-off | Option A | Option B | Impact |
|---|---|---|---|
| | | | |

## 13. Research Boundaries

```text
Domain
  ↓
Core Technology
  ↓
Hardware / Materials / Environment
  ↓
Sensors / Control / Algorithms
  ↓
Firmware / Software / UX
  ↓
Output Performance / Reliability / Economics
```

明确哪些问题属于本 Domain，哪些应交由相邻 Domain 或通用 Framework 处理。

## 14. Knowledge Map

```text
Knowledge Map
│
├── Core Technology
├── Hardware
├── Sensors
├── Control
├── Algorithms
├── Firmware / Software
├── Materials / Environment
└── Reliability / Service
```

> Knowledge Map 是导航，不要求每个 Domain 都拥有完全相同的文件集合；只有当模块会实质影响产品性能或研究结论时才建立独立知识文件。

## 15. Progressive Knowledge Build-Up

```text
domain.md
   ↓
first research
   ↓
technology.md benchmarks
   ↓
knowledge modules
   ↓
repeated research / validation
   ↓
more complete domain model
```

Only promote information into long-term knowledge when it is reusable and sufficiently validated.