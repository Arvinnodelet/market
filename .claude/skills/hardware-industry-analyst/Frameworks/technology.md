# Technology Analysis Framework v3

## Objective

本框架定义如何把硬件技术研究从“器件 / 参数 / 功能列表”升级为**系统能力、竞争差异和技术演进分析**。

> `Domains/<domain>/technology-model.md` 定义研究什么；本文件定义如何分析。

核心链：

```text
Evidence
 ↓
Problem / Limitation
 ↓
Technology Cluster
 ↓
Mechanism
 ↓
Implementation
 ↓
Closed Loop
 ↓
System Capability
 ↓
Product / User Value
 ↓
Trade-off
 ↓
Competitive Difference
 ↓
Defensibility
 ↓
Strategic Significance
 ↓
Next Constraint / Evolution
```

---

# 1. Technology Cluster

Technology Cluster 是 v3 默认分析单元。

不要把“一个传感器 / 一颗芯片 / 一个算法 / 一个营销功能”自动定义为核心技术。

一个 Cluster 通常由以下部分组成：

```text
Problem
 └─ Architecture
     ├─ Hardware
     ├─ Sensors
     ├─ Actuators
     ├─ Processing
     ├─ Software / Algorithms
     └─ Control
          ↓
     System Capability
```

### Cluster 选择标准

优先选择能够：
- 解决重大产品瓶颈；
- 整合多个子系统；
- 显著改善性能 / 质量 / 成本 / 可靠性 / UX；
- 跨产品复用；
- 形成明显竞品差异；
- 提高复制门槛；
- 决定下一代产品方向。

旗舰产品通常选择 **2–4 个 Cluster** 深挖，而不是罗列十几个“核心技术”。

---

# 2. Technology Deep Dive

每个核心 Cluster 尽量回答：

1. Problem
2. Legacy Limitation
3. Why Existing Solution Is Insufficient
4. Architecture
5. Mechanism
6. Hardware / Sensors / Actuators
7. Software / Algorithms
8. Closed Loop
9. Key Parameters
10. System Capability
11. Product / User Effect
12. Reliability / Failure Modes
13. Manufacturing / Cost Effect
14. Trade-offs
15. Competitor Difference
16. Copyability / Defensibility
17. Next Constraint
18. Strategic Significance

---

# 3. Mechanism Analysis

不能从“用了 X 技术”直接跳到“性能更好”。

推荐：

```text
Technology
 ↓
Physical / Mathematical Mechanism
 ↓
What Variable Changes?
 ↓
Subsystem Effect
 ↓
System Effect
 ↓
Capability
```

例如：

```text
Higher acceleration
 ↓
Motion dynamics / resonance excitation increases
 ↓
Input shaping + mechanical rigidity + control compensation
 ↓
Reduced vibration artifacts
 ↓
Higher usable speed
 ↓
Higher throughput
```

如果中间机制缺乏证据，应标记 `Inference`，不要写成事实。

---

# 4. Closed-Loop Analysis

存在反馈控制时，必须尽量还原：

```text
Physical State
 ↓
Sensor
 ↓
Sampling / Signal Processing
 ↓
State Estimation
 ↓
Decision / Control Law
 ↓
Actuator
 ↓
Physical Response
 ↺
```

至少说明：
- 测量对象是什么；
- 传感器在哪里；
- 测量频率 / 精度 / 重复性（有证据时）；
- 如何估计状态；
- 什么参数被调整；
- 哪个执行器被驱动；
- 延迟和稳定性约束；
- 失败模式；
- 最终形成什么能力。

**Sensor presence ≠ monitoring ≠ calibration ≠ closed-loop control。**

---

# 5. Capability Analysis

区分：

```text
Component
 ↓
Subsystem
 ↓
System Capability
 ↓
Workflow Capability
 ↓
User Value
```

例如：

```text
Camera
 + NPU
 + Detection Algorithm
 + Firmware
 ↓
Failure Detection Capability
 ↓
Reduced unattended-print risk
 ↓
Higher workflow reliability
```

只有整合后形成可验证能力，才可称为系统技术优势。

---

# 6. Parameter Interpretation

不要直接把厂商 headline parameter 当作能力。

分析：

```text
Headline Spec
 ↓
Operating Condition
 ↓
Physical Constraint
 ↓
System Integration
 ↓
Usable Capability
```

