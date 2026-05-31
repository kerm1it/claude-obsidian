---
address: c-000560
type: concept
title: "Dashboard Calibration / Governance Metric Quality 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - governance
  - dashboard
  - metrics
  - calibration
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]"
  - "[[concepts/ReleaseGateDebtBypassDetection边界]]"
  - "[[concepts/EvalPortfolioMetricHierarchy边界]]"
  - "[[concepts/MetricConflictResolution边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
  - "[[concepts/PostReleaseEvalDrift边界]]"
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/ProductFeedbackClosureActionability边界]]"
sources:
  - "[[sources/nist-sp800-55-measurement-guide-2024]]"
  - "[[sources/nist-sp800-55-vol2-measurement-program-2024]]"
  - "[[sources/nist-sp800-137-continuous-monitoring-2011]]"
  - "[[sources/nist-ai-rmf-playbook-monitoring-responsibility-2026]]"
  - "[[sources/google-sre-monitoring-distributed-systems-2016]]"
  - "[[sources/google-sre-alerting-on-slos-2018]]"
  - "[[sources/dora-software-delivery-performance-metrics-2026]]"
  - "[[sources/microsoft-responsible-ai-dashboard-2026]]"
---

# Dashboard Calibration / Governance Metric Quality 边界

Dashboard calibration / governance metric quality 是第 7 层产品与组织层的治理测量质量边界：它判断 AI governance dashboard 里的指标是否定义清楚、数据来源可靠、能被校准、能触发正确行动，并且没有因为 stale、偏差、不可比、低覆盖或 Goodhart 式优化而变成指标剧场。

一句话：**dashboard 展示信号；dashboard calibration 证明这些信号足以支持 release、review、freeze、rollback、deny renewal 或 backlog 决策。**

## 主归属

- 主归属：7. 产品与组织层
- 质量输入：6. 评估与可靠性层
- 上游输入：eval metrics、monitor signals、override records、gate bypass findings、incident data、release cards、SLO/SLI、business outcomes、audit packets
- 下游输出：metric definition sheet、calibration report、dashboard trust tier、action threshold update、metric quarantine、dashboard retirement、governance review backlog
- 证据底座：[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]

## 稳定链路

```text
decision inventory
    -> metric claim: what decision this number supports
    -> metric definition: numerator, denominator, source, scope, slice, window, lag, owner
    -> data quality and lineage check: missingness, freshness, duplication, coverage, access, retention
    -> calibration: compare with incidents, human review, online outcomes, interventions, false alarms
    -> dashboard trust tier: action metric, guardrail, diagnostic, exploratory, retired
    -> threshold and action ladder: warn, owner ticket, review, freeze, rollback, deny renewal, backlog
    -> post-action review: did the dashboard improve the real outcome?
    -> metric refresh, quarantine, split, merge, or retire
```

## 指标质量维度

| 维度 | 问题 |
|---|---|
| Decision relevance | 这个指标控制哪个真实决策，还是只是好看 |
| Definition stability | numerator、denominator、窗口、slice 和排除规则是否固定 |
| Data lineage | 数据来自哪里，是否能追到 release、eval、monitor、incident 或 audit packet |
| Freshness | 指标是否仍反映当前 artifact、policy、judge、provider、product 状态 |
| Coverage | 是否覆盖关键产品线、risk tier、artifact type、tenant、provider 和高风险 slice |
| Calibration | 高/低分是否真的对应事故、回滚、用户伤害、质量改善或债务下降 |
| Actionability | 超阈值时谁行动、做什么、多久关闭、证据是什么 |
| Anti-gaming | 优化这个指标会不会隐藏真实风险、诱导少报或转移问题 |

## 与相邻概念区别

