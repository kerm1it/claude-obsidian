---
address: c-000396
type: source
title: "OpenAI Evals"
source_url: https://github.com/openai/evals
source_type: repository
author: "OpenAI"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - evals
  - framework
  - benchmark
status: active
related:
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/EvalPortfolioMetricHierarchy边界]]"
---

# OpenAI Evals

**来源**：GitHub
**URL**：https://github.com/openai/evals

## 摘要

OpenAI Evals 是用于评估 LLM 和 LLM systems 的框架与 benchmark registry。它把 eval 表达为数据、配置、模板、grader 和运行结果，支持创建自定义 eval 和使用 registry 中的基准。

## 关键贡献

- 将 eval dataset、eval config、grader、runner 和 registry 分离成工程对象。
- 支持私有 eval 代表具体 workflow，而公开 registry 支持通用比较。
- 对本 vault 的意义：eval harness 运行评估；benchmark governance 管数据集的生命周期、泄漏、版本和决策用途。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：5. Agent 系统层、7. 产品与组织层

## 关联

- [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]
- [[concepts/EvalPortfolioMetricHierarchy边界]]
- [[Research: Evaluation dataset lifecycle benchmark governance 边界]]
