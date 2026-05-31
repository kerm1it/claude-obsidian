---
address: c-000452
type: synthesis
title: "Research: Offline online eval correlation 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - evals
  - online-evaluation
  - production-monitoring
status: active
related:
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
sources:
  - "[[sources/offline-metrics-predict-online-recsys-2020]]"
  - "[[sources/offline-ab-testing-recommender-systems-2018]]"
  - "[[sources/amazon-offline-online-product-ranking-2023]]"
  - "[[sources/langsmith-evaluation-types-2026]]"
  - "[[sources/langchain-production-monitoring-regression-tests-2026]]"
  - "[[sources/evaluation-driven-development-operations-llm-agents-2025]]"
  - "[[sources/openai-evaluation-best-practices-2026]]"
---

# Research: Offline online eval correlation 边界

## Overview

本轮研究把 offline / online eval correlation 归入第 6 层评估与可靠性层。它不是新的产品增长层，而是判断离线 eval、LLM judge、release card 和线上 outcome 是否同向的预测有效性边界。

稳定结论：**离线 eval 是候选筛选器，不是现实本身；上线后的 canary、A/B、online eval、人工反馈、投诉、成本和业务结果必须反过来校准离线质量门。**

## Key Findings

- Recommender systems 研究显示，offline metrics 可以和 online performance 有相关性，但离线指标提升对线上表现存在递减回报，候选排序也会随初始离线数据量变化。（Source: [[sources/offline-metrics-predict-online-recsys-2020]]）
- Offline A/B testing 研究用 counterfactual / off-policy estimators 估计新策略的潜在 uplift，并用线上 A/B business metrics 检验这些 estimator 的相关性。（Source: [[sources/offline-ab-testing-recommender-systems-2018]]）
- Amazon Science 的 product ranking 工作把 offline metrics 与 online business metrics 做 directional agreement 检验，说明“是否同向”本身就是工业评估对象。（Source: [[sources/amazon-offline-online-product-ranking-2023]]）
- LangSmith 文档把 backtesting、offline evaluation、online evaluation 和 production feedback loop 分开：production logs 可以转为 dataset，新版本再和真实 production outcomes 比较。（Source: [[sources/langsmith-evaluation-types-2026]]）
- LangChain 的 LLM evals 实践强调 offline 和 online eval 处理不同数据：offline 验证已知场景，online 监控真实 traces；真正有用的是把生产失败转成 regression tests，再上线验证修复。（Source: [[sources/langchain-production-monitoring-regression-tests-2026]]）
- EDDOps 论文把 offline development-time evaluation 和 online runtime evaluation 统一进闭环，强调 evaluation evidence 应驱动 runtime adaptation 和 governed redevelopment。（Source: [[sources/evaluation-driven-development-operations-llm-agents-2025]]）
- OpenAI eval best practices 要求用 production data、historical logs、human feedback 和 continuous evaluation 扩充 eval set，说明 eval 必须随真实产品分布增长。（Source: [[sources/openai-evaluation-best-practices-2026]]）

## 主归属

- 主归属：6. 评估与可靠性层
- 上游：offline eval、release card、LLM judge、canary/A-B、online eval、production trace、user/business/safety outcome
- 下游：eval trust tier、threshold refresh、dataset refresh、release gate update、production-to-regression feedback
- 组织接口：7. 产品与组织层

## 稳定框架

```text
offline release evidence
    -> staged online evidence
    -> align artifact/cohort/window/task/slice
    -> compare directional agreement, rank correlation, calibration, false pass/fail
    -> update eval trust, threshold, dataset, release gate, and feedback loop
```

## 与相邻概念的边界

- [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]：上线前写清楚预测和不确定性；本轮上线后验证预测是否成立。
- [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]：治理 eval 资产；本轮用线上 outcome 判断资产是否继续可信。
- [[concepts/ModelReleaseRollbackGate边界]]：执行发布/回滚；本轮校准 release gate 应信任哪些离线指标。
- [[concepts/DataFlywheelFeedbackLoop边界]]：分流真实使用信号；本轮判断哪些信号能校准 offline eval。

## Open Questions

- 对没有明确业务结果的高风险 safety eval，如何定义线上 outcome 的 proxy 和延迟窗口？
- 对低流量、高价值、长周期 agent 任务，如何在样本稀少时估计 offline/online correlation？
- 当线上 KPI 和安全 guardrail 冲突时，相关性报告应如何表达“业务同向但风险反向”？

## Sources

- [[sources/offline-metrics-predict-online-recsys-2020]]
- [[sources/offline-ab-testing-recommender-systems-2018]]
- [[sources/amazon-offline-online-product-ranking-2023]]
- [[sources/langsmith-evaluation-types-2026]]
- [[sources/langchain-production-monitoring-regression-tests-2026]]
- [[sources/evaluation-driven-development-operations-llm-agents-2025]]
- [[sources/openai-evaluation-best-practices-2026]]
