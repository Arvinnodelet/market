# <Domain Name> Technology Model

> 本文件定义该领域的**技术模型**，而不是通用评估方法。通用评估方法由 `Frameworks/technology.md` 提供。
>
> 作用：定义该领域的系统架构、技术层级、关键性能因果关系、主流实现模式、工程权衡和研究问题，并将这些技术节点映射到 `knowledge/`。
>
> **何时创建**：当某个 Domain 已经有稳定的技术结构，或首次研究需要系统拆解技术架构时创建。
>
> **最小可用**：可以只有系统架构 + Technology Layers + Knowledge Mapping；缺少具体知识时通过研究补充，不要求一次性填满。

---

## 1. System Architecture

```text
Input / User
      ↓
Software / Data
      ↓
Controller / Control
      ↓
Core Technology / Actuation
      ↓
Physical Process
      ↓
Output
      ↑
Sensors / Feedback
```

说明该领域的主要数据流、控制流和物理过程。

## 2. Technology Layers

| Layer | Domain Module | Core Question | Knowledge Module |
|---|---|---|---|
| Core Technology | | | |
| Hardware / Subsystems | | | |
| Sensors | | | |
| Electronics | | | |
| Control | | | |
| Algorithms | | | |
| Software | | | |
| Materials / Consumables | | | |
| Manufacturing / Service | | | |
| Reliability | | | |

> Technology Model 回答“技术如何组织和产生能力”；具体技术定义、参数和失效模式进入 `knowledge/`。Manufacturing / Service 用于描述技术如何被装配、校准、维护和规模化实现，不等同于通用制造评估框架。

## 3. Performance Causal Model

```text
Technology / Input
        ↓
Physical / Computational Mechanism
        ↓
Controllable Parameters
        ↓
Measured Performance
        ↓
User / Production Outcome
```

定义该领域最重要的 1–3 条性能因果链。

## 4. Key Engineering Models

记录真正用于解释性能差异的公式、物理模型、控制关系或系统约束。

例如：

- throughput model
- thermal / fluidic model
- motion / dynamics model
- optical model
- energy / battery model
- sensing / control model

具体模型的背景知识应链接到对应 `knowledge/*.md`，避免在 Technology Model 中重复完整知识教材。

## 5. Subsystem Assessment Map

| Subsystem | Primary Metrics | Secondary Questions | Knowledge |
|---|---|---|---|
| | | | |
| | | | |
| | | | |

这里定义**评估对象与指标入口**；具体评分方法由 `Frameworks/technology.md` 负责。

## 6. System Architecture Patterns

记录该领域的主流技术架构及其核心差异。

| Architecture | Key Components | Main Advantage | Main Cost / Risk | Typical Use |
|---|---|---|---|---|
| | | | | |
| | | | | |

## 7. Automation / Feedback Stack

```text
Sensor
  ↓
Measurement
  ↓
State Estimation / Detection
  ↓
Algorithm / Model
  ↓
Parameter / Command
  ↓
Control System
  ↓
Machine Response
```

明确哪些功能只是 monitoring，哪些属于 calibration，哪些真正形成 closed-loop control。

## 8. Technical Trade-offs

记录该领域最重要的工程权衡，而不是重复通用评价框架。

1. **Tradeoff A vs B** → engineering rationale and impact
2. **Tradeoff C vs D** → engineering rationale and impact
3. **Tradeoff E vs F** → engineering rationale and impact

## 9. Technology Research Questions

每次该领域技术研究至少回答：

1. 核心物理 / 计算机制是什么？
2. 哪些子系统决定主要性能瓶颈？
3. 各子系统如何协同？
4. 哪些参数是真正决定性能的控制变量？
5. 哪些能力来自硬件，哪些来自软件 / 算法？
6. 哪些能力形成闭环反馈？
7. 主要工程 trade-offs 是什么？
8. 哪些技术差异能够形成可靠的产品竞争差异？

## 10. Knowledge Mapping

```text
Technology Model
      │
      ├── Core Technology → knowledge/core-technology.md
      ├── Hardware → knowledge/hardware.md
      ├── Sensors → knowledge/sensors.md
      ├── Control → knowledge/control-system.md
      ├── Algorithms → knowledge/algorithms.md
      ├── Software → knowledge/software.md
      ├── Manufacturing / Service → knowledge/manufacturing.md
      └── Reliability → knowledge/reliability.md
```

只列实际存在或计划长期维护的知识模块；不要为了结构完整而创建空文件。
