---
address: c-000512
type: concept
title: "Override Governance / Residual Risk Acceptance 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - governance
  - override
  - residual-risk
  - release-gate
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/MetricConflictResolution边界]]"
  - "[[concepts/IntolerableRiskThresholdStopRule边界]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/SafetyCaseAssuranceCase边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
  - "[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]"
  - "[[concepts/ReleaseGateDebtBypassDetection边界]]"
sources:
  - "[[sources/nist-sp800-37-risk-response-2018]]"
  - "[[sources/sigstore-tuf-root-update-2024]]"
  - "[[sources/nist-sp800-30-risk-assessment-2012]]"
  - "[[sources/nist-ai-rmf-risk-tolerance-2023]]"
  - "[[sources/openai-preparedness-framework-2025]]"
  - "[[sources/microsoft-responsible-ai-standard-2022]]"
  - "[[sources/google-sre-error-budget-policy-2018]]"
  - "[[sources/nist-sp800-53-au11-audit-record-retention-2025]]"
  - "[[sources/nist-sp800-55-measurement-guide-2024]]"
  - "[[sources/google-sre-good-housekeeping-error-budget-debt-2018]]"
  - "[[sources/github-actions-reviewing-deployments-admin-bypass-2026]]"
  - "[[sources/nist-sp800-53-cm3-cm5-change-control-2025]]"
---

# Override Governance / Residual Risk Acceptance 边界

Override governance / residual risk acceptance 是第 7 层产品与组织层的受控例外边界：当第 6 层 eval、guardrail、freshness、release card、safety case 或 monitor 给出不完整、冲突或未完全达标的证据时，它定义哪些情况绝不能 override，哪些情况可在有 owner、期限、缓解、监控、回滚和审计记录的条件下接受残余风险。

一句话：**override 不是绕过质量门，而是把例外变成有边界、有期限、有责任人的风险决策。**

## 主归属

- 主归属：7. 产品与组织层
- 质量输入：6. 评估与可靠性层
- 上游输入：metric conflict、gray-zone eval、stale/unknown evidence、release card limitation、safety case defeater、business deadline、incident workaround
- 下游输出：approve / deny / restrict / expire / revoke decision、residual-risk record、monitor obligation、rollback trigger、review cadence、audit trail
- 硬边界：[[concepts/IntolerableRiskThresholdStopRule边界]]

## 稳定链路

```text
exception or override request
    -> identify controlled decision, artifact identity, evidence gap, affected users, risk tier
    -> check non-overridable hard stops and legal/prohibited-use boundaries
    -> evaluate alternatives: mitigate, restrict scope, canary, delay, fallback, rerun eval, external review
    -> document residual risk, uncertainty, owner, approval authority, expiry, conditions, monitoring, rollback
    -> write release card / safety case / risk register / gate decision
    -> monitor until expiry or closure
    -> renew, revoke, escalate, remediate, or convert to permanent policy only through review
```

## Override 记录字段

| 字段 | 作用 |
|---|---|
| Decision id / artifact identity | 绑定 model、prompt、tool、provider、router、eval result 或 release |
| Evidence gap | 哪个 eval、slice、freshness、signature、monitor 或 safety evidence 不足 |
| Hard-stop check | 明确没有触发不可容忍风险、法律禁止或强制 safeguard 缺失 |
| Residual risk | 剩余 harm、用户范围、概率/严重度、不确定性和可接受原因 |
| Mitigation alternatives | 已尝试或拒绝的 rerun、restrict、canary、fallback、delay、human review |
| Approval authority | 谁有权接受，是否需要 risk owner、legal、security、exec 或 external review |
| Expiry / review | 例外什么时候自动失效，何时复审，什么信号会提前撤销 |
| Monitor / rollback | 需要哪些 live signals、threshold、rollback trigger 和 owner |

## 与相邻概念区别

- 与 [[concepts/IntolerableRiskThresholdStopRule边界]]：stop rule 定义不能 override 的 hard no-go；本页只治理可接受范围内的例外和残余风险。
- 与 [[concepts/MetricConflictResolution边界]]：metric conflict 决定冲突动作；override governance 记录谁在什么条件下接受非理想动作的剩余风险。
- 与 [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]：release card 表达灰区、局限和 override rationale；本页定义 override 必须有哪些字段、权限、期限和监控。
- 与 [[concepts/SafetyCaseAssuranceCase边界]]：safety case 论证残余风险可接受；本页是批准、期限、复审和撤销的治理机制。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：release gate 执行例外放行、限制、hold 或 rollback；本页决定例外是否有资格进入 gate。
- 与 [[concepts/VerifierPolicyTrustRootRotation边界]]：verifier policy 失败、unknown root 或 root rotation client 不兼容不能静默放行；若业务必须继续，必须记录残余风险、期限、monitor、补证和回滚条件。
- 与 [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]：override governance 定义例外能否批准；audit packet lifecycle 确保批准依据、残余风险、期限、monitor、补证和撤销记录长期可查。
- 与 [[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]：override governance 审批或撤销单条例外；override debt dashboard 观察跨例外的比率、续期、过期、重复 owner 和事故转化。
- 与 [[concepts/ReleaseGateDebtBypassDetection边界]]：override governance 定义合法例外如何记录、过期和监控；gate bypass detection 发现没有形成合法例外的 admin bypass、shadow approval、direct path 和 stale exception。
- 与 business exception：商业压力不是证据；只有带风险 owner、限制范围、补证计划和 rollback 条件的例外才可进入 AI release decision。

## 工程实践

1. 把 override 作为结构化对象，不写在聊天、邮件或口头决定里。
2. 先跑 hard-stop checklist：法律禁止、不可容忍风险、critical privacy/security/tool breach、缺失强制 safeguard 时直接 deny。
3. 对每个 override 设置默认过期时间；没有 expiry 的例外默认无效。
4. 要求补证计划：rerun eval、补样本、校准 judge、刷新 release card、做 canary、跑 drill 或更新 safety case。
5. 绑定 live monitor 和 rollback trigger；无法监控的高风险 override 不应放行。
6. 定期统计 override debt：重复例外、过期例外、商业压力例外、同一 owner 反复接受的残余风险。
7. 例外转永久政策必须走完整评审，不能通过连续 renewal 偷偷常态化。

## 评估方式

- Override rate：每类 release gate、metric conflict 或 evidence gap 中有多少走 override。
- Expired exception rate：过期后仍在生产、release card 或 risk register 中生效的例外比例。
- Non-overridable bypass attempts：试图绕过 hard stop、法律禁止或 mandatory safeguard 的次数。
- Residual-risk incident rate：已接受残余风险是否变成事故、回滚或用户伤害。
- Monitor coverage：override 是否都有 live monitor、owner、rollback trigger 和 review date。
- Mitigation closure：补证、修复、限制、重新评估是否按期完成。
- Approval match：批准者是否符合风险等级和数据/安全/法律权限。

## 过时风险

- 具体审批工具和风险分类会变化，但 hard-stop check、residual-risk record、expiry、owner、monitor 和 rollback trigger 稳定。
- 模型越强、产品越快，override 会成为组织偷懒的捷径；必须用统计和过期机制防止 exception sprawl。
- Residual risk acceptance 不能证明系统安全，只证明组织在知道剩余风险的情况下作出可审计决策。

## 一句话归类

Override governance / residual risk acceptance 主属第 7 层，是第 6 层证据不足或冲突进入第 7 层发布、限制、延后、回滚或残余风险接受前的受控例外边界；它不新增顶层，而是防止例外吞掉质量门。
