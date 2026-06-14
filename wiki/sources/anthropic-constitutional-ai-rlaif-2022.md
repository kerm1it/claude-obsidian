---
address: c-000375
type: source
title: "Constitutional AI: Harmlessness from AI Feedback"
source_url: https://www.anthropic.com/research/constitutional-ai-harmlessness-from-ai-feedback
source_type: research
author: "Anthropic"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - synthetic-feedback
  - rlaif
  - alignment
status: active
related:
  - "[[concepts/SyntheticDataGovernance边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
---

# Constitutional AI: Harmlessness from AI Feedback

**来源**：Anthropic Research
**URL**：https://www.anthropic.com/research/constitutional-ai-harmlessness-from-ai-feedback

## 摘要

Anthropic Constitutional AI 研究使用原则集合指导模型生成 critique、revision 和 AI feedback，以减少人工标注依赖并训练更 harmless 的 assistant。它是 synthetic feedback / RLAIF 的代表来源。

## 关键贡献

- 显示合成反馈可以参与 alignment training。
- 关键不是“让模型随便评价自己”，而是用明确原则、训练流程和评估约束 AI feedback。
- 对本 vault 的意义：synthetic preference / critique 属于训练候选，必须防止 judge bias、reward hacking 和自我确认。

## 对 AI 知识体系的归属

- 主归属：2. 模型构建层
- 交叉链接：6. 评估与可靠性层、8. 自我改进与前沿层

## 关联

- [[concepts/SyntheticDataGovernance边界]]
- [[Research: Synthetic data governance 边界]]
