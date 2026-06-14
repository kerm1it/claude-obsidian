---
address: c-000499
type: source
title: "SLSA v1.2 Build: Verifying artifacts"
source_url: https://slsa.dev/spec/v1.2/verifying-artifacts
source_type: specification
author: "SLSA"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - supply-chain
  - verification
  - provenance
  - slsa
status: active
related:
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
---

# SLSA v1.2 Build: Verifying artifacts

**来源**：SLSA
**URL**：https://slsa.dev/spec/v1.2/verifying-artifacts

## 摘要

SLSA 的 artifact verification 说明，provenance 只有被检查才有用。验证过程包括检查 builder identity、验证 provenance envelope 签名、确认 statement subject 与 artifact digest 匹配，并检查 buildType 和 externalParameters 是否符合期望。

## 关键贡献

- 验证 provenance 需要 roots of trust，而不只是保存 provenance。
- subject digest、signature、builder identity、predicateType 和 expected parameters 都是验证点。
- 消费者可在 package ecosystem、consumer 或 monitor 位置执行 verification。
- 对本 vault 的意义：signed eval artifact 也必须有 verifier policy；只把分数文件签名但不检查被测 artifact 和运行配置，证据仍不可靠。
- 对 trust root rotation 的意义：verification expectations 和 roots of trust 需要版本化，否则相同 artifact 在不同 verifier 上会得到不同结论。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/EvidenceAttestationSignedEvalArtifact边界]]
- [[concepts/VerifierPolicyTrustRootRotation边界]]
- [[Research: Evidence attestation signed eval artifact 边界]]
- [[Research: Verifier policy trust root rotation 边界]]
