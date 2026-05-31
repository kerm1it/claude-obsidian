---
address: c-000439
type: concept
title: "Intolerable Risk Threshold / Stop Rule 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - governance
  - risk-threshold
  - stop-rule
  - safety
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/MetricConflictResolution边界]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/SafetyCaseAssuranceCase边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
  - "[[concepts/ProductionContractCompatibilityTest边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/OverrideGovernanceResidualRiskAcceptance边界]]"
  - "[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]"
sources:
  - "[[sources/google-sre-embracing-risk-2016]]"
  - "[[sources/ai-incident-escalation-criteria-2026]]"
  - "[[sources/nist-sp800-37-risk-response-2018]]"
  - "[[sources/nist-ai-rmf-risk-tolerance-2023]]"
  - "[[sources/nist-ai-rmf-1-0-2023]]"
  - "[[sources/openai-preparedness-framework-2025]]"
  - "[[sources/anthropic-responsible-scaling-policy-v3-2026]]"
  - "[[sources/deepmind-frontier-safety-framework-2025]]"
  - "[[sources/eu-ai-act-prohibited-practices-2024]]"
  - "[[sources/microsoft-responsible-ai-standard-2022]]"
  - "[[sources/iso-iec-42001-ai-management-system-2023]]"
  - "[[sources/nist-sp800-137-continuous-monitoring-2011]]"
---

# Intolerable Risk Threshold / Stop Rule 边界

Intolerable risk threshold / stop rule 是第 7 层产品与组织层的高风险停机边界：它把第 6 层 eval、red-team、capability assessment、incident、法律要求和 safeguard evidence，翻译成“必须暂停、禁止、限制、升级 safeguard、外部审查或回滚”的组织决策规则。

一句话：**普通阈值决定能不能发布；不可容忍风险阈值决定什么时候不能用收益、平均分或商业压力抵消风险。**

## 主归属

- 主归属：7. 产品与组织层
- 上游输入：capability assessment、risk taxonomy、eval/red-team、incident、law/policy、production monitoring、safeguard assessment、residual risk
- 下游输出：stop / pause / block / restrict / rollback / external-review decision、required safeguards、risk acceptance record、exception denial、public or internal risk report
- 证据接口：6. 评估与可靠性层
- 发布接口：[[concepts/ModelReleaseRollbackGate边界]]
- 事故接口：[[concepts/AIIncidentResponsePostmortem边界]]

## 稳定链路

```text
AI system / capability / use case / deployment scope
    -> harm taxonomy and stakeholder/legal requirements
    -> layer 6 measurement: eval, red-team, incident, monitoring, uncertainty, safeguard effectiveness
    -> risk tolerance: acceptable, tolerable with safeguards, intolerable / prohibited
    -> stop rule: do not train, do not deploy, restrict scope, pause, rollback, external review, or require stronger safeguards
    -> owner decision: accountable authority, evidence package, exception policy, communication
    -> monitor residual risk and refresh threshold when capability, context, law, or safeguards change
```

## 阈值类型

| 阈值类型 | 触发条件 | 典型动作 |
|---|---|---|
| Legal prohibition | 法规明确禁止的用途或实践 | block / do not offer |
| Severe capability threshold | 模型达到 CBRN、cyber、autonomy、manipulation 等高危能力 | stronger safeguards / external review / restrict |
| Safeguard inadequacy | 能力已达阈值，但安全、部署或安全保障措施不足 | pause deployment / no-go |
| Incident stop rule | 生产中发生 severe harm、near miss 或重复高危信号 | rollback / disable / incident response |
| Hard guardrail breach | 隐私、权限、高影响动作、未授权工具、critical SLO 破线 | block release / human escalation |
| Residual risk rejection | 剩余风险超过组织或社会可接受范围 | do not accept exception |
| Ambiguity precaution | 风险证据不确定但潜在伤害极高 | limited deployment / more evidence / external review |

## 与相邻概念区别