- 与 [[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]：override debt dashboard 是一个具体治理看板；本页判断 dashboard 中的 override rate、expired exception、renewal、risk exposure 等指标是否可信、可比、可行动。
- 与 [[concepts/ReleaseGateDebtBypassDetection边界]]：gate bypass detection 产生 admin bypass、shadow approval、direct path、stale exception 等信号；本页校准这些信号是否被正确计数、分母是否清楚、漏报是否被审查。
- 与 [[concepts/EvalPortfolioMetricHierarchy边界]]：eval portfolio 组织指标角色；dashboard calibration 检查这些角色进入看板后是否仍然有效、可解释、可触发行动。
- 与 [[concepts/EvalResultInterpretationDecisionThreshold边界]]：threshold 把单个 metric 转成决策；dashboard calibration 验证多个 dashboard metric 的数据质量、阈值质量和行动后效果。
- 与 [[concepts/OfflineOnlineEvalCorrelation边界]]：offline/online correlation 校准 eval 预测线上结果；dashboard calibration 还覆盖治理、事故、例外、发布、SLO 和组织行动指标。
- 与 [[concepts/MonitorOwnershipEscalationLadder边界]]：monitor ownership 定义信号交给谁；dashboard calibration 判断信号是否值得交给人，以及是否造成误报、漏报或无效行动。
- 与 [[concepts/ProductFeedbackClosureActionability边界|product feedback closure]]：本页校准 dashboard 指标是否可信；feedback closure 证明指标或反馈是否已经触发具体行动并带证据关闭。
- 与 generic BI dashboard：本页不是报表美化，而是 governance measurement system，必须绑定证据、阈值、owner、行动和指标复审。

## 工程实践

1. 先写 decision inventory：每张 dashboard 只保留能支持 release、rollback、review、budget、risk、incident 或 backlog 的指标。
2. 给每个指标写 metric definition sheet：claim、owner、source、query、numerator、denominator、slice、window、lag、freshness、threshold、action。
3. 将指标按角色分层：action metric、hard guardrail、diagnostic、exploratory、vanity、retired；vanity 和 retired 不允许驱动治理动作。
4. 对输入数据做 lineage 和 quality check：缺失、重复、延迟、权限、采样偏差、provider/API schema 变化、手工录入质量。
5. 做 outcome calibration：看 dashboard 告警、freeze、review、deny renewal 是否预测或减少事故、回滚、用户影响、风险暴露或债务。
6. 记录 false action 和 missed action：误冻结、误升级、漏报事故、漏报绕过、低质量例外关闭都要进入 metric review。
7. 对指标设 refresh/retire cadence：policy、product、provider、judge、artifact type、risk taxonomy 或组织流程改变后，必须复核指标。
8. 做 anti-gaming review：检查指标是否诱导少报、拆小变更、隐藏例外、延迟关闭、绕过 dashboard 或追求低风险外观。
9. 将 dashboard action 与 feedback closure ticket 绑定，要求 owner、artifact、验证结果和关闭证据，否则指标只能算 diagnostic，不能算 action metric。

## 评估方式

- Decision hit rate：dashboard 触发的行动有多少被事后证明合理。
- False action rate：指标导致的误冻结、误升级、误回滚或误 backlog。
- Missed risk rate：事故、绕过、过期例外或用户伤害发生前，dashboard 是否漏报。
- Metric freshness SLA：指标依赖的 source、query、schema、policy、artifact map 是否仍有效。
- Coverage gap：高风险产品线、artifact type、provider、tenant、risk tier 是否缺指标。
- Calibration drift：指标和真实 outcome、incident conversion、online eval、human review 的相关性是否下降。
- Closure quality：dashboard 行动关闭是否有 evidence packet，而不是口头“已处理”。
- Feedback closure rate：dashboard 触发的 owner ticket 有多少完成验证并带 closure evidence，多少重开或复发。
- Gaming signal：指标改善但真实风险、事故或用户体验没有改善。

## 过时风险

- 具体 BI 工具、observability 工具和 dashboard UI 会变化，但 decision inventory、metric definition、data lineage、calibration、action ladder、refresh/retire 稳定。
- 指标一旦绑定绩效和发布压力，就会被优化；必须持续做 anti-gaming 和 outcome calibration。
- 低频高风险 AI 事故会让指标样本稀疏；这时需要 human review、scenario drill、synthetic stress、tabletop 和近失事件补足校准。

## 一句话归类

Dashboard calibration / governance metric quality 主属第 7 层，是 governance dashboard 进入组织决策前的测量质量边界；它不新增顶层，而是把第 6 层指标和第 7 层行动之间的“这数字到底能不能信”固定下来。
