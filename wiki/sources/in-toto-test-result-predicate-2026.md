---
address: c-000500
type: source
title: "in-toto Test Result predicate"
source_url: https://github.com/in-toto/attestation/blob/main/spec/predicates/test-result.md
source_type: specification
author: "in-toto Attestation Framework"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - in-toto
  - attestation
  - test-result
  - evals
status: active
related:
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
---

# in-toto Test Result predicate

**来源**：in-toto Attestation Framework
**URL**：https://github.com/in-toto/attestation/blob/main/spec/predicates/test-result.md

## 摘要

in-toto Test Result predicate 是一个通用 test result attestation schema，用于表达测试在软件供应链中是否运行、是否通过，以及使用了什么配置。它包含 result、configuration、url、passedTests、warnedTests 和 failedTests 等字段。

## 关键贡献

- 把 test result 绑定到 in-toto Statement 的 subject artifact。
- 支持 verifier 检查测试配置是否符合 policy。
- 支持按部署目标或上下文只消费相关测试结果。
- 对本 vault 的意义：AI eval run 可以被建模为 test result attestation，subject 是被测 model/prompt/judge/dataset/container，predicate 是 eval 配置和结果。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/EvidenceAttestationSignedEvalArtifact边界]]
- [[Research: Evidence attestation signed eval artifact 边界]]