- 与 [[concepts/EvalResultInterpretationDecisionThreshold边界]]：decision threshold 解释 eval 分数；本页定义哪些风险不能被平均质量、收益或灰区例外抵消。
- 与 [[concepts/MetricConflictResolution边界]]：metric conflict resolution 处理多指标冲突；本页是最高优先级的 hard stop，不允许被 primary、online 或 business metric 抵消。
- 与 [[concepts/OverrideGovernanceResidualRiskAcceptance边界]]：本页定义不能 override 的 hard no-go；override governance 只处理未触发 hard stop 后可被 owner 接受的残余风险。
- 与 [[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]：本页定义 hard stop 和 no-go；override debt dashboard 监控 near miss、bypass attempt 和 hard-stop pressure 是否上升。
- 与 [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]：release card 把 hard stop、residual risk、uncertainty 和 no-go 条件显式暴露给决策者；本页定义这些条件的组织含义。
- 与 [[concepts/SafetyCaseAssuranceCase边界]]：safety case 论证残余风险为什么可接受；本页定义哪些条件使论证不能通过或必须外部审查。
- 与 [[concepts/AISafetyOpsGovernance边界]]：safety ops 是完整风险运行系统；本页是其中的不可容忍阈值和 stop rule 组件。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：release gate 执行发布、灰度、回滚；本页给 gate 提供 hard stop / no-go / external-review 条件。
- 与 [[concepts/MonitorOwnershipEscalationLadder边界]]：本页定义哪些信号必须 stop、pause、restrict 或 external review；monitor ownership 决定这些信号如何被升级到有权行动的人。
- 与 [[concepts/ProductionContractCompatibilityTest边界]]：production contract 定义产品行为契约；本页定义契约之外的高危能力、法律禁止和 residual risk 边界。
- 与 [[concepts/RewardHackingEvalOverfitting边界]]：reward hacking 是风险被指标绕过；本页要求某些 guardrail breach 不能被总体分数提升抵消。
- 与法律合规：法律 prohibition 是一类 hard stop；但组织还需要为未立法的 frontier capability 和高影响 use case 定义内部 stop rule。

## 工程实践

1. 写 risk taxonomy：CBRN、cyber、autonomy、manipulation、privacy、minor safety、high-impact decision、biometric、tool side effect、model-weight theft。
2. 为每类风险定义触发器：capability threshold、red-team severe failure、production incident、monitoring breach、safeguard assessment failure、legal prohibition。
3. 每个触发器绑定动作：no-go、scope restriction、additional safeguard、human review、external review、canary only、rollback、disable。
4. 明确 evidence standard：需要哪些 eval、专家 deep dive、confidence、slice、production signal 或 safety case。
5. 明确 owner 和 authority：谁能接受 residual risk，谁不能 override，例外期限和复审条件是什么。
6. 对 high uncertainty / high severity 用 precautionary rule：证据不充分时先限制或暂停，而不是默认放行。
7. 记录 risk report / safeguards report：capability、threat model、mitigation、residual risk、decision rationale、review date。
8. 把 stop rule 接入 release gate、incident playbook、provider governance、tool permissioning 和 self-improvement gate。

## 评估方式

- Threshold coverage：关键风险类别是否都有可测试触发器和对应动作。
- Detection latency：风险从出现到触发 stop rule 的时间。
- False pass：高危系统被放行后出现 severe incident 或 near miss 的比例。
- False stop：错误阻断导致的机会成本和复审质量。
- Safeguard readiness：达到能力阈值前，required safeguards 是否已验证有效。
- Exception quality：例外是否有 authority、期限、缓解、监控和复审。
- Residual risk audit：被接受的 residual risk 是否和政策、法律、用户承诺和外部证据一致。

## 过时风险

- 具体风险类别和法规会变化，但“风险证据 → 可接受/可容忍/不可容忍 → stop rule → owner decision → monitor residual risk”的链路稳定。
- Frontier capability threshold 难免有 ambiguity；工程上要保留 precautionary rule、外部审查和 threshold refresh，而不是假装 eval 给出绝对答案。
- 如果组织 KPI 能 override stop rule，治理会退化成文档；hard stop 必须绑定真实发布、训练、路由和供应商控制面。

## 一句话归类

Intolerable risk threshold / stop rule 主属第 7 层，是第 6 层风险证据进入组织 no-go、pause、restrict、rollback 和外部审查的高风险停机边界；它保证某些风险不能被平均分、商业收益或灰区例外稀释。
