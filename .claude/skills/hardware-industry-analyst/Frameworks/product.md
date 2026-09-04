# Product Research & Analysis Framework v3

## Objective

研究单个硬件产品，不停留在“参数 + 功能”层面，而是回答：

1. 产品解决什么问题，服务谁，在产品组合中扮演什么角色？
2. 系统如何工作，哪些技术共同形成核心能力？
3. 核心能力如何转化为用户价值、经济性和制造能力？
4. 与竞品相比，差异来自哪里，是否可复制？
5. 当前能力边界和瓶颈是什么，下一步可能如何演进？

**核心原则：Specification ≠ Capability ≠ User Value ≠ Competitive Advantage。**

---

# 1. Product Definition & Positioning

建立事实表，并标记 Evidence / Confidence。

| Attribute | Data | Evidence | Confidence |
|---|---|---|---|
| Manufacturer | | | |
| Product / Model | | | |
| Series / Tier | | | |
| MSRP / Street Price | | | |
| Release Date | | | |
| Status | | | |
| Target User | | | |
| Primary Use Cases | | | |
| Predecessor / Successor | | | |

### 必须回答

- 产品解决的核心问题是什么？
- 为什么公司在这个时间推出它？
- 与同品牌其他产品的边界是什么？
- 定位由价格、性能、体验、生态还是材料/工艺能力决定？

---

# 2. Portfolio Role

| Dimension | Analysis |
|---|---|
| Product Line | |
| Price Position | |
| Performance Position | |
| Technology Role | |
| Shared Platform | |
| Shared Components | |
| Ecosystem Role | |
| Upgrade Path | |
| Cannibalization Risk | |

必须判断该产品是：**旗舰技术展示 / 平台产品 / 规模产品 / 入门获客 / 特定场景产品 / 成本优化产品**，或组合角色。

---

# 3. User Problem & Workflow

```text
User Problem
    ↓
Current Workflow / Pain Point
    ↓
Product Intervention
    ↓
New Capability
    ↓
Workflow Improvement
    ↓
Economic / Experience Value
```

| User | Problem | Workflow | Product Capability | Value | Evidence |
|---|---|---|---|---|---|
| | | | | | |

不要只写“适合创客/工程师”，必须解释用户为什么需要该能力。

---

# 4. Core Specifications

公开参数、实测参数和推导参数分开。

| Category | Parameter | Value | Source | Status |
|---|---|---|---|---|
| Physical | | | | Confirmed / Reported / Inferred / Estimated |
| Performance | | | | |
| Electrical | | | | |
| Connectivity | | | | |
| Environmental | | | | |
| Materials | | | | |
| Software | | | | |

缺失参数写 `Unknown / 未公开`，禁止为了完整性猜测。

---

# 5. System Architecture

先建立系统模型，再写章节。

```text
User / Input
     ↓
Software / Workflow
     ↓
Planning / Algorithms
     ↓
Control
     ↓
┌──────────┬──────────┬──────────┐
│ Sensing  │Actuation │Processing│
└────┬─────┴────┬─────┴────┬─────┘
     └──────────┼──────────┘
                ↓
          Physical Process
                ↓
             Output
                ↓
             Feedback
```

针对具体 Domain 替换模块，并解释：
- 数据流
- 能量流
- 控制流
- 关键接口
- 闭环位置

---

# 6. Product Capability Map

这是 v3 的核心章节。必须把组件和参数上升为系统能力。

| Technology / Subsystem | Mechanism | System Capability | Product Effect | User Value |
|---|---|---|---|---|
| | | | | |

推荐使用：

```text
Component
  ↓
Subsystem
  ↓
Technology Cluster
  ↓
System Capability
  ↓
Workflow Capability
  ↓
Product Positioning
```

禁止把单个传感器、芯片、算法直接称为“核心能力”，除非它在系统层形成可验证能力。

---

# 7. Core Technology System

不要按零件目录平铺。优先选择 **2–4 个 Technology Clusters**。

每个 Cluster 必须回答：

1. Problem
2. Legacy Limitation
3. Architecture
4. Mechanism
5. Hardware / Sensors / Actuators
6. Software / Algorithms
7. Closed Loop
8. Key Parameters
9. Capability Created
10. Product / User Effect
11. Reliability / Failure Modes
12. Trade-offs
13. Competitor Difference
14. Copyability / Defensibility
15. Next Constraint
16. Strategic Significance

推荐结构：

```text
Problem
  ↓
Technology Cluster
  ↓
Mechanism / Implementation
  ↓
Closed Loop
  ↓
Capability
  ↓
Product Effect
  ↓
User / Economic Value
  ↓
Competitive Difference
  ↓
Strategic Significance
```

### Core Technology Selection Criteria

优先选择满足多个条件的技术：
- 解决重大产品痛点
- 显著改变性能、质量、可靠性、成本或体验
- 跨多个子系统协同
- 形成可复用平台能力
- 明显影响竞品差异
- 存在较高复制门槛
- 决定未来产品演进空间

---

# 8. Software / Algorithms

| Layer | Implementation | What It Senses / Computes | Capability | Hardware Effect | Evidence |
|---|---|---|---|---|---|
| Firmware | | | | | |
| Control | | | | | |
| Algorithm | | | | | |
| App | | | | | |
| Cloud | | | | | |

重点判断软件是否真正改变硬件能力：

