---
address: c-000459
type: concept
title: "Safety Case / Assurance Case 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - safety-case
  - assurance-case
  - governance
  - evals
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/IntolerableRiskThresholdStopRule边界]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
  - "[[concepts/PostReleaseEvalDrift边界]]"
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
  - "[[concepts/OverrideGovernanceResidualRiskAcceptance边界]]"
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
sources:
  - "[[sources/safety-cases-advanced-ai-systems-2024]]"
  - "[[sources/nist-sp800-37-risk-response-2018]]"
  - "[[sources/aisi-frontier-ai-safety-case-cyber-2024]]"
  - "[[sources/big-argument-ai-safety-cases-2025]]"
  - "[[sources/structured-safety-case-ai-systems-2026]]"
  - "[[sources/nist-ai-rmf-1-0-2023]]"
  - "[[sources/openai-preparedness-framework-2025]]"
  - "[[sources/anthropic-responsible-scaling-policy-v3-2026]]"
  - "[[sources/deepmind-frontier-safety-framework-2025]]"
  - "[[sources/nist-deployed-ai-monitoring-challenges-2026]]"
  - "[[sources/slsa-provenance-v1-2-2026]]"
  - "[[sources/safety-case-maintenance-slr-2021]]"
  - "[[sources/dynamic-safety-cases-changing-world-2025]]"
  - "[[sources/iso-15489-records-management-2016]]"
---

# Safety Case / Assurance Case 边界

Safety case / assurance case 是第 7 层产品与组织层的高风险发布论证边界：它把第 6 层 eval、red-team、capability assessment、offline/online correlation、release card、safeguard evidence、incident evidence 和 monitoring plan，组织成一个可审查的 claims-arguments-evidence 包，用来说明系统在特定上下文中的风险是否可接受。

一句话：**eval 给证据，release card 给决策摘要，safety case 给“为什么这些证据足以支持接受残余风险”的完整论证。**

## 主归属

- 主归属：7. 产品与组织层
- 证据接口：6. 评估与可靠性层
- 上游输入：risk model、hazard taxonomy、system scope、capability eval、red-team、release card、online monitor、safeguard assessment、incident/postmortem、residual risk
- 下游输出：assurance argument、review package、approval/deny decision、required safeguards、monitoring obligation、counterevidence register、case refresh trigger
- 发布接口：[[concepts/ModelReleaseRollbackGate边界]]

## 稳定链路

```text
AI system / use case / deployment scope
    -> top claim: acceptable risk for this context
    -> risk model and stakeholders: hazards, harms, misuse, failure modes, uncertainty
    -> subclaims: inability, control, trustworthiness, safeguards, monitoring, governance
    -> evidence: evals, red-team, benchmarks, field data, audits, lineage, expert review
    -> argument structure: claims -> arguments -> evidence, assumptions, limits, defeaters
    -> independent review: residual risk, counterevidence, stop rules, exception authority
    -> decision: deploy, restrict, pause, add safeguards, external review, or reject
    -> maintain case when model, prompt, tool, provider, data, users, law, or incidents change
```

## Safety Case 字段

| 字段 | 回答的问题 | 常见缺口 |
|---|---|---|
| Top claim | 为什么这个系统在这个上下文中风险可接受？ | 只有证据列表，没有结论 |
| Scope/context | 哪个模型、版本、用例、人群、工具和部署范围？ | 把论证外推到未覆盖场景 |
| Risk model | 主要 harm、threat、hazard 和 misuse 路径是什么？ | 风险 taxonomy 不完整 |
| Argument pattern | 用 inability、control、trustworthiness、safeguard 还是 operational monitoring 论证？ | 证据堆叠但逻辑不清 |
| Evidence map | eval、red-team、monitoring、audit、expert review 支持哪个 claim？ | 证据无法追溯到 claim |
| Uncertainty / defeaters | 哪些反证、盲区、假设失效会推翻论证？ | 没有 counterevidence register |
| Residual risk | 仍存在什么风险，谁接受，何时复审？ | 风险接受无 owner |
| Maintenance trigger | 什么变化会使 case stale？ | 模型/工具变化后仍复用旧 case |

## 与相邻概念区别

