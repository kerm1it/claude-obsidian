---
address: c-000364
type: synthesis
title: "Research: AI incident response postmortem 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - incident-response
  - postmortem
status: developing
related:
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/AgentIdentityDelegation边界]]"
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/MultiProviderGovernance边界]]"
sources:
  - "[[sources/nist-ai-rmf-core-incident-response-2023]]"
  - "[[sources/oecd-defining-ai-incidents-2024]]"
  - "[[sources/oecd-ai-incidents-monitor-methodology-2026]]"
  - "[[sources/google-sre-emergency-response-2016]]"
  - "[[sources/google-sre-postmortem-culture-2016]]"
  - "[[sources/eu-ai-act-risk-management-post-market-2024]]"
  - "[[sources/nist-genai-profile-data-privacy-2024]]"
---

# Research: AI incident response postmortem 边界

## Overview

本轮研究 AI incident response / postmortem：AI 系统上线后出现真实伤害、严重错误、越权、泄露、provider 故障或合规风险时，组织如何检测、止血、沟通、取证、复盘并反哺系统。结论是：它主属第 7 层产品与组织层，是 [[concepts/AISafetyOpsGovernance边界]] 的事故闭环；第 6 层提供监控/eval/red-team 证据，第 7 层负责 owner、severity、rollback、communication、postmortem 和 action item。

## Key Findings

- NIST AI RMF Core 把 incident response、recovery、change management、communication 和 continual improvement 放在 post-deployment risk management 中；这支持把 AI incident response 放在第 7 层运行系统，而不是单次 eval。(Source: [[sources/nist-ai-rmf-core-incident-response-2023]])
- OECD 将 AI incident 定义为 AI 系统的开发、使用或故障直接或间接导致健康、关键基础设施、人权/法律义务、财产/社区/环境等实际伤害；AI hazard 是可能导致此类事故的潜在危险。(Source: [[sources/oecd-defining-ai-incidents-2024]])
- OECD AIM 通过公开新闻事件跟踪 incidents/hazards，同时明确这些数据只是证据起点，不能替代组织自己的监控、报告和验证。(Source: [[sources/oecd-ai-incidents-monitor-methodology-2026]])
- Google SRE emergency response 强调事故流程、回滚、out-of-band communication、备用工具和演练；这些通用工程实践可以迁移到 AI 系统，但 AI 还要加 model/context/tool/provider/data evidence。(Source: [[sources/google-sre-emergency-response-2016]])
- Google SRE postmortem culture 明确 postmortem 是学习机制，不是惩罚；触发条件包括用户可见降级、数据丢失、人工介入、恢复时间超阈值和监控失败。(Source: [[sources/google-sre-postmortem-culture-2016]])
- EU AI Act 对 high-risk AI systems 要求 post-market monitoring，并对 serious incidents 设定报告义务；这把生产事故从内部工程流程扩展为可能的监管义务。(Source: [[sources/eu-ai-act-risk-management-post-market-2024]])

## 稳定归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层、5. Agent 系统层、8. 自我改进与前沿层
- 上游输入：monitoring alerts、eval regressions、user reports、red-team findings、tool trace、provider status、regulatory complaint
- 下游输出：severity、owner、containment、rollback、evidence package、communications、postmortem、action items、new evals

## 稳定链路

```text
signal / alert / report
    -> triage and severity
    -> incident commander and accountable owner
    -> containment / rollback / disable / human override
    -> evidence preservation and stakeholder communication
    -> root and contributing cause analysis
    -> blameless postmortem
    -> action items and regression conversion
```

## AI 特有差异

| 普通软件事故 | AI 事故额外要记录 |
|---|---|
| 版本、日志、配置、依赖 | model version、prompt/context、RAG docs、memory state、tool call、provider、eval baseline |
| 服务错误率和延迟 | false confidence、harmful output、policy bypass、bias、data leakage、autonomy side effect |
| 回滚代码或配置 | 回滚模型、prompt、router、skill、memory、provider、tool permission 或 self-improvement diff |
| postmortem action | 新增 eval、red-team case、monitor、data quality check、approval gate、training candidate |

## 工程实践

1. 给 AI 系统建 incident severity rubric：伤害、隐私、越权、合规、可用性、经济影响、受影响人数。
2. 每个高风险系统要有 owner、incident commander 轮值、fallback 和 rollback playbook。
3. 事故期间优先 containment：禁用工具、切 provider、降低 autonomy、暂停 memory write、回滚 prompt/model/router。
4. 保留 evidence package：trace、prompt、context、model/tool/provider version、policy decision、identity grant、用户影响范围。
5. Postmortem 必须 blameless，但 action items 要有 owner、due date 和复测证据。
6. 每个事故至少尝试转成一个 regression eval、monitor、red-team case 或 policy test。
7. 对 serious incident 判断是否触发客户通知、监管报告或第三方 provider escalation。

## 评估方式

- MTTD / MTTR / containment time。
- Severity calibration：严重度是否匹配真实影响。
- Evidence completeness：是否能复现或解释事故。
- Action item closure rate。
- Recurrence rate。
- Regression conversion rate。
- Regulatory/customer communication timeliness。
- Release gate improvement：事故后 gate 是否真的拦住同类风险。

## Contradictions

没有发现直接矛盾。主要边界差异是：SRE 传统事故流程关注服务可靠性和学习机制；AI 风险框架关注社会技术伤害、监管报告和全生命周期治理。合并后的稳定框架是：用 SRE 的 detect/contain/postmortem 方法管理运行过程，用 AI RMF/OECD/EU AI Act 定义 AI-specific severity、harm、evidence 和外部报告边界。

## Open Questions

- 如何把“harm severity”与工程 SLO severity 合并成一个可执行 incident rubric？
- 多 agent 事故中，责任链应按 agent identity、用户授权、工具 owner 还是产品 owner 划分？
- 自动 self-improvement 造成事故时，postmortem action 是否应该优先改 eval gate、diff gate 还是训练数据？

## Sources

- [[sources/nist-ai-rmf-core-incident-response-2023]]：NIST AI RMF Core incident response
- [[sources/oecd-defining-ai-incidents-2024]]：OECD AI incident definitions
- [[sources/oecd-ai-incidents-monitor-methodology-2026]]：OECD AIM methodology
- [[sources/google-sre-emergency-response-2016]]：Google SRE emergency response
- [[sources/google-sre-postmortem-culture-2016]]：Google SRE postmortem culture
- [[sources/eu-ai-act-risk-management-post-market-2024]]：EU AI Act post-market monitoring / serious incidents
- [[sources/nist-genai-profile-data-privacy-2024]]：NIST GenAI Profile
