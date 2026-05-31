---
address: c-000535
type: research
title: "Research: Override debt exception analytics dashboard 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - research
  - governance
  - override
  - metrics
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]"
sources:
  - "[[sources/nist-sp800-55-measurement-guide-2024]]"
  - "[[sources/nist-sp800-137-continuous-monitoring-2011]]"
  - "[[sources/google-sre-good-housekeeping-error-budget-debt-2018]]"
  - "[[sources/google-sre-error-budget-policy-2018]]"
  - "[[sources/nist-sp800-37-risk-response-2018]]"
  - "[[sources/nist-ai-rmf-playbook-monitoring-responsibility-2026]]"
  - "[[sources/openai-preparedness-framework-2025]]"
  - "[[sources/microsoft-responsible-ai-standard-2022]]"
---

# Research: Override debt exception analytics dashboard 边界

## 问题

当 AI release、safety case、eval gray zone 或 residual-risk acceptance 里出现越来越多 override 时，如何判断这是合理的一次性例外，还是质量门正在被组织习惯侵蚀？

## 结论

Override debt / exception analytics dashboard 主属第 7 层。它不是新的 eval，也不是单条 override 审批，而是把单条例外记录聚合为治理健康指标：例外率、活跃债务、过期例外、续期、重复 owner、风险加权暴露、monitor coverage 和 incident conversion。

稳定链路是：`override records -> normalized ledger -> risk-weighted analytics -> threshold action -> gate/eval/policy backlog -> closure evidence`。

## 关键发现

- NIST SP 800-55 强调组织需要选择和评估 measures，用来判断 policies、procedures 和 controls 是否足够，并支持风险管理决策。(Source: [[sources/nist-sp800-55-measurement-guide-2024]])
- NIST SP 800-137 将 continuous monitoring 定义为对资产、威胁和 control effectiveness 的持续可见性，并在控制不足时及时响应风险。(Source: [[sources/nist-sp800-137-continuous-monitoring-2011]])
- Google SRE error budget practice 将 overspend 转成 release freeze、reliability work 和 debt paydown；同理，override 也需要预算和债务治理。(Source: [[sources/google-sre-good-housekeeping-error-budget-debt-2018]])
- Google SRE Error Budget Policy 显示指标必须绑定发布动作，否则 dashboard 不能改变系统行为。(Source: [[sources/google-sre-error-budget-policy-2018]])
- NIST SP 800-37 的 ongoing authorization 思路说明 authorizing official 需要持续判断当前风险是否仍可接受。(Source: [[sources/nist-sp800-37-risk-response-2018]])
- NIST AI RMF Playbook 要求明确 deployed AI 的监控、更新、角色职责和授权，支持把 override debt 接到 owner 和 review cadence。(Source: [[sources/nist-ai-rmf-playbook-monitoring-responsibility-2026]])
- OpenAI Preparedness Framework 的 residual risk review 提供了“风险证据 -> safeguards -> 部署决策”的组织链路，但单次 review 仍需要跨时间的 debt analytics。(Source: [[sources/openai-preparedness-framework-2025]])
- Microsoft Responsible AI Standard 强调 accountability 和 impact assessment，支持把例外接受转成可审查的组织责任记录。(Source: [[sources/microsoft-responsible-ai-standard-2022]])

## 分类决策

- 主归属：7. 产品与组织层
- 证据输入：6. 评估与可靠性层
- 上游：override record、release card、metric conflict、stale evidence、monitor breach、incident
- 下游：debt ledger、risk-weighted dashboard、review queue、gate/eval/policy backlog、release freeze 或 deny-renewal trigger

## Open Questions

- 高风险 AI 产品的默认 override budget 应按 release 数、用户影响、时间窗口还是 risk-weighted exposure 计算？
- 如何防止团队为了降低 override rate 而改走非结构化聊天/邮件批准？
- 哪些 override debt 指标应进入高层 review，哪些只需进入团队 backlog？

## 代表来源

- [[sources/nist-sp800-55-measurement-guide-2024]]
- [[sources/nist-sp800-137-continuous-monitoring-2011]]
- [[sources/google-sre-good-housekeeping-error-budget-debt-2018]]
- [[sources/google-sre-error-budget-policy-2018]]
- [[sources/nist-sp800-37-risk-response-2018]]
- [[sources/nist-ai-rmf-playbook-monitoring-responsibility-2026]]
- [[sources/openai-preparedness-framework-2025]]
- [[sources/microsoft-responsible-ai-standard-2022]]
