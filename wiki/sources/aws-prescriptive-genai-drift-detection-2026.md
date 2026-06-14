---
address: c-000469
type: source
title: "Detecting drift in production applications"
source_url: https://docs.aws.amazon.com/prescriptive-guidance/latest/gen-ai-lifecycle-operational-excellence/prod-monitoring-drift.html
source_type: official-docs
author: "AWS Prescriptive Guidance"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - drift
  - llmops
  - production-monitoring
status: active
related:
  - "[[concepts/PostReleaseEvalDrift边界]]"
  - "[[concepts/JudgeDriftGraderObservability边界]]"
---

# Detecting Drift in Production Applications

**来源**：AWS Prescriptive Guidance
**URL**：https://docs.aws.amazon.com/prescriptive-guidance/latest/gen-ai-lifecycle-operational-excellence/prod-monitoring-drift.html

## 摘要

AWS 将 LLM drift 描述为生产中随时间出现的性能退化，通常由数据分布或用户行为变化导致。它建议先比较 reference 与 current distribution，再用适合 embedding 空间的距离指标触发 alert，最后用 LLM-as-judge 做语义诊断。

## 关键贡献

- 将 prompt/input 分布变化与生成输出质量退化连接起来。
- 强调高维 embedding 空间中传统单变量漂移测试不足，需要更合适的距离度量。
- 给出双层方法：统计 drift alert + LLM judge 语义分类。
- 对本 vault 的意义：post-release eval drift 要区分“发生了漂移”和“漂移意味着哪些 release evidence 失效”。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/PostReleaseEvalDrift边界]]
- [[Research: Post-release eval drift 边界]]