- 与 [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]：release card 是一次变更的轻量证据摘要；safety case 是高风险系统的完整论证包。
- 与 [[concepts/IntolerableRiskThresholdStopRule边界]]：stop rule 定义哪些条件必须 no-go；safety case 论证未触发 hard stop 后，残余风险为什么可接受。
- 与 [[concepts/OverrideGovernanceResidualRiskAcceptance边界]]：safety case 论证残余风险为什么可接受；override governance 记录谁接受、期限、条件、monitor、rollback 和撤销路径。
- 与 [[concepts/AISafetyOpsGovernance边界]]：safety ops 是组织运行系统；safety case 是该系统在重大发布或高风险用例上的审查 artifact。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：release gate 执行动作；safety case 为高风险 gate 提供论证和批准依据。
- 与 [[concepts/OfflineOnlineEvalCorrelation边界]]：correlation 校准离线证据是否预测线上 outcome；safety case 消费这些校准结果作为证据强度说明。
- 与 [[concepts/PostReleaseEvalDrift边界]]：post-release eval drift 提供 case refresh trigger，指出哪些 evidence、assumption、monitor 或 deployment constraint 已经过期。
- 与 [[concepts/EvidenceFreshnessStaleProof边界]]：safety case 需要知道每条 evidence 和 assumption 是否仍 fresh；stale proof 是 case maintenance 的证据底座。
- 与 [[concepts/EvidenceAttestationSignedEvalArtifact边界]]：safety case 组织 claims-arguments-evidence；attestation 保证引用的 eval、model、prompt、judge、container 和 release evidence 能追到可验证签名和 subject digest。
- 与 [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]：safety case 组织 claim/argument/evidence；audit packet lifecycle 负责这些 evidence 的保存、检索、legal hold、重验和退役。
- 与 合规清单：合规清单证明覆盖了要求；assurance case 证明 claims、evidence、uncertainty 和残余风险之间的逻辑关系。

## 工程实践

1. 先写 top claim 和 context，不从证据列表开始。
2. 使用 CAE / GSN 风格：claim、argument、evidence、assumption、context、justification、defeater 分开写。
3. 每个 evidence 都要有版本、owner、freshness、scope、uncertainty 和关联 claim。
4. 明确 argument pattern：inability、control、trustworthiness、safeguards、monitoring、human oversight 或 combination。
5. 记录 counterevidence：失败 eval、red-team bypass、judge drift、线上 incident、coverage gap、法规模糊。
6. 对 high uncertainty / high severity 的 claim，默认要求 external review、restricted deployment 或 stronger safeguards。
7. 把 safety case 绑定 release gate 和 incident response：case 失败时能 pause、rollback、restrict 或 reopen review。
8. 把 case 维护当成生命周期任务：模型、prompt、tool、provider、data、用户分布、法律或事故变化后刷新。

## 评估方式

- Claim coverage：关键风险、stakeholder 和部署场景是否都有 claim。
- Evidence traceability：每条证据是否能追溯到 eval run、dataset、model version、review 和 owner。
- Defeater coverage：反例、盲区、uncertainty 和 counterevidence 是否被显式处理。
- Review quality：是否有独立审查、专家意见、外部 review 或 red-team challenge。
- Freshness：case 是否随 model/provider/prompt/tool/data/法律/incident 变化更新。
- Decision auditability：审批、限制、例外和 residual risk acceptance 是否可审计。
- Post-release validation：case 预测的风险是否和线上监控、事故、投诉和 rollback 记录一致。

## 过时风险

- AI 系统动态变化使传统 safety case 容易 stale；必须绑定 artifact identity、monitoring、change trigger 和 review cadence。
- 强模型会让能力、工具副作用和社会技术上下文快速变化；case 不能只依赖一次 benchmark 或一次 red-team。
- 如果组织把 safety case 当作合规文档而不连接 release gate、stop rule 和 incident response，它会失去工程约束力。

## 一句话归类

Safety case / assurance case 主属第 7 层，是高风险 AI 系统把第 6 层证据组织成可审查发布论证的治理边界；它不新增顶层，而是把 eval、risk threshold、release card、monitoring 和 residual risk acceptance 串成一个完整决策包。
