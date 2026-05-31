---
address: c-000395
type: source
title: "Evaluation best practices"
source_url: https://platform.openai.com/docs/guides/evaluation-best-practices
source_type: documentation
author: "OpenAI"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - evals
  - evaluation
  - ai
status: active
related:
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/EvalPortfolioMetricHierarchy边界]]"
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
---

# Evaluation best practices

**来源**：OpenAI Developers Docs
**URL**：https://platform.openai.com/docs/guides/evaluation-best-practices

## 摘要

OpenAI evaluation best practices 将 eval 定义为测试 AI 系统准确性、性能和可靠性的结构化方法，并强调 eval-driven development、task-specific eval、日志挖掘、人类反馈校准、continuous evaluation 和生产分布覆盖。

## 关键贡献

- 把 eval 过程拆成 objective、dataset、metrics、run/compare、continuous evaluation。
- 区分 industry benchmark、通用指标和自定义产品 eval。
- 强调 eval set 要随产品迭代增长，并用 human feedback 校准自动评分。
- 对本 vault 的意义：eval dataset lifecycle 是持续过程，不是一次性测试文件。
- 对 offline/online correlation 的意义：production data、historical logs、human feedback 和 continuous evaluation 是校准离线 eval 是否预测真实分布的来源。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层、8. 自我改进与前沿层

## 关联

- [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]
- [[concepts/EvalPortfolioMetricHierarchy边界]]
- [[concepts/EvidenceFreshnessStaleProof边界]]
- [[concepts/EvalResultInterpretationDecisionThreshold边界]]
- [[concepts/OfflineOnlineEvalCorrelation边界]]
- [[Research: Evaluation dataset lifecycle benchmark governance 边界]]
