# Technology Analysis Model

## Objective
解释“技术为什么重要”，而不是罗列技术名称。

## Technology Cluster
优先把相关技术组合为系统能力：

```text
Problem
 ↓
Technology Cluster
 ├─ Architecture
 ├─ Mechanism
 ├─ Sensors
 ├─ Actuators
 ├─ Software / Algorithms
 └─ Control
 ↓
System Capability
 ↓
Product Effect
 ↓
User / Economic Value
 ↓
Competitive Advantage
 ↓
Strategic Value
```

## Required Deep-Dive Questions
1. 解决什么问题？
2. 为什么传统方案不够？
3. 系统架构是什么？
4. 关键硬件、传感器、执行器是什么？
5. 算法 / firmware 做什么？
6. 是否形成闭环？
7. 核心参数如何影响结果？
8. 新能力是什么？
9. 对用户工作流产生什么变化？
10. 带来什么成本、复杂度、可靠性代价？
11. 与竞品的本质差异是什么？
12. 为什么可能难以复制？
13. 下一代瓶颈是什么？

## Closed-loop Pattern
```text
Sensing
  ↓
State Estimation
  ↓
Decision / Control
  ↓
Actuation
  ↓
Physical Result
  ↓
Feedback
```

## Technology Evolution
```text
Old limitation
 ↓
Driver
 ↓
Technology change
 ↓
New capability
 ↓
User / product effect
 ↓
Next limitation
```

## Output Rule
深拆优先选择 2–4 个 Technology Clusters，而不是简单选择若干零部件。每个 Cluster 至少形成一张系统关系图或因果链，并包含 Trade-off 与 Competitive Difference。
