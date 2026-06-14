---
address: c-000538
type: source
title: "Google SRE Good Housekeeping for Error Budgets"
source_url: https://cloud.google.com/blog/products/devops-sre/good-housekeeping-error-budgetscre-life-lessons
source_type: engineering-blog
author: "Google Cloud"
date_published: 2018-06-28
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - sre
  - error-budget
  - debt
  - release-freeze
status: active
related:
  - "[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]"
  - "[[concepts/OverrideGovernanceResidualRiskAcceptance边界]]"
---

# Google SRE Good Housekeeping for Error Budgets

**来源**：Google Cloud Blog / CRE Life Lessons
**URL**：https://cloud.google.com/blog/products/devops-sre/good-housekeeping-error-budgetscre-life-lessons

## 摘要

Google SRE 的 error budget housekeeping 将 error budget overspend 视为需要分析和偿还的 debt：识别主要 spend contributors，临时降低 release velocity，转向 reliability work，必要时 feature freeze，并要求有限 override 有成本和 postmortem。

## 关键贡献

- Debt 不是抽象隐喻，而是会改变发布节奏和工程优先级的治理信号。
- Overspend 分析要找到主要贡献者，而不是只惩罚最后一次 release。
- 重要例外可以存在，但应 expensive、limited in frequency，并触发 postmortem。
- 对本 vault 的意义：override debt dashboard 可以借用 error budget 思路，把例外率、续期和过期状态绑定到 release freeze、review 和 debt paydown。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]
- [[concepts/OverrideGovernanceResidualRiskAcceptance边界]]
- [[Research: Override debt exception analytics dashboard 边界]]
