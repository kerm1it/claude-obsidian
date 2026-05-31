---
address: c-000558
type: source
title: "Google Cloud Deploy Approvals, Deploy Policies, and Audit Logs"
source_url: https://docs.cloud.google.com/deploy/docs/promote-release
source_type: documentation
author: "Google Cloud"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - google-cloud
  - cloud-deploy
  - approvals
  - audit-logs
  - deploy-policy
status: active
related:
  - "[[concepts/ReleaseGateDebtBypassDetection边界]]"
  - "[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
---

# Google Cloud Deploy Approvals, Deploy Policies, and Audit Logs

**来源**：Google Cloud Deploy docs
**URL**：https://docs.cloud.google.com/deploy/docs/promote-release
**补充 URL**：https://docs.cloud.google.com/deploy/docs/deploy-policy；https://docs.cloud.google.com/deploy/docs/audit-logs；https://docs.cloud.google.com/deploy/docs/securing/binary-authorization

## 摘要

Cloud Deploy 支持 target approval、rollout approval/reject、deploy policies、policy override、rollout/job state、audit logs 和与 Binary Authorization 配合的部署时规则 enforcement。这些机制把发布 gate、绕过、审计和运行时 enforcement 连接起来。

## 关键贡献

- Target 可设置 `requireApproval: true`，rollout 在 approval 前处于 pending approval。
- Deploy policies 可以限制 manual 或 automated pipeline action，并可通过 override permission 显式绕过。
- Cloud Deploy audit logs 记录 approve、advance、create rollout、update policy、override 等管理动作。
- Binary Authorization 可在 deploy time 通过 attestations 判断之前流程是否完成，并持续验证容器是否符合 policy。
- 对本 vault 的意义：gate bypass detection 应 join rollout states、policy override、audit log、attestation enforcement 和 runtime deployment state。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/ReleaseGateDebtBypassDetection边界]]
- [[concepts/CrossVerifierPolicyDriftConformanceTest边界]]
- [[concepts/EvidenceAttestationSignedEvalArtifact边界]]
- [[Research: Release gate debt gate bypass detection 边界]]
