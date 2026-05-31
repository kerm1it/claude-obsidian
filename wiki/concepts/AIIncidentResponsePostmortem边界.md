---
address: c-000363
type: concept
title: "AI Incident Response / Postmortem 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - incident-response
  - postmortem
  - governance
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/AgentIdentityDelegation边界]]"
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/MultiProviderGovernance边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
  - "[[concepts/DataDeletionUnlearningImpact边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/PostReleaseEvalDrift边界]]"
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
  - "[[concepts/MonitorTabletopRunbookDrill边界]]"
  - "[[concepts/OverrideGovernanceResidualRiskAcceptance边界]]"
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
sources:
  - "[[sources/nist-sp800-61r3-incident-response-2025]]"
  - "[[sources/nist-sp800-37-risk-response-2018]]"
  - "[[sources/nist-sp800-84-tte-program-2006]]"
  - "[[sources/fema-hseep-exercise-evaluation-2020]]"
  - "[[sources/google-sre-being-on-call-2016]]"
  - "[[sources/google-sre-managing-incidents-2016]]"
  - "[[sources/microsoft-ai-incident-response-readiness-2026]]"
  - "[[sources/nist-ai-rmf-core-incident-response-2023]]"
  - "[[sources/oecd-defining-ai-incidents-2024]]"
  - "[[sources/oecd-ai-incidents-monitor-methodology-2026]]"
  - "[[sources/google-sre-emergency-response-2016]]"
  - "[[sources/google-sre-postmortem-culture-2016]]"
  - "[[sources/eu-ai-act-risk-management-post-market-2024]]"
  - "[[sources/nist-genai-profile-data-privacy-2024]]"
  - "[[sources/tensorflow-ml-metadata-2026]]"
  - "[[sources/google-machine-unlearning-challenge-2023]]"
  - "[[sources/google-cloud-deploy-automation-2026]]"
  - "[[sources/nist-deployed-ai-monitoring-challenges-2026]]"
  - "[[sources/nist-sp800-92r1-log-management-2023]]"
---

# AI Incident Response / Postmortem 边界

AI incident response / postmortem 是第 7 层产品与组织层的事故闭环：当第 6 层监控、eval、red-team、用户反馈、tool trace 或外部报告发现 AI 系统造成或可能造成伤害、越权、泄露、服务失效、错误决策或合规风险时，它规定如何分级、止血、沟通、取证、修复、复盘，并把结论反哺 eval、数据、工具、provider、产品和自我改进。

一句话：**incident response 负责让事故停止扩大；postmortem 负责让同类事故更难复发。**

## 主归属

- 主归属：7. 产品与组织层
- 上游输入：production monitoring、eval regression、user report、red-team finding、tool trace、provider incident、regulatory complaint
- 下游输出：severity、incident commander、mitigation、rollback、communications、evidence package、postmortem、action items、new evals
- 质量输入：6. 评估与可靠性层
- 反哺层级：2. 模型构建层、4. 上下文与知识层、5. Agent 系统层、6. 评估与可靠性层、8. 自我改进与前沿层

## 稳定链路

```text
signal / alert / report
    -> triage and severity
    -> incident commander and owner
    -> containment, rollback, disable, or human override
    -> evidence preservation and stakeholder communication
    -> root/contributing cause analysis
    -> blameless postmortem and action items
    -> new evals, monitors, policies, data fixes, tool gates, provider review, or model changes
```

## AI 事故类型

| 类型 | 例子 | 常见反哺 |
|---|---|---|
| 可靠性事故 | 大面积 hallucination、routing 漂移、模型升级回归 | eval、router gate、release gate |
| 安全事故 | prompt injection、越权工具调用、secrets 泄露 | tool permission、identity、sandbox |
| 数据事故 | 未授权数据进入 memory/eval/training、RAG 泄露 | data rights、lineage、retention |
| 伤害事故 | 歧视、误导、高影响错误建议、基本权利影响 | risk register、human oversight、policy |
| Provider 事故 | 第三方模型/区域/日志/SLA 失效 | provider policy、fallback、vendor review |
| 自我改进事故 | 自动改 prompt/skill/eval 后质量下降 | diff gate、rollback、hold-out eval |

## 事故闭环产物

