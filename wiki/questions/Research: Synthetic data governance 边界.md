---
address: c-000371
type: synthesis
title: "Research: Synthetic data governance 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - synthetic-data
  - data-governance
status: developing
related:
  - "[[concepts/SyntheticDataGovernance边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/Dream与SelfImprovement工程原语]]"
sources:
  - "[[sources/model-collapse-nature-2024]]"
  - "[[sources/is-model-collapse-inevitable-2024]]"
  - "[[sources/self-instruct-2022]]"
  - "[[sources/anthropic-constitutional-ai-rlaif-2022]]"
  - "[[sources/openai-model-distillation-2024]]"
  - "[[sources/openai-fine-tuning-data-quality-2026]]"
  - "[[sources/data-cards-2022]]"
---

# Research: Synthetic data governance 边界

## Overview

本轮研究 synthetic data governance：合成样本什么时候可以进入训练、eval、RAG、memory、skill、router 或 self-improvement。结论是：它主属第 6 层评估与可靠性层，因为核心问题不是“能不能生成”，而是“生成后能不能成为可信证据或训练候选”；第 2 层负责消费训练数据，第 7 层负责权利和用途，第 8 层只能提出候选改动。

## Key Findings

- Self-Instruct 证明模型自生成 instruction/input/output 样本可以提升 instruction following，但流程包含过滤无效或相似样本，并用专家写的新任务评估，说明合成数据有效依赖过滤和独立评估。(Source: [[sources/self-instruct-2022]])
- OpenAI model distillation 将强模型输出生成训练数据、fine-tune 小模型、再用 eval 验证，说明合成 teacher output 是工程化训练候选，而不是自动可部署能力。(Source: [[sources/openai-model-distillation-2024]])
- Constitutional AI / RLAIF 使用模型生成 critique、revision 和 AI feedback 来训练 harmlessness，但这类 synthetic feedback 需要明确原则、偏好模型和评估闭环。(Source: [[sources/anthropic-constitutional-ai-rlaif-2022]])
- Nature 2024 model collapse 论文显示，递归训练在生成数据上会让模型分布退化并丢失尾部信息，说明合成数据不能无约束替代真实数据。(Source: [[sources/model-collapse-nature-2024]])
- 2024 “Is Model Collapse Inevitable?” 发现，如果合成数据与原始真实数据累积而不是替换，实验中可以避免模型崩塌；因此治理结论不是“禁用合成数据”，而是“不能让合成数据替代真实分布和 hold-out”。(Source: [[sources/is-model-collapse-inevitable-2024]])
- Data Cards 强调数据集要记录来源、采集、处理、用途、限制和影响；合成数据尤其需要记录 generator、prompt、seed、filter 和用途。(Source: [[sources/data-cards-2022]])

## 稳定归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层、7. 产品与组织层、8. 自我改进与前沿层
- 上游输入：seed data、generator、teacher model、prompt、target gap、rights、real hold-out
- 下游输出：accepted synthetic train/eval samples、rejected queue、data card、lineage、monitoring signal

## 决策框架

```text
target gap
    -> seed rights / provenance
    -> generator + prompt + version
    -> generation
    -> filtering / dedup / diversity / label checks
    -> split and hold-out isolation
    -> real-world validation
    -> route to training, eval, RAG, memory, skill, simulation, or reject
```

## 用途矩阵

| 用途 | 默认判定 |
|---|---|
| Training candidate | 允许，但必须通过真实 hold-out、数据权利、去重和下游收益验证 |
| Distillation | 允许，teacher output 必须覆盖目标行为并由独立 eval 检查 |
| Eval / red-team | 允许，但必须与训练隔离，防止 synthetic eval 泄漏回训练 |
| RAG / knowledge | 默认只作摘要或候选，不能替代原始来源和 citation |
| Memory / personalization | 通常不直接写入，除非主体、时间、来源和可删性明确 |
| Self-improvement | 只能作为 proposed diff / candidate data，必须经过 gate |
| Privacy substitute | 不能自动视作匿名；仍要检查 seed data leakage 和重识别风险 |

## Contradictions

表面矛盾：Self-Instruct、distillation 和 RLAIF 显示合成数据有用；model collapse 显示合成数据会让模型退化。稳定解释是：合成数据在有目标、有过滤、有真实数据锚点、有独立 eval 时有用；当它递归替代真实分布、污染 eval 或由同一模型家族自我确认时会放大风险。

## Open Questions

- 不同任务中合成数据与真实数据的安全混合比例如何设定？
- 如何自动检测合成数据中的 generator fingerprint、同质化和隐藏 contamination？
- 当 synthetic eval 由同一模型家族生成和评分时，如何校准 judge bias？

## Sources

- [[sources/model-collapse-nature-2024]]：AI models collapse when trained on recursively generated data
- [[sources/is-model-collapse-inevitable-2024]]：Is Model Collapse Inevitable?
- [[sources/self-instruct-2022]]：Self-Instruct
- [[sources/anthropic-constitutional-ai-rlaif-2022]]：Constitutional AI
- [[sources/openai-model-distillation-2024]]：OpenAI model distillation
- [[sources/openai-fine-tuning-data-quality-2026]]：OpenAI fine-tuning data quality
- [[sources/data-cards-2022]]：Data Cards
