# Knowledge Modules — 渐进补全指南

> Knowledge 模块是**可选的预加载缓存**，不是新领域的必须步骤。它们的本质是把 AI 通过 WebSearch 获取并验证过的知识沉淀下来，让下次调研更快、更一致。没有它们，技能通过 WebSearch 即时搜索一样能工作。

---

## 渐进补全节奏

```text
阶段 0: 空目录（首次调研）
  └── AI 通过 domain.md 的术语 + 媒体列表 + 子系统清单，
      用 WebSearch 搜索，产出第一份报告。

阶段 1: 沉淀技术模型（第 1 次调研后）
  └── 把报告中验证过的关键技术路线、核心指标口径、性能因果关系
      写入 technology-model.md。

阶段 2: 沉淀知识（第 2-3 次调研后）
  └── 把可长期复用的技术原理、典型实现、参数范围、失效模式、
      trade-offs 和高质量来源写入 knowledge/*.md。
      文件长度按知识复杂度决定，不设机械行数要求。

阶段 3: 趋于完整（第 5+ 次调研后）
  └── knowledge 基本覆盖主要影响产品性能的子系统，WebSearch
      主要用于验证、更新和发现新技术。
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

- ❌ 避免营销语言（"革命性"、"行业首创"）
- ✅ 包含定量指标范围时必须注明口径、测试条件或来源
- ✅ 说明每种技术路线的 engineering tradeoffs
- ✅ 列出具体的厂商实现案例（仅在有可靠来源时）
- ✅ 给出来源引用的具体数据点，并区分事实、报告、推断和估算
- ❌ 不把一次性价格、促销、未经验证的论坛猜测直接写入长期知识库
