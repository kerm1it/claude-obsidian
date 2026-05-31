---
address: c-000456
type: source
title: "LangSmith Evaluation Types"
source_url: https://docs.langchain.com/langsmith/evaluation-types
source_type: documentation
author: "LangChain"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - evals
  - llmops
  - online-evaluation
  - offline-evaluation
status: active
related:
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
---

# LangSmith Evaluation Types

**来源**：LangChain Docs
**URL**：https://docs.langchain.com/langsmith/evaluation-types

## 摘要

LangSmith 文档区分 offline evaluation、backtesting、pairwise evaluation 和 online evaluation。它把 production logs 转换为 dataset 后用于 backtesting，并说明 online evaluations 在生产流量上近实时运行，用于质量趋势、异常和边界 case。

## 关键贡献

- 明确 offline eval、online eval 和 backtesting 适用的数据和问题不同。
- 把 failed production runs 作为 offline dataset candidates，形成 production feedback loop。
- 对本 vault 的意义：offline/online correlation 需要同时记录离线 dataset 结果和线上 traces/outcomes。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/OfflineOnlineEvalCorrelation边界]]
- [[Research: Offline online eval correlation 边界]]
