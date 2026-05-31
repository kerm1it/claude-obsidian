---
address: c-000505
type: research
title: "Research: Monitor tabletop runbook drill 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - research
  - tabletop
  - runbook
  - incident-response
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/MonitorTabletopRunbookDrill边界]]"
sources:
  - "[[sources/google-sre-incident-management-guide-2026]]"
  - "[[sources/google-sre-managing-incidents-2016]]"
  - "[[sources/microsoft-ai-incident-response-readiness-2026]]"
  - "[[sources/nist-sp800-84-tte-program-2006]]"
  - "[[sources/ncsc-effective-steps-cyber-exercise-creation-2026]]"
  - "[[sources/aws-security-ir-simulations-2026]]"
  - "[[sources/cisa-ai-cyber-tabletop-exercise-series-2025]]"
  - "[[sources/fema-hseep-exercise-evaluation-2020]]"
---

# Research: Monitor tabletop runbook drill 边界

## 问题

第 7 层如何演练 monitor owner、on-call、incident command、release gate、risk owner、provider POC 和 comms/legal/support 的交接，避免监控和 runbook 只停在文档里？

## 结论

Monitor tabletop / runbook drill 应主属第 7 层，因为它验证的是组织响应能力、决策权限、交接质量和改进闭环。它不是新的可靠性顶层，也不是普通 eval；它消费第 6 层信号，验证第 7 层行动链。

稳定链路是：`scenario -> injects -> role handoff -> decision/action -> after-action report -> improvement plan -> re-drill`。

## 关键发现

- Google SRE 的事故管理模型强调 incident command、ops、comms、planning 和 live state document；演练要验证这些角色和状态文档是否能在 AI 事故中快速建立。(Source: [[sources/google-sre-managing-incidents-2016]])
- Google SRE incident management guide 强调提前训练、角色清晰、指挥与执行分离；这支持把 monitor drill 设计成角色演练，而不是只检查 dashboard。(Source: [[sources/google-sre-incident-management-guide-2026]])
- Microsoft AI incident readiness 明确 AI 事故需要 AI-specific taxonomy、observability、staged remediation、ownership、escalation triggers，并建议测试 cross-functional coordination。(Source: [[sources/microsoft-ai-incident-response-readiness-2026]])
- NIST SP 800-84 给出 tabletop exercise 程序框架，强调目标、场景、参与者、facilitator、observer、evaluation 和 after-action improvement plan。(Source: [[sources/nist-sp800-84-tte-program-2006]])
- NCSC 的 exercise guidance 把演练创建拆成 objective、scope、scenario、injects、facilitation、evaluation 和 learning loop，适合 AI monitor drill 的轻量结构。(Source: [[sources/ncsc-effective-steps-cyber-exercise-creation-2026]])
- AWS security incident simulation guidance 区分 tabletop、functional 和 full-scale/live simulation；AI runbook drill 可以从 discussion-based tabletop 逐步升级到 controlled technical drill。(Source: [[sources/aws-security-ir-simulations-2026]])
- CISA AI cybersecurity tabletop series 把 AI 特有风险纳入演练场景，说明 AI 响应演练需要覆盖模型、数据、供应链、权限和跨组织协调。(Source: [[sources/cisa-ai-cyber-tabletop-exercise-series-2025]])
- FEMA HSEEP 强调 evaluation、after-action report 和 improvement plan；这防止演练变成一次性会议。(Source: [[sources/fema-hseep-exercise-evaluation-2020]])

## 分类决策

- 主归属：7. 产品与组织层
- 质量输入：6. 评估与可靠性层
- 上游：monitor/eval/release-card/freshness/provider/user-report signals
- 下游：owner readiness、runbook updates、release-gate update、incident playbook update、new eval/monitor tasks

## Open Questions

- 高风险 AI 系统的 tabletop 频率应该按 release cadence、risk tier 还是 incident history 决定？
- 哪些 drill 可以进入 live controlled exercise，哪些只能保持 discussion-based tabletop？
- 如何量化演练对真实事故 MTTD/MTTR、false escalation 和 recurrence 的贡献？

## 代表来源

- [[sources/google-sre-incident-management-guide-2026]]
- [[sources/google-sre-managing-incidents-2016]]
- [[sources/microsoft-ai-incident-response-readiness-2026]]
- [[sources/nist-sp800-84-tte-program-2006]]
- [[sources/ncsc-effective-steps-cyber-exercise-creation-2026]]
- [[sources/aws-security-ir-simulations-2026]]
- [[sources/cisa-ai-cyber-tabletop-exercise-series-2025]]
- [[sources/fema-hseep-exercise-evaluation-2020]]
