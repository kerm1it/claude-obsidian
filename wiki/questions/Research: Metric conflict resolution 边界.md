---
address: c-000492
type: research
title: "Research: Metric conflict resolution 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - research
  - evals
  - metrics
  - decision-threshold
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/MetricConflictResolution边界]]"
sources:
  - "[[sources/google-sre-embracing-risk-2016]]"
  - "[[sources/google-sre-error-budget-policy-2018]]"
  - "[[sources/google-sre-canarying-releases-2018]]"
  - "[[sources/nist-ai-rmf-risk-tolerance-2023]]"
  - "[[sources/openai-evals-business-framework-2025]]"
  - "[[sources/openai-preparedness-framework-2025]]"
  - "[[sources/microsoft-responsible-ai-standard-2022]]"
  - "[[sources/responsible-ai-tensions-tradeoffs-2023]]"
---

# Research: Metric conflict resolution 边界

## 问题

当一个 AI 变更出现“主指标提升，但安全、slice、SLO、成本、线上结果或风险指标变差”时，体系里应该如何排序、升级和行动？

## 结论

Metric conflict resolution 主属第 6 层，因为它解释的是证据之间的冲突；但它必须接到第 7 层 release gate、risk owner 和 escalation ladder。它的稳定职责是：按 metric role、risk tolerance、freshness、uncertainty 和 production correlation 决定 block、restrict、canary、refresh、rollback 或 residual risk acceptance。

## 关键发现

- Google SRE 的 error budget 把可靠性和发布速度的冲突制度化：在 SLO 内可以消耗风险预算，超出预算则改变发布策略。(Source: [[sources/google-sre-embracing-risk-2016]], [[sources/google-sre-error-budget-policy-2018]])
- Canary release 把“是否能发”拆成分阶段观察；当冲突来自不确定性或线上风险时，灰度比一次性全量更稳定。(Source: [[sources/google-sre-canarying-releases-2018]])
- NIST AI RMF 强调 risk tolerance、context、use case 和 severe harm；这支持 hard stop 和不可容忍风险不能被平均质量提升抵消。(Source: [[sources/nist-ai-rmf-risk-tolerance-2023]])
- OpenAI 的业务 eval 框架强调从 workflow、critical decisions 和 unacceptable behavior 出发；这支持先定义指标角色，再决定冲突优先级。(Source: [[sources/openai-evals-business-framework-2025]])
- OpenAI Preparedness Framework 用 High / Critical thresholds、safeguards report 和 leadership decision 连接能力证据与部署限制；这是 frontier risk 的 hard-stop 模式。(Source: [[sources/openai-preparedness-framework-2025]])
- Microsoft Responsible AI Standard 把 fairness、reliability/safety、privacy/security、transparency、accountability 变成工程要求和 impact assessment；这些原则之间有冲突时需要显式评审。(Source: [[sources/microsoft-responsible-ai-standard-2022]])
- Responsible AI trade-offs 研究指出伦理维度之间会有实际 tension；工程上需要记录 trade-off、stakeholder 和 decision rationale，不能假装所有指标同时最优。(Source: [[sources/responsible-ai-tensions-tradeoffs-2023]])

## 分类决策

- 主归属：6. 评估与可靠性层
- 组织接口：7. 产品与组织层
- 上游：eval portfolio、threshold、release card、online outcome、risk tolerance、freshness/stale proof
- 下游：conflict rule、metric quarantine、canary/hold/restrict、owner escalation、release card override、post-release monitor

## 冲突优先级

默认顺序：

1. Prohibited / intolerable / critical safety, privacy, security, tool, data breach。
2. Required safeguard、hard guardrail、contract/SLO。
3. Key slice regression、high-impact user segment、high-risk workflow。
4. Primary task metric、human/judge preference、offline product eval。
5. Online/business/cost/latency metric。
6. Diagnostic/exploratory metric。

## Open Questions

- 当 online metric 受混杂因素影响但 offline eval 清晰时，最小 canary 时长和样本量应如何定？
- 关键 slice regression 能否被 scope restriction 接受，还是必须全局 no-go？
- 高层 override 的 expiry 和复审 cadence 应按风险 tier 还是按证据 uncertainty 决定？

## 代表来源

- [[sources/google-sre-embracing-risk-2016]]
- [[sources/google-sre-error-budget-policy-2018]]
- [[sources/google-sre-canarying-releases-2018]]
- [[sources/nist-ai-rmf-risk-tolerance-2023]]
- [[sources/openai-evals-business-framework-2025]]
- [[sources/openai-preparedness-framework-2025]]
- [[sources/microsoft-responsible-ai-standard-2022]]
- [[sources/responsible-ai-tensions-tradeoffs-2023]]