| 产物 | 作用 |
|---|---|
| Incident severity rubric | 定义用户影响、伤害、数据、合规、可用性和外部报告等级 |
| Incident commander / owner | 事故期间的单一协调责任和升级链 |
| Containment playbook | 暂停模型、回滚 prompt、禁用工具、切 provider、降级到人工 |
| Evidence package | trace、prompt、model/tool/provider version、logs、policy decision、影响范围 |
| Communication plan | 内部状态、用户通知、监管通知、客户支持和外部说明 |
| Blameless postmortem | 记录时间线、影响、处置、促成因素、遗漏信号和 action items |
| Regression package | 将事故复现为 eval、red-team case、monitor、data quality check 或 policy test |

## 与相邻概念区别

- 与 [[concepts/AISafetyOpsGovernance边界]]：safety ops 是完整风险运行系统；incident response/postmortem 是事故发生后的闭环子系统。
- 与 eval：eval 发现或复现问题；incident response 负责止血、取证、沟通和恢复。
- 与 monitoring：monitoring 提供信号；incident response 决定是否升级、谁负责和如何处置。
- 与 [[concepts/MonitorOwnershipEscalationLadder边界]]：monitor ownership 规定告警 owner、SLA、升级路径和预授权动作；incident response 是升级为事故后的角色、止血、沟通和复盘。
- 与 [[concepts/MonitorTabletopRunbookDrill边界]]：incident response 处理真实事故；tabletop/drill 在事故前验证 playbook、role handoff、evidence package、comms 和 rollback 是否能运作。
- 与 [[concepts/ToolRiskPermissioning边界]]：tool permissioning 阻止高风险动作；事故复盘会反向修改风险层、approval 和 sandbox。
- 与 [[concepts/AgentIdentityDelegation边界]]：identity/delegation 提供 actor 和授权证据；事故流程用它还原责任链。
- 与 [[concepts/MultiProviderGovernance边界]]：provider governance 管供应商资格；provider 事故会触发 fallback、vendor review 和 policy change。
- 与 [[concepts/RewardHackingEvalOverfitting边界]]：postmortem 要检查指标是否掩盖真实伤害，避免把事故错误地归类为“eval 通过”。
- 与 [[concepts/DatasetLineageProvenanceGraph边界]]：事故 evidence package 需要 lineage 还原哪些数据、prompt、RAG chunk、memory、tool trace、model/provider version 和 eval/release decision 参与了事故。
- 与 [[concepts/DataDeletionUnlearningImpact边界]]：事故可能触发删除、隔离、provider deletion、model replacement 或 unlearning；postmortem 要把这些动作变成 owner、due date、verification 和 regression eval。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：incident response 执行 rollback、disable、route-around 或 provider fallback；postmortem 把事故样本和触发条件回填到下一次 release gate。
- 与 [[concepts/OverrideGovernanceResidualRiskAcceptance边界]]：incident response 处理 override 失效或残余风险成真的事故；postmortem 要判断 override 是否过期、monitor 是否缺失、approval authority 是否错误。
- 与 [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]：incident response 需要保全 trace、prompt、model/tool/provider version 和决策证据；audit packet lifecycle 定义这些事故证据如何长期保留、检索、legal hold 和销毁。
- 与 [[concepts/PostReleaseEvalDrift边界]]：post-release drift 是事故前的早期信号和证据 stale 检测；一旦漂移造成 harm、越权、泄露或重大服务失败，就升级为 incident response。

## 评估方式

- Detection time：从事故开始到被检测的时间。
- Triage accuracy：严重度是否准确，是否漏报、误报或延迟升级。
- Mitigation time / recovery time：止血、回滚、禁用和恢复用时。
- Evidence completeness：是否能重建 prompt、context、model、tool、identity、provider、policy 和用户影响。
- Action item closure：复盘 action item 是否有 owner、due date、复测和证据。
- Recurrence rate：同类事故是否复发，复发原因是否解释清楚。
- Regression conversion：事故是否转化为 eval、monitor、red-team case 或 policy test。
- Communication quality：受影响用户、内部团队、监管方和客户支持是否获得及时准确信息。

## 过时风险

- 具体监管时限、模板和报告对象会变化；稳定结构是 detect → triage → contain → preserve evidence → communicate → postmortem → regression。
- AI 事故形态会随 agent 权限、多模态、provider、memory 和 self-improvement 扩大；事故 taxonomy 要可更新，但不新增顶层。
- Postmortem 容易退化成文档剧场；必须绑定 action item、owner、eval、monitor 和 release gate。

## 一句话归类

AI incident response / postmortem 主属第 7 层，是第 6 层监控/eval 发现风险后进入组织止血、复盘、问责、沟通和改进的事故闭环；它不是新顶层，而是 AI safety ops 的运行子系统。
