---
address: c-000483
type: research
title: "Research: Monitor ownership escalation ladder 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - research
  - monitoring
  - escalation
  - governance
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
sources:
  - "[[sources/nist-ai-rmf-playbook-monitoring-responsibility-2026]]"
  - "[[sources/nist-sp800-61r3-incident-response-2025]]"
  - "[[sources/google-sre-being-on-call-2016]]"
  - "[[sources/google-sre-managing-incidents-2016]]"
  - "[[sources/microsoft-ai-incident-response-readiness-2026]]"
  - "[[sources/openai-frontier-governance-framework-2026]]"
  - "[[sources/ai-incident-escalation-criteria-2026]]"
---

# Research: Monitor ownership escalation ladder 边界

## 问题

第 6 层 monitor / eval / drift / freshness 信号出现后，如何稳定地分派给 owner、SLA、incident、release gate 或 risk owner，而不是变成无人处理的仪表盘噪声？

## 结论

Monitor ownership / escalation ladder 应主属第 7 层，因为它的核心不是“测什么”，而是“谁负责、多久响应、何时升级、谁有权行动”。它消费第 6 层证据，输出第 7 层组织动作。

稳定链路是：`monitor signal -> signal contract -> owner assignment -> response SLA -> escalation/elevation -> action -> closure evidence`。

## 关键发现

- NIST AI RMF Playbook 围绕 AI RMF Core 提出 ongoing monitoring、periodic review、roles/responsibilities 和 post-deployment monitoring plans 问题；这说明监控必须绑定组织责任，而不是只绑定指标。(Source: [[sources/nist-ai-rmf-playbook-monitoring-responsibility-2026]])
- NIST SP 800-61r3 把 escalation/elevation、triage、prioritization、senior leadership updates 和 recovery decision 放进 incident response profile；这给 AI 监控升级提供通用结构。(Source: [[sources/nist-sp800-61r3-incident-response-2025]])
- Google SRE 的 on-call 机制强调 primary/secondary rotation、分钟级响应、clear escalation paths 和 incident-management procedures；这把“监控信号”接到可执行的人。(Source: [[sources/google-sre-being-on-call-2016]])
- Google SRE incident management 把事故角色拆成 Incident Command、Operational Work、Communication、Planning，并要求 live incident state 和 clear handoff；AI 事故同样需要角色分离。(Source: [[sources/google-sre-managing-incidents-2016]])
- Microsoft AI incident response 指出 AI 事故有 taxonomy gaps、context-dependent severity、ambiguous root cause 和 telemetry gaps，因此需要 AI-specific observability、staged remediation、ownership assignments 和 escalation triggers。(Source: [[sources/microsoft-ai-incident-response-readiness-2026]])
- OpenAI Frontier Governance / Preparedness 把 capability thresholds、safeguards、Safety Advisory Group、leadership decision 和 board oversight 连起来；对 frontier risk，升级链必须包含高层和安全治理。(Source: [[sources/openai-frontier-governance-framework-2026]])
- AI incident escalation 研究提醒：如果升级必须等 confirmed harm、只看单个 incident、或阈值无法在压力下操作，会系统性漏升。(Source: [[sources/ai-incident-escalation-criteria-2026]])

## 分类决策

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层
- 上游：post-release monitor、eval breach、stale evidence、release card watch item、incident report、provider alert
- 下游：owner assignment、SLA、runbook、incident command、rollback/disable、risk elevation、postmortem、eval refresh

## 与相邻概念

- [[concepts/PostReleaseEvalDrift边界]] 负责发现发布证据是否 stale；本概念负责把信号送到 owner 和行动链。
- [[concepts/EvidenceFreshnessStaleProof边界]] 负责判断证据能否继续支持 claim；本概念负责谁刷新、谁隔离、谁升级。
- [[concepts/AIIncidentResponsePostmortem边界]] 处理已经升级为 incident 的事件；本概念覆盖 incident 前的 alert ownership 和升级触发。
- [[concepts/ModelReleaseRollbackGate边界]] 执行发布/回滚；本概念把 monitor breach 路由到 gate action。
- [[concepts/AISafetyOpsGovernance边界]] 是整体风险运行系统；本概念是其中的责任链组件。

## 工程落地

每条 AI 监控信号都应拥有：

- `signal_contract`：指标、scope、severity、阈值、freshness state、误报处理。
- `owner_chain`：monitor owner、artifact owner、service owner、risk owner、backup。
- `sla`：ack、triage、contain、communicate、close。
- `action_ladder`：watch、ticket、page、incident、executive elevation、external coordination。
- `authority`：哪些动作可由 on-call 执行，哪些需要 release owner、risk owner 或 leadership。
- `closure_evidence`：原因、处置、eval refresh、rollback、card update、postmortem action item。

## Open Questions

- LLM judge / monitor 自身漂移时，owner 应属于 eval 平台团队、产品团队还是 risk owner？
- 对第三方托管模型的 silent update，何时由 provider POC 参与，何时直接执行 route-away？
- 对高风险但未造成 harm 的 near miss，哪些场景必须 elevation 到 risk owner？

## 代表来源

- [[sources/nist-ai-rmf-playbook-monitoring-responsibility-2026]]
- [[sources/nist-sp800-61r3-incident-response-2025]]
- [[sources/google-sre-being-on-call-2016]]
- [[sources/google-sre-managing-incidents-2016]]
- [[sources/microsoft-ai-incident-response-readiness-2026]]
- [[sources/openai-frontier-governance-framework-2026]]
- [[sources/ai-incident-escalation-criteria-2026]]
