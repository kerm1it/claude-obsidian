---
address: c-000291
type: source
title: "RouterBench: A Benchmark for Multi-LLM Routing System"
source_url: https://arxiv.org/abs/2403.12031
source_type: paper
author: "Qitian Jason Hu et al."
published: 2024-03-18
updated_source: 2024-03-28
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - model-routing
  - benchmark
  - evals
status: active
related:
  - "[[concepts/ModelRoutingMixture边界]]"
  - "[[concepts/ReasoningEvalVerifier边界]]"
---

# RouterBench: A Benchmark for Multi-LLM Routing System

**来源**：arXiv
**URL**：https://arxiv.org/abs/2403.12031

## 摘要

RouterBench 提出 multi-LLM routing 系统的评估框架和数据集。它的前提是没有单一模型能在所有任务上同时最优，尤其在 performance 与 cost 之间权衡时，routing 系统需要被标准化评估。

## 关键贡献

- 将 LLM routing 系统作为需要独立评估的对象。
- 提供超过 405k inference outcomes 的数据集，覆盖多个代表性 LLM 和任务。
- 比较不同 routing 方法的潜力和局限，帮助评估经济可行的 LLM deployment。
- 对本 vault 的意义：router 本身进入第 6 层 eval，必须持续监控质量、成本、延迟和错误路由。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：3. 推理与能力层、7. 产品与组织层
- 作用：为 model routing 提供 evaluation surface。

## 关联

- [[concepts/ModelRoutingMixture边界]]
- [[concepts/ReasoningEvalVerifier边界]]
- [[Research: Model routing mixture 边界]]
