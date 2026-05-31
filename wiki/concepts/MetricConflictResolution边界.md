---
address: c-000491
type: concept
title: "Metric Conflict Resolution 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - evals
  - metrics
  - decision-threshold
  - governance
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/EvalPortfolioMetricHierarchy边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/IntolerableRiskThresholdStopRule边界]]"
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
  - "[[concepts/MonitorTabletopRunbookDrill边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/OverrideGovernanceResidualRiskAcceptance边界]]"
  - "[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]"
  - "[[concepts/DashboardCalibrationGovernanceMetricQuality边界]]"
sources:
  - "[[sources/google-sre-embracing-risk-2016]]"
  - "[[sources/google-sre-error-budget-policy-2018]]"
  - "[[sources/nist-sp800-37-risk-response-2018]]"
  - "[[sources/google-sre-canarying-releases-2018]]"
  - "[[sources/nist-ai-rmf-risk-tolerance-2023]]"
  - "[[sources/openai-evals-business-framework-2025]]"
  - "[[sources/openai-preparedness-framework-2025]]"
  - "[[sources/microsoft-responsible-ai-standard-2022]]"
  - "[[sources/responsible-ai-tensions-tradeoffs-2023]]"
  - "[[sources/ncsc-effective-steps-cyber-exercise-creation-2026]]"
  - "[[sources/google-sre-good-housekeeping-error-budget-debt-2018]]"
  - "[[sources/dora-software-delivery-performance-metrics-2026]]"
---

# Metric Conflict Resolution 边界

Metric conflict resolution 是第 6 层评估与可靠性层的证据冲突解释边界：当 hard stop、guardrail、primary metric、slice metric、online outcome、business metric、SLO、cost/latency 或 judge/human 信号互相矛盾时，它定义优先级、升级规则和行动，而不是用一个总分掩盖冲突。

一句话：**指标冲突不是平均一下就结束；要先看指标角色，再看风险等级、证据可信度和谁有权接受残余风险。**

## 主归属

- 主归属：6. 评估与可靠性层
- 组织接口：7. 产品与组织层
- 上游输入：eval portfolio、metric roles、threshold、uncertainty、freshness、slice、online outcome、risk tolerance、release card
- 下游输出：conflict decision、precedence rule、gray-zone review、metric quarantine、canary/restrict/rollback、owner escalation、card update
- 执行接口：[[concepts/ModelReleaseRollbackGate边界]]、[[concepts/MonitorOwnershipEscalationLadder边界]]

## 稳定链路

```text
metric conflict detected
    -> classify metric roles: hard stop, guardrail, primary, slice, online, SLO, diagnostic
    -> check evidence quality: freshness, uncertainty, sample size, judge health, production correlation
    -> apply precedence: prohibited/intolerable risk > critical guardrail > contract/SLO > key slice > primary > business/cost > diagnostic
    -> choose action: block, restrict, canary, hold, investigate, quarantine metric, refresh eval, rollback, or accept residual risk
    -> escalate owner if override, gray zone, high-risk slice, or residual risk acceptance is needed
    -> record conflict, rationale, owner, expiry, post-release monitor, and regression update
```

## 冲突类型

| 冲突 | 含义 | 默认动作 |
|---|---|---|
| Primary up / guardrail down | 主任务更好，但安全、隐私、权限、合规或 SLO 变差 | 阻断、限制范围、补 safeguard |
| Average up / slice down | 总体提升但关键人群、语言、风险场景或工具路径退化 | slice no-go、局部限制、补样本 |
| Offline up / online down | 离线 eval 好，但线上投诉、人工接管、A/B 或 SLO 变差 | 降低 offline trust、canary hold、刷新 eval |
| Judge disagreement | LLM judge、人类、rubric 或多裁判互相冲突 | human adjudication、judge quarantine |
| Fresh evidence vs stale evidence | 新证据和旧 release card / safety evidence 冲突 | 旧证据降权或失效，更新 card/case |
| Quality up / cost-latency bad | 质量提升但超出成本、延迟或吞吐预算 | router/cascade、scope limit、SLO review |
| Business up / risk up | 转化率、留存或效率提升，但风险指标变坏 | risk owner review，不允许 KPI 抵消 hard stop |

## 优先级规则

