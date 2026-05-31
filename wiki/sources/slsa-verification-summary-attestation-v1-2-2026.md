---
address: c-000518
type: source
title: "SLSA v1.2 Verification Summary Attestation"
source_url: https://slsa.dev/spec/v1.2/verification_summary
source_type: specification
author: "SLSA"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - slsa
  - verification
  - attestation
  - policy
status: active
related:
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
  - "[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]"
---

# SLSA v1.2 Verification Summary Attestation

**来源**：SLSA
**URL**：https://slsa.dev/spec/v1.2/verification_summary

## 摘要

SLSA VSA 定义 verification summary attestation：某个 verifier 针对 artifact 和 attestation bundle 执行 policy 验证后，生成一个可被消费者信任或复核的 summary。

## 关键贡献

- VSA 把 verifier、subject、policy、verified levels 和 result 明确写入 attestation。
- 消费者仍需要验证 VSA envelope 的签名来自预配置 root of trust。
- VSA 可用于传递 transitive dependency 的 verified level。
- 对本 vault 的意义：AI release gate 可以接受第三方或平台 verifier 的 summary，但必须保存 verifier identity、policy version 和 trust root。
- 对 cross-verifier conformance 的意义：delegated verifier 的 VSA 也要和本地 policy expectation 对齐，否则会出现第三方通过、本地不接受或反向不一致。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/VerifierPolicyTrustRootRotation边界]]
- [[concepts/CrossVerifierPolicyDriftConformanceTest边界]]
- [[Research: Verifier policy trust root rotation 边界]]
- [[Research: Cross-verifier policy drift conformance test 边界]]
