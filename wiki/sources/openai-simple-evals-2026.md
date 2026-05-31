---
address: c-000473
type: source
title: "OpenAI simple-evals"
source_url: https://github.com/openai/simple-evals
source_type: repository
author: "OpenAI"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - evals
  - benchmarks
  - repository
status: active
related:
  - "[[concepts/EvalPortfolioMetricHierarchy边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
---

# OpenAI simple-evals

**来源**：OpenAI GitHub
**URL**：https://github.com/openai/simple-evals

## 摘要

OpenAI simple-evals 是一个轻量 benchmark runner，汇集 MMLU、MATH、GPQA、DROP、MGSM、HumanEval、SimpleQA、BrowseComp、HealthBench 等评估，并支持通过 API 对模型运行这些 eval。

## 关键贡献

- 展示 public benchmark 可以作为 eval portfolio 中的通用能力探针。
- 明确该仓库不是 OpenAI Evals 的完整替代，而是轻量集合。
- 说明 benchmark 会饱和，因此应作为 portfolio 的一部分，而不是唯一发布依据。
- 对本 vault 的意义：public benchmark 属于 diagnostic / broad capability evidence，产品 release 仍需 private hold-out、regression、contract、online 和 safety evidence。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/EvalPortfolioMetricHierarchy边界]]
- [[Research: Eval portfolio metric hierarchy 边界]]
