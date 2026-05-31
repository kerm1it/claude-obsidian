---
address: c-000428
type: source
title: "Attesting LLM Pipelines: Enforcing Verifiable Training and Release Claims"
source_url: https://arxiv.org/abs/2603.28988
source_type: paper
author: "Zhuoran Tan et al."
fetched: 2026-05-30
created: 2026-05-30
confidence: medium
tags:
  - ai
  - supply-chain
  - attestation
status: active
related:
  - "[[concepts/ProductionContractCompatibilityTest边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
---

# Attesting LLM Pipelines: Enforcing Verifiable Training and Release Claims

**来源**：arXiv / LLMSC 2026
**URL**：https://arxiv.org/abs/2603.28988

## 摘要

论文把 LLM 系统视为由预训练权重、adapter、dataset、dependency package 和 container 等第三方 artifact 拼装而成的供应链。作者提出 attestation-aware promotion gate，在 artifact 进入训练、微调或部署环境前验证 claim evidence、扫描和安全加载策略。

## 关键贡献

- 训练和发布声明如果没有和 artifact 绑定，就难以在团队和阶段之间一致执行。
- Promotion gate 可以验证 lineage、build environment、security scan 和 deployment constraints。
- 对本 vault 的意义：compatibility test 不只验证输出行为，也要验证供应链 artifact 的来源、声明和准入证据。
- 对 evidence attestation 的意义：promotion gate 必须把 release claim、artifact identity、扫描结果和部署约束绑定为可验证证据，否则 release card 和 safety case 只能依赖人工声明。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层、2. 模型构建层

## 关联

- [[concepts/ProductionContractCompatibilityTest边界]]
- [[concepts/EvidenceAttestationSignedEvalArtifact边界]]
- [[Research: Production contract compatibility test 边界]]
