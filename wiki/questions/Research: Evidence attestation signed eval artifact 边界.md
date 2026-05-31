---
address: c-000497
type: research
title: "Research: Evidence attestation signed eval artifact 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - research
  - attestation
  - evals
  - supply-chain
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
sources:
  - "[[sources/slsa-provenance-v1-2-2026]]"
  - "[[sources/slsa-verifying-artifacts-v1-2-2026]]"
  - "[[sources/in-toto-test-result-predicate-2026]]"
  - "[[sources/sigstore-cosign-verifying-attestations-2026]]"
  - "[[sources/openssf-model-signing-2026]]"
  - "[[sources/nist-ssdf-sp800-218-2022]]"
  - "[[sources/attesting-llm-pipelines-release-claims-2026]]"
---

# Research: Evidence attestation signed eval artifact 边界

## 问题

第 6/7 层如何证明 eval artifact、模型版本、prompt、judge、dataset、container、release card 和来源声明没有被替换、篡改或错误绑定？

## 结论

Evidence attestation / signed eval artifact 应主属第 6 层，因为它解决的是“评估证据是否完整、可验证、可审计”。它不是新的顶层，也不是单纯的安全工具；它位于 lineage、freshness、eval portfolio、release card 和 release gate 之间。

稳定链路是：`artifact digest -> attestation statement -> signed bundle -> policy verification -> release/safety evidence`。

## 关键发现

- SLSA v1.2 将 provenance 定义为可验证信息，用于追踪 artifact 从复杂供应链回到来源；这给模型、prompt、eval result 和容器 artifact 提供通用心智模型。(Source: [[sources/slsa-provenance-v1-2-2026]])
- SLSA verification 不只验证签名，还要检查 subject digest、builder identity、predicateType、buildType、externalParameters 和 roots of trust；这说明 signed eval artifact 必须有 policy verification，而不是只有 checksum。(Source: [[sources/slsa-verifying-artifacts-v1-2-2026]])
- in-toto Test Result predicate 提供通用 test result attestation schema，可表达 result、configuration、run URL、passed/warned/failed tests；这很接近 AI eval run 的 signed result 结构。(Source: [[sources/in-toto-test-result-predicate-2026]])
- Sigstore / Cosign 支持签名和 verify-attestation，并可使用 OIDC identity、Fulcio/Rekor 或企业 trust root；这给模型、容器、eval bundle 和 prompt package 提供可操作实现路径。(Source: [[sources/sigstore-cosign-verifying-attestations-2026]])
- OpenSSF Model Signing 明确 ML 模型也需要签名和验证，特别是训练团队、hub 和部署团队不是同一方时；这把 model weights 纳入 supply-chain integrity。(Source: [[sources/openssf-model-signing-2026]])
- NIST SSDF 提供 secure software development 的共同词汇，强调软件供应链风险管理和 vulnerability management；AI release evidence 可以借用其 acquisition / supplier communication 思路。(Source: [[sources/nist-ssdf-sp800-218-2022]])
- Attesting LLM Pipelines 论文把 LLM pipeline artifact、training/release claims 和 promotion gate 连接起来，支持在 artifact 进入训练、微调或部署前验证声明。(Source: [[sources/attesting-llm-pipelines-release-claims-2026]])

## 分类决策

- 主归属：6. 评估与可靠性层
- 组织接口：7. 产品与组织层
- 上游：artifact identity、hash、lineage、eval run、builder/evaluator identity、signature、policy
- 下游：release card、safety case、release/rollback gate、provider review、incident reconstruction

## 工程结构

```text
subject: model/prompt/judge/dataset/container/eval-result digest
predicateType: provenance / test-result / verification-summary / custom eval predicate
predicate: run config, evaluator, result, policy, source, dependencies, timestamps
envelope: signature, certificate or key, timestamp/transparency evidence
verifier: trust root + expected identity + expected parameters + freshness policy
decision: accept, quarantine, rerun, reject, block release, or re-attest
```

## Open Questions

- AI eval 是否需要专门的 in-toto predicate，还是用 Test Result predicate 加扩展字段足够？
- 第三方模型 hub 的 verification badge 能否作为高风险 release gate 证据，还是必须导出 bundle 给本地 verifier？
- 对 prompt、rubric、policy 这类小文本 artifact，是否应和模型权重使用同一签名和透明日志机制？

## 代表来源

- [[sources/slsa-provenance-v1-2-2026]]
- [[sources/slsa-verifying-artifacts-v1-2-2026]]
- [[sources/in-toto-test-result-predicate-2026]]
- [[sources/sigstore-cosign-verifying-attestations-2026]]
- [[sources/openssf-model-signing-2026]]
- [[sources/nist-ssdf-sp800-218-2022]]
- [[sources/attesting-llm-pipelines-release-claims-2026]]