```text
Sensor → Estimation → Algorithm → Control → Actuator → Physical Result
```

若视觉/AI只做告警，不应描述为自动控制；若算法没有改变执行参数，也不能直接称为闭环。

---

# 9. Materials / Consumables / Process

适用时分析：

| Material | Machine Requirement | Validated Workflow | Performance | Cost | Lock-in | Evidence |
|---|---|---|---|---|---|---|

必须区分：**Supported ≠ Validated ≠ Optimized。**

---

# 10. UX & Workflow

| Dimension | Evidence | Mechanism | User Effect | Assessment |
|---|---|---|---|---|
| Setup | | | | |
| Calibration | | | | |
| First Use | | | | |
| Operation | | | | |
| Error Recovery | | | | |
| Maintenance | | | | |
| Software | | | | |
| Support | | | | |

重点分析自动化如何减少用户工作量，而非简单罗列 App 功能。

---

# 11. Reliability & Service

| Failure / Risk | Physical Mechanism | Detection | Mitigation | User Impact | Evidence / Confidence |
|---|---|---|---|---|---|
| | | | | | |

分析：wear parts、热/机械/电应力、校准漂移、维护周期、故障恢复、维修性、备件、环境敏感性。

---

# 12. Manufacturing & Economics

### Manufacturing

| Dimension | Analysis | Confidence |
|---|---|---|
| BOM Structure | | |
| Major Cost Drivers | | |
| Assembly Complexity | | |
| Wiring / Harness | | |
| Calibration | | |
| DFM / DFA | | |
| Automation Potential | | |
| Serviceability | | |
| Supply Chain Risk | | |

### Economics

| Item | Value / Estimate | Basis | Confidence |
|---|---|---|---|
| MSRP | | | |
| Street Price | | | |
| Estimated BOM | | | |
| Consumable Cost | | | |
| Service Cost | | | |
| Labor Intervention | | | |
| Cost per Workflow / Part | | | |

所有 BOM / 毛利 / 成本模型必须明确 `Estimated` 及假设。

---

# 13. Competitive Benchmark

选择 2–4 个真正直接竞品。

| Dimension | Product | Competitor A | Competitor B | Underlying Difference | Capability Effect |
|---|---|---|---|---|---|
| Architecture | | | | | |
| Motion / Process | | | | | |
| Sensing | | | | | |
| Control | | | | | |
| Materials | | | | | |
| Software | | | | | |
| Ecosystem | | | | | |
| Reliability | | | | | |
| Economics | | | | | |

### 必须回答

- 差异是什么？
- 为什么不同？
- 是否解决同一个问题？
- 能力差异是什么？
- Trade-off 是什么？
- 为什么不能简单复制？
- 对目标用户是否真的重要？

---

# 14. Product / Technology Evolution

不要只做发布时间线。

```text
Previous Limitation
      ↓
Evolution Driver
      ↓
Technology Change
      ↓
New Capability
      ↓
Product Effect
      ↓
Next Constraint
```

| Generation | Limitation | Technology Change | New Capability | Strategic Meaning | Next Constraint |
|---|---|---|---|---|---|
| | | | | | |

判断变化属于：incremental upgrade / architecture change / platform change / ecosystem expansion / cost-down。

---

# 15. Strategic Assessment

使用：

```text
Technology Capability
      ↓
Product Capability
      ↓
Portfolio Role
      ↓
Market Position
      ↓
Economic Effect
      ↓
Competitive Advantage
      ↓
Defensibility
      ↓
Strategic Option
```

必须回答：
- 建立了什么平台能力？
- 是否可跨产品复用？
- 是否改善成本、速度、质量、可靠性或 UX？
- 是否强化生态或渠道？
- 是否扩大未来产品可行空间？
- 优势属于结构性、执行性、暂时性还是易复制？

---

# 16. Future Outlook

未来不是趋势堆砌，必须由当前瓶颈推导：

```text
Current Capability
      ↓
Remaining Bottleneck
      ↓
Why It Matters
      ↓
Technology Enabler
      ↓
Company Existing Capability
      ↓
Competitive / Economic Pressure
      ↓
Likely Evolution
      ↓
Strategic Consequence
```

每项预测标记：`Fact / Trend / Inference / Scenario / Estimate`。

建议按 Near / Mid / Long term 输出，但不得把推断路线写成公司已确认 roadmap。

---

# 17. Overall Assessment

最终结论必须形成闭环：

```text
What the company built
→ Why it works
→ What capability it creates
→ Why users care
→ Why competitors care
→ Why it is hard to copy
→ What constraint comes next
→ Where the product is likely to evolve
```

避免重复前文的参数和功能列表。

---

# 18. Evidence & Confidence

| Status | Definition |
|---|---|
| Fact | 来源明确陈述 |
| Verified | 多个可靠来源交叉确认 |
| Reported | 可靠第三方报告 |
| Inferred | 工程推理 / 结构证据 |
| Estimated | 计算或 benchmark 推算 |
| Assessment | 分析者判断 |
| Unknown | 证据不足 |

重要结论必须能够回溯到证据或明确的推理链。

---

# 19. Sources

优先：官方产品页、手册、技术文档、软件仓库、release notes、专利、认证、投资者资料；其次是专业评测、拆解、长期测试和工程社区。

```markdown
## Sources
- [Source description](URL)
```
