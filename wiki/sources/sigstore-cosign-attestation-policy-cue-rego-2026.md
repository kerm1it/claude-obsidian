---
address: c-000541
type: source
title: "Sigstore Cosign In-Toto Attestation Policy with CUE and Rego"
source_url: https://docs.sigstore.dev/cosign/verifying/attestation/
source_type: documentation
author: "Sigstore"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - sigstore
  - cosign
  - attestation
  - policy
status: active
related:
  - "[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]"
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
---

# Sigstore Cosign In-Toto Attestation Policy with CUE and Rego

**来源**：Sigstore Docs
**URL**：https://docs.sigstore.dev/cosign/verifying/attestation/

## 摘要

Sigstore Cosign 文档说明 verify-attestation 不只检查签名，还可以用 CUE 或 Rego policy 校验 in-toto attestation 的 predicate 内容。

## 关键贡献

- Attestation verification 可以绑定 policy，而不是只验证 signature。
- CUE / Rego policy 让 CLI 验证和 gate/admission 验证共享语义。
- 文档强调 policy 要验证 predicate portion，避免验错层级。
- 对本 vault 的意义：cross-verifier conformance test 应用同一 attestation policy 运行在 local CLI、CI 和 admission/release gate 上。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/CrossVerifierPolicyDriftConformanceTest边界]]
- [[concepts/VerifierPolicyTrustRootRotation边界]]
- [[Research: Cross-verifier policy drift conformance test 边界]]
