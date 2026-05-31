---
address: c-000523
type: source
title: "in-toto verify"
source_url: https://in-toto.readthedocs.io/en/stable/command-line-tools/in-toto-verify.html
source_type: documentation
author: "in-toto"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - in-toto
  - verification
  - supply-chain
  - policy
status: active
related:
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
  - "[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]"
---

# in-toto verify

**来源**：in-toto Docs
**URL**：https://in-toto.readthedocs.io/en/stable/command-line-tools/in-toto-verify.html

## 摘要

in-toto verify 用 root layout、verification keys 和 link metadata 验证供应链步骤是否按 layout 执行，包括签名、expiry、threshold、authorized functionary 和 artifact rules。

## 关键贡献

- Verification 不只验证签名，还验证 layout、expiry、threshold、授权 functionary 和材料/产物规则。
- Root layout 与 verification keys 是可回放的 verifier policy 输入。
- 文档强调 verification workflow 不依赖外部 key 信息，便于审计和重放。
- 对本 vault 的意义：AI verifier policy 也应保存 policy、root/key 和 expected artifact rules，避免口头解释“为什么通过”。
- 对 cross-verifier conformance 的意义：layout、expiry、threshold 和 artifact rules 是 golden corpus 的核心测试维度。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/VerifierPolicyTrustRootRotation边界]]
- [[concepts/CrossVerifierPolicyDriftConformanceTest边界]]
- [[Research: Verifier policy trust root rotation 边界]]
- [[Research: Cross-verifier policy drift conformance test 边界]]