1. 法律禁止、不可容忍风险、critical data/security/tool breach 一票否决。
2. Hard stop 和 required safeguard 不能被平均质量、ROI、成本节省或业务指标抵消。
3. Guardrail 破线默认阻断或灰区，除非有明确 risk owner、期限、缓解和 post-release monitor。
4. 关键 slice regression 优先于总体平均提升；发布范围应按 slice 限制。
5. Online outcome 与 offline eval 冲突时，不直接否定离线指标，而是降 trust tier、检查混杂因素并更新 eval。
6. Diagnostic / exploratory metric 不能单独放行或阻断，只能解释原因或进入研究队列。
7. 任何 override 必须写入 release card：谁批准、为什么、多久复审、用哪些监控保护。

## 与相邻概念区别

- 与 [[concepts/EvalPortfolioMetricHierarchy边界]]：portfolio 定义指标角色；本页定义角色冲突时的优先级和行动。
- 与 [[concepts/EvalResultInterpretationDecisionThreshold边界]]：threshold 判断单个指标是否过线；本页处理多个已解释指标之间互相矛盾。
- 与 [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]：release card 记录冲突、灰区、override 和 owner；本页提供冲突决策规则。
- 与 [[concepts/IntolerableRiskThresholdStopRule边界]]：stop rule 是最高优先级的 hard stop；metric conflict 不允许绕过它。
- 与 [[concepts/OverrideGovernanceResidualRiskAcceptance边界]]：本页决定冲突下应 block、restrict、canary、hold 或 escalate；override governance 记录例外批准、残余风险、期限、monitor 和 rollback。
- 与 [[concepts/OfflineOnlineEvalCorrelation边界]]：offline/online correlation 判断预测关系；本页规定预测关系冲突时如何降权、canary 或刷新。
- 与 [[concepts/MonitorOwnershipEscalationLadder边界]]：本页决定冲突动作；monitor ownership 把冲突升级给正确 owner 和 SLA。
- 与 [[concepts/MonitorTabletopRunbookDrill边界]]：本页写冲突规则；tabletop/drill 用冲突 injects 验证 hard stop、guardrail、business KPI 和 override 路径是否被正确执行。
- 与 [[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]：本页处理一次指标冲突如何行动；override debt dashboard 识别同类冲突是否长期通过例外被正常化。
- 与 [[concepts/DashboardCalibrationGovernanceMetricQuality边界]]：本页决定冲突时该怎么行动；dashboard calibration 先检查冲突涉及的指标定义、数据质量、freshness、coverage 和 action precision 是否足以支撑这个行动。
- 与 [[concepts/RewardHackingEvalOverfitting边界]]：reward hacking 是冲突被隐藏或被单一指标钻空子；本页要求冲突显式化。

## 工程实践

1. 在 eval portfolio 里给每个指标标注 role、owner、freshness、trust tier、action authority 和 conflict rule。
2. 禁止加权平均吞掉 hard stop、guardrail 或关键 slice regression。
3. 预定义 conflict matrix：每种冲突的默认动作、需要谁批准、何时进入 incident 或 release gate。
4. 对灰区使用 canary、shadow、human review、more sampling、paired eval、专家 adjudication 或 limited rollout。
5. 对冲突指标检查证据质量：样本量、CI、flakiness、judge health、freshness、线上相关性和数据污染。
6. 业务指标、成本和速度只能在风险可接受边界内优化；不能作为 hard stop override 的理由。
7. 每次 override 都要有 expiry、monitor、rollback trigger 和复审任务。

## 评估方式

- Conflict coverage：常见冲突是否都有预定义 matrix 和 owner。
- Hard-stop escape：hard stop 或 guardrail 被平均分/业务指标绕过的次数。
- Slice regression escape：关键 slice 退化但仍发布的次数。
- Override quality：override 是否有 owner、期限、缓解、监控和复审证据。
- False pass / false stop：冲突规则是否减少坏候选放行和好候选误杀。
- Conflict latency：从发现冲突到行动决策的时间。
- Post-release surprise：发布后出现的冲突是否已在 release card 中预期。

## 过时风险

- 具体指标会变化，但 hard stop / guardrail / primary / slice / online / diagnostic 的角色分层稳定。
- 强模型可能让平均能力指标饱和，冲突会更多来自 slice、tool side effect、privacy、latency、provider drift 和长期用户结果。
- 如果所有冲突都升级给高层，流程会堵塞；必须把低风险冲突自动化、把高风险冲突显式 elevation。

## 一句话归类

Metric conflict resolution 主属第 6 层，是 eval portfolio、decision threshold、release card 和 release gate 之间的多证据冲突解释边界；它不新增顶层，而是防止一个总分掩盖风险、slice 退化和 hard stop。
