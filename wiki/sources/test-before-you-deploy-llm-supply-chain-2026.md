---
address: c-000407
type: source
title: "Test Before You Deploy: Governing Updates in the LLM Supply Chain"
source_url: https://arxiv.org/abs/2604.27789
source_type: paper
author: "Mohd Sameen Chishti et al."
published: 2026-04-30
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: medium
tags:
  - ai
  - llm-supply-chain
  - compatibility-gate
  - deployment
status: active
related:
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/ProductionContractCompatibilityTest边界]]"
---

# Test Before You Deploy: Governing Updates in the LLM Supply Chain

**来源**：arXiv
**URL**：https://arxiv.org/abs/2604.27789
**发布时间**：2026-04-30

## 摘要

论文把 LLM 托管服务的持续更新视为软件供应链治理问题。作者指出 provider-side silent updates 会造成行为漂移和应用回归，并提出 production contracts、risk-category-based testing suite 和 compatibility gates。

## 关键贡献

- Hosted LLM 的行为可能在没有显式版本变化时漂移。
- 应用侧需要 production contract：模型在该产品里必须满足的行为规则。
- risk-category testing suite 比整体 benchmark 更能发现特定业务风险。
- compatibility gate 应在更新进入真实流量前阻断不兼容变更。
- 对本 vault 的意义：model release / rollback gate 不只管理自己训练的模型，也要管理 provider 更新和模型 alias 漂移。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层、3. 推理与能力层

## 关联

- [[concepts/ModelReleaseRollbackGate边界]]
- [[concepts/ProductionContractCompatibilityTest边界]]
- [[Research: Model release rollback gate 边界]]
