# <Domain Name> Domain Configuration

> 🆕 新领域模板 — 复制本目录，填写此文件即可激活新硬件品类的分析能力。
>
> **最小启动**：只需填写本文件（`domain.md`）。`technology.md` 和 `knowledge/*.md` 可选，渐进补全。

---

## Metadata

- **domain_id**: `<kebab-case-id>`
- **name_zh**: `<中文名称>`
- **name_en**: `<English Name>`
- **category**: `<Consumer Robot / Fabrication Tool / Home Service Robot / Outdoor Robot>`

---

## Triggers

> 这些触发词会添加到技能 SKILL.md 的 triggers 清单中。

```yaml
# 复制到 SKILL.md 的 triggers 字段
- <中文产品名>
- <English product name>
- <品牌名 1>
- <品牌名 2>
- <核心技术术语 1>
- <核心技术术语 2>
```

---

## Key Subsystems

> 定义该领域硬件的技术子系统。这决定了报告的技术维度框架。
>
> `Knowledge Module` 列为**可选**——有则预加载 curated 知识，无则 WebSearch 即时搜索。
> 建议：先列出子系统清单，knowledge 文件在首次调研时自动沉淀。

| Order | Subsystem | Knowledge Module | What It Covers |
|---|---|---|---|
| 1 | | *(可选) `knowledge/.md`* | |
| 2 | | *(可选) `knowledge/.md`* | |
| 3 | | *(可选) `knowledge/.md`* | |
| 4 | | *(可选) `knowledge/.md`* | |
| 5 | | *(可选) `knowledge/.md`* | |
| 6 | | *(可选) `knowledge/.md`* | |

---

## Industry Media & Data Sources

> 按优先级排列。AI 会优先从这些来源获取信息。

1. 公司官网 / Official Wiki
2. 行业媒体：
3. 社区论坛：
4. 供应链公开信息
5. 竞品对比评测

---

## Terminology

> 中英文术语映射表。保证报告用词一致、准确。

| English | 中文 | 说明 |
|---|---|---|
| | | |

---

## Notation

> 领域特定的符号和单位规范。

- **核心指标**: `<notation>`
- **End of Life**: `[EOL]` or `†`；新产品：`🆕`
- **Product names**: 使用官方型号
- **File names**: `公司名_Brand_报告类型_年份.md`
- **First mention**: `中文官方名（English Name）`；此后使用上下文合适的简称

---

## Key Players

> 该领域的主要厂商。初次调研时可通过 WebSearch 补全。

| Player | Chinese Name | Role (Leader / Challenger / Niche / Emerging) |
|---|---|---|
| | | |
| | | |
| | | |

---

## Progressive Build-Up（渐进补全策略）

```
第 1 次使用：domain.md（触发词 + 术语 + 玩家）→ WebSearch 即时搜索 → 产出报告
第 2 次使用：上次报告中发现的基准数据 → 沉淀到 technology.md 的评分矩阵
第 3 次使用：积累的技术路线对比 → 沉淀到 knowledge/*.md
...
第 N 次使用：knowledge 模块趋向完整，WebSearch 只为验证和更新
```

> 💡 不需要一开始就填满。`domain.md` 的 Key Subsystems 清单 + Terminology 已足够 AI 生成有质量的第一份报告。后续每次调研自然积累 knowledge。