常见规则：
- 最大速度 ≠ 持续打印速度；
- 最大温度 ≠ 材料能力；
- 最大流量 ≠ 所有材料的稳定流量；
- 精度 ≠ 重复性；
- 传感器分辨率 ≠ 系统控制精度；
- 峰值功率 ≠ 持续功率；
- 实验室 benchmark ≠ 真实工作流 throughput。

---

# 7. Trade-off Analysis

**每个核心技术必须分析 Trade-off。**

```text
Technology Choice
 ↓
Benefit
 ↕
Cost / Complexity / Risk
 ↓
Why This Trade-off Is Rational?
 ↓
For Which Market / User?
```

至少回答：
- 它解决了什么？
- 什么指标变好？
- 什么指标变差？
- 增加了哪些 BOM / 装配 / 校准 / 软件复杂度？
- 引入什么新故障模式？
- 为什么公司仍选择它？

---

# 8. Architecture Coherence

评价技术不是简单把子系统分数相加。

分析：

| Dimension | Question |
|---|---|
| Integration | 多个功能是否由统一平台协同？ |
| Data Flow | 传感、算法、控制是否形成完整数据链？ |
| Mechanical-Electrical | 机械、电气、控制是否匹配？ |
| Software-Hardware | 软件是否真正释放硬件能力？ |
| Platform | 能否跨产品复用？ |
| Upgrade Headroom | 下一代是否可以继续扩展？ |

---

# 9. Defensibility

必须回答：**为什么竞争对手不能简单复制这个功能？**

```text
Visible Feature
 ↓
Underlying Capability
 ↓
Complementary Assets
 ↓
Integration / Data / Manufacturing / IP / Ecosystem
 ↓
Replication Difficulty
 ↓
Defensibility
```

防御力来源可以包括：
- proprietary hardware
- control algorithms
- sensor calibration
- manufacturing process
- firmware / software stack
- training data
- ecosystem
- supply chain
- accumulated field data
- patents / IP
- organization / engineering know-how

不要因为“自研”就自动判断为 moat。

---

# 10. Competitive Technology Analysis

优先比较**解决同一问题的不同技术路线**。

| Problem | Company A | Company B | Architectural Difference | Capability Effect | Trade-off |
|---|---|---|---|---|---|
| | | | | | |

必须判断：
- 是真正不同路线，还是不同实现？
- 哪一方的系统集成更深？
- 哪一方更便宜 / 更可靠 / 更容易制造？
- 差异是否被目标用户感知？
- 是否会随着器件商品化而消失？

---

# 11. Technology Evolution

不要只建立年份时间线。

使用：

```text
Old Limitation
 ↓
Evolution Driver
 ↓
Technology Change
 ↓
New Capability
 ↓
Product Effect
 ↓
New Bottleneck
```

| Generation | Old Limitation | Technology Change | Capability | New Constraint |
|---|---|---|---|---|
| | | | | |

判断演进属于：
- incremental improvement
- architecture transition
- platform transition
- vertical integration
- automation
- software-defined capability
- cost-down / manufacturing optimization

---

# 12. Technology Maturity

每项技术可从以下角度判断：

| Dimension | Question |
|---|---|
| Physical Maturity | 原理是否成熟？ |
| Component Maturity | 核心器件是否商品化？ |
| Integration Maturity | 系统是否成熟？ |
| Manufacturing Maturity | 是否规模化？ |
| Software Maturity | 算法 / firmware 是否稳定？ |
| Ecosystem Maturity | 是否有配套生态？ |
| Commoditization Risk | 是否容易成为行业标配？ |

---

# 13. Technology Assessment

最终输出不得只写“Leading / Competitive / Behind”。

推荐：

```text
Technology Position
 + Evidence
 + Mechanism
 + Capability
 + Trade-off
 + Competitor Comparison
 + Defensibility
 + Next Constraint
```

### Recommended conclusion

```markdown
**判断：** Leading / Competitive / Behind / Unclear

**依据：**
- ...

**真正优势：**
- ...

**主要代价：**
- ...

**竞争壁垒：**
- ...

**下一瓶颈：**
- ...
```

---

# 14. Output Rule

技术章节优先回答：

> **这项技术为什么出现？它到底改变了什么变量？如何形成系统能力？用户获得什么？竞争对手为什么难以复制？这个路线下一步会遇到什么瓶颈？**

而不是：

> “产品采用了 A、B、C、D 四项先进技术。”
