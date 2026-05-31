---
address: c-000571
type: source
title: "Autogenesis: A Self-Evolving Agent Protocol"
source_url: https://arxiv.org/abs/2604.15034
source_type: paper
author: "Wentao Zhang, Zhe Zhao, Haibin Wen, Yingcheng Wu, Cankun Guo, Ming Yin, Bo An, Mengdi Wang"
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - agents
  - self-evolution
  - protocol
status: active
related:
  - "[[concepts/SelfImprovementGateChangeRiskBudget边界]]"
  - "[[concepts/SkillLibraryRouting生命周期]]"
  - "[[concepts/RAG与Memory边界]]"
---

# Autogenesis: A Self-Evolving Agent Protocol

**来源**：arXiv:2604.15034
**URL**：https://arxiv.org/abs/2604.15034

## 摘要

Autogenesis Protocol 把 prompts、agents、tools、environments 和 memory 建模为 protocol-registered resources，并强调显式状态、生命周期和版本接口。其 Self Evolution Protocol Layer 描述 closed-loop operator interface，用于 proposing、assessing 和 committing improvements，并带 auditable lineage 与 rollback。

## 对本体系的贡献

- 给第 8 层 self-improvement 一个 resource model：改动对象不只是“提示词”，而是 prompt、tool、agent、environment、memory 的版本化资源。
- 支撑 self-improvement gate 的字段：versioned interface、lineage、rollback、assess/commit 分离。
- 帮助后续 memory/skill governance drift 研究：长期资源需要生命周期和版本治理。

## 对 AI 知识体系的归属

- 主归属：8. 自我改进与前沿层
- 交叉链接：4. 上下文与知识层、5. Agent 系统层、6. 评估与可靠性层

## 关联

- [[concepts/SelfImprovementGateChangeRiskBudget边界]]
- [[concepts/SkillLibraryRouting生命周期]]
- [[Research: Self-improvement gate change-risk budget 边界]]
