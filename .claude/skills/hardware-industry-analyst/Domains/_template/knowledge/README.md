# Knowledge Modules — 渐进补全指南

> ⚠️ Knowledge 模块是**可选的预加载缓存**，不是新领域的必须步骤。
>
> 它们的本质是把 AI 通过 WebSearch 获取并验证过的知识**沉淀下来**，让下次调研更快、更一致。没有它们，技能通过 WebSearch 即时搜索一样能工作。

---

## 渐进补全节奏

```
阶段 0: 空目录（首次调研）
  └── AI 通过 domain.md 的术语 + 媒体列表 + 子系统清单，
      用 WebSearch 搜索，产出第一份报告。
      报告质量足够，但没有缓存——每次关键词搜索都要等待。

阶段 1: 沉淀指标（第 1 次调研后）
  └── 把报告中用到的"段位均值""行业天花板"写入 technology.md。

阶段 2: 沉淀知识（第 2-3 次调研后）
  └── 把"技术路线对比""主流方案判断"写入 knowledge/*.md。
      每个文件 100-200 行足够。

阶段 3: 趋于完整（第 5+ 次调研后）
  └── knowledge 基本覆盖主要子系统，WebSearch 仅用于验证和更新。
      此时可与 fdm-3d-printer 和 robot-vacuum 的 knowledge 完整性对标。
```

---

## 文件命名

`<subsystem-name>.md` — 使用 kebab-case，如 `navigation.md`、`cleaning-systems.md`。

---

## 文件结构模板

```markdown
# <Subsystem Name> Knowledge Base

## Purpose
1-2 句说明本文档覆盖什么。

---

# <Technology Variant 1>

## Principle
工作原理（物理/工程层面）。

## Typical Specs
| Metric | Entry | Mid | High-End |
|---|---|---|---|
| | | | |

## Advantages
- Point 1
- Point 2

## Disadvantages
- Point 1
- Point 2

## Typical Implementations
- Manufacturer A: Model X
- Manufacturer B: Model Y

---

# <Technology Variant 2>
(same structure)

---

# Evaluation Matrix

| Variant | Performance | Reliability | Cost | Manufacturing Complexity | Best For |
|---|---|---|---|---|---|
| | | | | | |

---

# Industry Trends (Current Year − Current Year+2)

- Trend 1
- Trend 2
```

---

## 质量标准

- ❌ 避免营销语言（"革命性""行业首创"）
- ✅ 包含定量指标范围和容差
- ✅ 说明每种技术路线的 engineering tradeoffs
- ✅ 列出具体的厂商实现案例
- ✅ 给出来源引用的具体数据点
