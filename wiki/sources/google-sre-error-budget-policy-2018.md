---
address: c-000421
type: source
title: "Error Budget Policy for Service Reliability"
source_url: https://sre.google/workbook/error-budget-policy/
source_type: book-chapter
author: "Google SRE"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - sre
  - error-budget
  - release-gate
status: active
related:
  - "[[concepts/MetricConflictResolution边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
  - "[[concepts/OverrideGovernanceResidualRiskAcceptance边界]]"
  - "[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]"
---

# Error Budget Policy for Service Reliability

**来源**：Google SRE Workbook
**URL**：https://sre.google/workbook/error-budget-policy/

## 摘要

Google SRE Workbook 的 error budget policy 把服务是否满足 SLO 转成发布策略：在 SLO 内继续发布，超出 error budget 时暂停非紧急变更，并把重大消耗转成 postmortem 和规划项。

## 关键贡献

- Error budget 是 1 - SLO，用于平衡可靠性和创新速度。
- 超出预算时，发布政策改变；单次事故或同类事故消耗过多预算时触发 postmortem 或规划项。
- 对本 vault 的意义：AI eval threshold 也应绑定动作，例如 promote、hold、rollback、disable、human review，而不是只展示仪表盘。
- 对 override governance 的意义：例外应默认阻断、明确批准、限制范围并复审，避免持续 override 变成事实政策。
- 对 override debt dashboard 的意义：例外率、续期和过期状态只有绑定 release freeze、review 和 debt paydown，才不是单纯报表。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/EvalResultInterpretationDecisionThreshold边界]]
- [[concepts/ModelReleaseRollbackGate边界]]
- [[concepts/MetricConflictResolution边界]]
- [[concepts/OverrideGovernanceResidualRiskAcceptance边界]]
- [[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]
- [[Research: Override governance residual risk acceptance 边界]]
- [[Research: Override debt exception analytics dashboard 边界]]
