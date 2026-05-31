---
address: c-000552
type: concept
title: "Release Gate Debt / Gate Bypass Detection 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - release-gate
  - governance
  - bypass-detection
  - change-control
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/OverrideGovernanceResidualRiskAcceptance边界]]"
  - "[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]"
  - "[[concepts/DashboardCalibrationGovernanceMetricQuality边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
  - "[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]"
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
sources:
  - "[[sources/github-actions-deployment-protection-rules-2026]]"
  - "[[sources/github-actions-reviewing-deployments-admin-bypass-2026]]"
  - "[[sources/gitlab-protected-environments-deployment-approvals-2026]]"
  - "[[sources/gitlab-deployment-safety-2026]]"
  - "[[sources/google-cloud-deploy-approvals-policies-audit-2026]]"
  - "[[sources/nist-sp800-53-cm3-cm5-change-control-2025]]"
  - "[[sources/nist-sp800-55-measurement-guide-2024]]"
  - "[[sources/google-sre-alerting-on-slos-2018]]"
---

# Release Gate Debt / Gate Bypass Detection 边界

Release gate debt / gate bypass detection 是第 7 层产品与组织层的发布治理健康边界：它检测 AI 系统的模型、prompt、router、tool、skill、provider、RAG/memory 或 policy 变更是否绕过了既定 release gate，或通过 admin bypass、manual hotfix、shadow approval、过期例外、未保护环境、直接生产写入、provider silent update 和 gate config 漂移稀释了质量门。

一句话：**release gate 决定一次变更能不能上；gate bypass detection 证明真实生产变更没有绕开这道门。**

## 主归属

- 主归属：7. 产品与组织层
- 质量输入：6. 评估与可靠性层
- 上游输入：gate policy、protected environment config、approval history、deployment events、runtime artifact inventory、audit logs、attestation、override records、provider/model update notices
- 下游输出：ungated-change finding、gate debt ledger、admin-bypass review、policy/config repair、access revocation、release freeze、rollback/containment、postmortem/action backlog
- 记录底座：[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]

## 稳定链路

```text
required release path and gate policy
    -> production change inventory: artifact, actor, channel, target, time, runtime state
    -> evidence join: eval/release card, approval, protected environment, attestation, exception, audit log
    -> classify: valid gated change, approved emergency, admin bypass, stale exception, direct path, shadow approval, unknown
    -> action: block, rollback, quarantine, revoke access, require retroactive review, fix gate config, freeze releases
    -> gate debt ledger and trend review
```

## Bypass 类型

| 类型 | 说明 |
|---|---|
| Admin bypass | 管理员强制跳过保护规则、审批、等待或 deploy policy |
| Shadow approval | 审批发生在聊天、邮件或口头沟通里，没有进入 release evidence |
| Direct-to-prod write | 通过 kubectl、console、cloud API、manual script 或 provider UI 直接改生产 |
| Ungated artifact | 生产运行的 model/prompt/router/tool/provider 版本没有 release card 或 eval bundle |
| Stale exception | 过期 override、已失效 residual-risk acceptance 或已关闭 incident workaround 仍然生效 |
| Gate config drift | protected environment、branch/tag restriction、required reviewer、deploy policy 或 approval count 被改弱 |
| Concurrency / stale deploy | 较旧 pipeline、重试、rollback retry 或并发 job 覆盖新版本 |
| Provider silent path | 外部 model/provider alias、region、tool 或 safety policy 被供应商更新，绕过本地变更门 |

## 与相邻概念区别

- 与 [[concepts/ModelReleaseRollbackGate边界]]：release gate 管单次发布、灰度、回滚；本页检查真实生产变更是否都经过该 gate，或 gate 是否被削弱。
- 与 [[concepts/OverrideGovernanceResidualRiskAcceptance边界]]：override governance 管合法例外；本页检测无记录例外、过期例外、admin bypass 和 shadow approval。
- 与 [[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]：override debt dashboard 聚合结构化例外；本页还要捕捉没有形成结构化 override record 的隐藏绕过。
- 与 [[concepts/DashboardCalibrationGovernanceMetricQuality边界]]：本页产生 gate bypass、ungated change 和 stale exception 信号；dashboard calibration 检查这些信号有没有清楚分母、漏报审查、freshness、coverage 和正确 action ladder。
- 与 [[concepts/CrossVerifierPolicyDriftConformanceTest边界]]：cross-verifier test 检查 verifier 语义一致；本页检查部署/变更路径是否真的被 gate/verifier 覆盖。
- 与 [[concepts/MonitorOwnershipEscalationLadder边界]]：monitor ownership 把信号交给 owner；本页定义哪些信号说明 gate 被绕过或欠债。
- 与 generic CI/CD audit：AI gate bypass 还要覆盖 model alias、prompt/config、tool permission、RAG index、memory write policy、provider update 和 eval evidence。

## 工程实践

1. 建立 required release path registry：每类 artifact 必须经过哪些 eval、approval、attestation、protected environment 和 rollout step。
2. 对生产环境做实际状态采集：model snapshot、prompt hash、router config、tool/skill version、RAG index、provider/model alias、admission policy 和 deployment target。
3. 把实际状态与 release evidence join：找不到 release card、approval、signed bundle、exception 或 audit log 的生产变更先标为 unknown/ungated。
4. 对 GitHub/GitLab/Cloud Deploy 等平台定期扫描 protected environment、admin bypass、self-approval、required reviewers、deploy policy override、deployment approval history 和 audit logs。
5. 限制直接生产写入：生产凭证只给 release runner / deploy service account；人工 emergency path 要自动生成 override record。
6. 对 gate config 做 drift check：required approval count、allow-admin-bypass、protected branch/tag、environment scope、policy override role、freeze window、deployment project 权限。
7. 对每次 admin bypass、deploy policy override、failed gate override 或 retroactive approval 做原因分类和到期复审。
8. 把 bypass finding 写入 gate debt ledger，超过阈值触发 release freeze、权限收紧、gate 修复或事故复盘。

## 评估方式

- Ungated change rate：生产变更中没有 release evidence 的比例。
- Admin bypass rate：管理员强制绕过、policy override 或 emergency path 的频率。
- Shadow approval discovery：聊天/邮件/工单里发现但 release evidence 中缺失的批准次数。
- Stale exception leakage：过期 exception、过期 emergency access 或关闭 workaround 仍然影响生产的次数。
- Gate coverage：关键 artifact type 是否都有 required release path 和 protected deployment target。
- Config drift latency：gate config 被改弱到被检测和修复的时间。
- Retroactive review closure：绕过发现后是否补齐 root cause、权限修复、eval/gate backlog 和 closure evidence。

## 过时风险

- 具体 CI/CD 平台、审批系统和部署工具会变化，但 required path registry、production state inventory、evidence join、bypass classification、gate debt ledger 和 closure action 稳定。
- 如果只统计已记录 override，会漏掉 shadow approval 和 direct-to-prod；如果只查 CI/CD，会漏掉 provider silent update 和运行时手工改动。
- 零 bypass 不是目标本身；真正目标是 emergency path 可见、限时、可审计，并且不会变成常规发布路径。

## 一句话归类

Release gate debt / gate bypass detection 主属第 7 层，是 release gate 和 override governance 之后的治理健康边界；它不新增顶层，而是证明 AI 生产变更真实经过了既定证据门，或在绕过时留下可审查、可关闭的风险债务。
