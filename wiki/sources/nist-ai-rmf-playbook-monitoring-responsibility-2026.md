---
address: c-000484
type: source
title: "NIST AI RMF Playbook monitoring responsibility prompts"
source_url: https://airc.nist.gov/docs/AI_RMF_Playbook.pdf
source_type: framework
author: "NIST AI Resource Center"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - nist
  - monitoring
  - governance
status: active
related:
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
  - "[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]"
  - "[[concepts/DashboardCalibrationGovernanceMetricQuality边界]]"
---

# NIST AI RMF Playbook monitoring responsibility prompts

**来源**：NIST AI Resource Center
**URL**：https://airc.nist.gov/docs/AI_RMF_Playbook.pdf

## 摘要

NIST AI RMF Playbook 把 AI 系统部署后的维护、再验证、监控、更新、角色职责和授权作为组织必须回答的问题。它多次要求明确 design、development、deployment、assessment 和 monitoring 中人员的 roles、responsibilities 和 delegation of authorities。

## 关键贡献

- 要求说明谁负责 deployed AI 的维护、再验证、监控和更新。
- 要求定义 monitoring 相关角色、职责和授权。
- 要求建立 incident、negative outcome、drift、decontextualization 和 deactivation 相关流程。
- 对本 vault 的意义：monitor ownership 不是单独的仪表盘字段，而是 AI risk management 的治理责任。
- 对 override debt dashboard 的意义：例外债务指标需要明确 owner、authority、review cadence 和 action path。
- 对 dashboard calibration 的意义：需要记录 metric selection criteria、未测量风险的理由、部署后 performance monitoring 和 existing metrics 是否仍 sufficient。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/MonitorOwnershipEscalationLadder边界]]
- [[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]
- [[concepts/DashboardCalibrationGovernanceMetricQuality边界]]
- [[Research: Monitor ownership escalation ladder 边界]]
- [[Research: Override debt exception analytics dashboard 边界]]
- [[Research: Dashboard calibration governance metric quality 边界]]
