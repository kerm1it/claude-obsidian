---
address: c-000451
type: concept
title: "Offline / Online Eval Correlation 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - evals
  - online-evaluation
  - production-monitoring
  - correlation
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/MetricConflictResolution边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/ProductFeedbackClosureActionability边界]]"
  - "[[concepts/JudgeDriftGraderObservability边界]]"
  - "[[concepts/PostReleaseEvalDrift边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
sources:
  - "[[sources/google-sre-canarying-releases-2018]]"
  - "[[sources/offline-metrics-predict-online-recsys-2020]]"
  - "[[sources/offline-ab-testing-recommender-systems-2018]]"
  - "[[sources/amazon-offline-online-product-ranking-2023]]"
  - "[[sources/langsmith-evaluation-types-2026]]"
  - "[[sources/langchain-production-monitoring-regression-tests-2026]]"
  - "[[sources/langsmith-user-feedback-traces-2026]]"
  - "[[sources/evaluation-driven-development-operations-llm-agents-2025]]"
  - "[[sources/openai-evaluation-best-practices-2026]]"
  - "[[sources/nist-deployed-ai-monitoring-challenges-2026]]"
---

# Offline / Online Eval Correlation 边界

Offline / online eval correlation 是第 6 层评估与可靠性层的预测有效性边界：它检查离线 eval、LLM judge、benchmark、release card 和 production outcome 是否同向，决定哪些离线指标仍能作为第 7 层 release gate 的可信前置信号。

一句话：**离线 eval 负责快速筛选候选；线上 outcome 负责校准离线 eval 是否真的预测真实用户和业务结果。**

## 主归属

- 主归属：6. 评估与可靠性层
- 组织接口：7. 产品与组织层
- 上游输入：offline eval delta、release card、benchmark/hold-out、LLM judge score、canary/A-B/online eval、production trace、user feedback、business metric、incident signal
- 下游输出：metric correlation report、directional-agreement score、eval trust tier、eval refresh/retire decision、release gate rule update、production-to-regression dataset candidate
- 反馈接口：[[concepts/DataFlywheelFeedbackLoop边界]]

## 稳定链路

```text
candidate change and release-card hypothesis
    -> offline eval delta: primary, guardrail, slice, judge, cost, latency
    -> staged online evidence: canary, A/B, online evaluator, human review, production telemetry
    -> align units: same artifact, cohort, time window, task taxonomy, risk tier, baseline
    -> compare deltas: directional agreement, rank correlation, calibration, false pass / false fail
    -> decide eval trust: keep, reweight, split by slice, refresh, quarantine, or retire metric
    -> update release gate, eval dataset, dashboard, card template, and production feedback loop
```

## 相关性类型

| 类型 | 回答的问题 | 典型动作 |
|---|---|---|
| Directional agreement | 离线指标涨时，线上 outcome 是否也改善？ | 保留或降权指标 |
| Rank correlation | 多个候选的离线排序是否预测线上排序？ | 选择候选或要求线上实验 |
| Calibration curve | 离线 delta 多大才对应可见线上改善？ | 更新 threshold 和 MDE |
| Slice agreement | 哪些用户、语言、任务、工具路径同向？ | 拆分 eval、加 slice gate |
| Failure capture | 线上事故/投诉是否能被离线 eval 捕捉？ | 把 trace 转成 regression |
| Cost-quality agreement | 成本/延迟优化是否损害线上满意度？ | 调整 router / serving gate |
| Judge-to-human agreement | LLM judge online score 是否预测人工/用户反馈？ | 校准或替换 judge |

## 与相邻概念区别

- 与 [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]：release card 写明上线前证据和不确定性；本页在上线后验证卡片里的预测是否和真实 outcome 同向。
- 与 [[concepts/PostReleaseEvalDrift边界]]：本页判断离线指标和线上 outcome 是否同向；post-release eval drift 持续监控这种关系和 release evidence 是否随时间变 stale。
- 与 [[concepts/EvalResultInterpretationDecisionThreshold边界]]：decision threshold 解释一次 eval 是否过线；本页评估这个阈值长期是否能预测线上成败。
- 与 [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]：benchmark governance 管 eval 资产；本页用 production correlation 决定资产是否可信、需刷新或退役。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：release gate 做发布/回滚动作；本页给 gate 提供“哪些离线指标可靠”的校准证据。
- 与 [[concepts/MetricConflictResolution边界]]：本页发现 offline 和 online 证据冲突；metric conflict resolution 决定降权、canary hold、补 eval、限制范围或 release override。
- 与 [[concepts/DataFlywheelFeedbackLoop边界]]：data flywheel 分流真实使用信号；本页专门判断这些信号如何校准离线 eval。
- 与 [[concepts/ProductFeedbackClosureActionability边界|product feedback closure]]：本页判断线上反馈是否校准离线 eval；feedback closure 要求这些线上反馈进入可行动 artifact 并被验证关闭。
- 与 A/B testing：A/B testing 估计线上因果效果；本页比较离线指标和线上效果的关系，决定是否能少做、缩小或优先安排线上实验。
- 与 online eval：online eval 是生产测量；offline/online correlation 是把线上测量反过来校准离线质量门。

## 工程实践

1. 每次 release card 记录 offline delta、threshold、灰区、预期线上影响和对应 production metric。
2. 上线后按同一 artifact、cohort、time window、risk tier 和 task taxonomy 对齐线上结果。
3. 分开 user outcome、business outcome、safety outcome、cost/latency outcome，不把一个指标当全局真相。
4. 用 directional agreement 做第一层：离线改善是否至少不反向伤害线上指标。
5. 用 rank correlation / calibration curve 管候选排序和阈值幅度；小离线提升常会在线上递减。
6. 对关键 slice 单独算相关性：语言、地区、设备、用户层级、工具路径、RAG corpus、风险类别。
7. 线上新失败必须回填：trace → annotation / judge review → regression eval → release gate。
8. 当相关性下降，先 quarantine 该 eval 或 judge 分数，不让它直接进入 release gate、router、training 或 self-improvement。

## 评估方式

- Directional agreement rate：离线和线上 delta 同向比例。
- False pass / false fail：离线放行但线上失败、离线阻断但线上可行的比例。
- Rank correlation：离线候选排序与线上效果排序是否一致。
- Calibration error：离线分数提升幅度与线上影响幅度的偏差。
- Regression capture rate：线上失败有多少能被转成离线 regression 并复现。
- Segment stability：相关性是否在关键用户、任务、语言和工具路径上稳定。
- Decision latency：线上信号多久能校准 release decision。
- Eval trust tier drift：指标是否从 high-trust 降为 diagnostic-only 或 retire。

## 过时风险

- 产品、用户分布、模型、provider、prompt、RAG、tool 和 judge 变化都会改变相关性；相关性是需要监控的运行属性，不是一次性证明。
- 线上 outcome 往往滞后且受产品 UI、流量、季节性和业务活动影响；需要 cohort、time window 和 confounder 记录。
- 如果只优化与线上 KPI 相关的离线指标，可能引入 reward hacking；相关性报告必须保留 guardrail、hold-out 和人类审查。

## 一句话归类

Offline / online eval correlation 主属第 6 层，是离线 eval、release card 和线上 production outcome 之间的预测有效性边界；它决定哪类离线证据仍能被第 7 层 release gate 信任。
