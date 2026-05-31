---
address: c-000513
type: research
title: "Research: Override governance residual risk acceptance 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - research
  - governance
  - residual-risk
  - override
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/OverrideGovernanceResidualRiskAcceptance边界]]"
sources:
  - "[[sources/nist-sp800-37-risk-response-2018]]"
  - "[[sources/nist-sp800-30-risk-assessment-2012]]"
  - "[[sources/nist-ai-rmf-risk-tolerance-2023]]"
  - "[[sources/openai-preparedness-framework-2025]]"
  - "[[sources/microsoft-responsible-ai-standard-2022]]"
  - "[[sources/google-sre-error-budget-policy-2018]]"
---

# Research: Override governance residual risk acceptance 边界

## 问题

第 7 层如何防止 exception、override 和 residual risk acceptance 变成绕过 eval、release card、stop rule、safety case 和 release gate 的常态？

## 结论

Override governance / residual risk acceptance 应主属第 7 层，因为它解决的是组织决策、责任、期限、监控和审计问题。它消费第 6 层证据，但不替代 eval；它必须被 stop rule 约束，并反哺 release gate、monitor 和 safety case。

稳定链路是：`exception request -> hard-stop check -> residual-risk record -> approval authority -> expiry + monitor -> review/revoke/close`。

## 关键发现

- NIST SP 800-37 的 risk response 明确包括 acceptance、mitigation 等 response，并强调风险接受要保留 deficiencies、monitor risk factors、由授权责任人接受剩余风险。(Source: [[sources/nist-sp800-37-risk-response-2018]])
- NIST SP 800-30 把 risk assessment 作为给 senior leaders / executives 提供决策信息的过程；AI override 必须保留 likelihood、impact、uncertainty 和 course-of-action evidence。(Source: [[sources/nist-sp800-30-risk-assessment-2012]])
- NIST AI RMF risk tolerance 说明组织要定义风险偏好和不可接受风险；这支持把 hard-stop 与可接受 residual risk 分开。(Source: [[sources/nist-ai-rmf-risk-tolerance-2023]])
- OpenAI Preparedness Framework 使用专门的 safety review 和 stronger safeguards / further evaluation 决策语言，说明 frontier deployment 例外不能只靠产品 owner 单方决定。(Source: [[sources/openai-preparedness-framework-2025]])
- Microsoft Responsible AI Standard 强调 product requirements、impact assessment 和 governance review；这支持把 residual risk acceptance 写成审查记录而非临时判断。(Source: [[sources/microsoft-responsible-ai-standard-2022]])
- Google SRE error budget policy 展示了 release halt、exception 和 executive approval 的运营模式；AI release override 可借鉴“默认阻断 + 明确批准 + 过期/复审”的结构。(Source: [[sources/google-sre-error-budget-policy-2018]])

## 分类决策

- 主归属：7. 产品与组织层
- 质量输入：6. 评估与可靠性层
- 上游：metric conflict、gray-zone eval、stale evidence、guardrail breach、release-card limitation、business pressure
- 下游：deny/approve/restrict/canary/rollback、risk register、release card、safety case、monitor obligation、review task

## Open Questions

- 不同风险等级的 override 默认过期时间应如何设定？
- 哪些 AI 风险必须要求 external reviewer 或 legal/security co-approval？
- 如何把 override debt 转成路线图优先级，而不是无限延期？

## 代表来源

- [[sources/nist-sp800-37-risk-response-2018]]
- [[sources/nist-sp800-30-risk-assessment-2012]]
- [[sources/nist-ai-rmf-risk-tolerance-2023]]
- [[sources/openai-preparedness-framework-2025]]
- [[sources/microsoft-responsible-ai-standard-2022]]
- [[sources/google-sre-error-budget-policy-2018]]
