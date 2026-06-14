---
address: c-000524
type: source
title: "Sigstore policy-controller"
source_url: https://github.com/sigstore/policy-controller
source_type: repository
author: "Sigstore"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - sigstore
  - policy-controller
  - admission-control
  - supply-chain
status: active
related:
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]"
---

# Sigstore policy-controller

**来源**：Sigstore GitHub
**URL**：https://github.com/sigstore/policy-controller

## 摘要

Sigstore policy-controller 是 Kubernetes admission controller，用 verifiable supply-chain metadata enforce policy。它能自动验证 container signatures 和 attestations，并支持 per-namespace enforcement 与 multiple keys。

## 关键贡献

- Verification policy 可以从手工命令进入 admission gate。
- 自动验证 signatures / attestations 是 release/runtime admission 的工程模式。
- Policy tester 支持在部署前检查 policy 行为。
- 对本 vault 的意义：AI release gate 可借鉴 admission-controller 模式，把 verifier policy 变成可测试、可执行、可审计的质量门。
- 对 cross-verifier conformance 的意义：policy-controller 是 admission enforcement 点，必须和 local CLI、CI、release gate 执行同一 policy、trust root 和 warn/enforce 语义。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/VerifierPolicyTrustRootRotation边界]]
- [[concepts/CrossVerifierPolicyDriftConformanceTest边界]]
- [[Research: Verifier policy trust root rotation 边界]]
- [[Research: Cross-verifier policy drift conformance test 边界]]
