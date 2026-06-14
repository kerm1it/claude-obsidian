---
address: c-000198
type: source
title: "Mitigating Provenance-Role Collapse in Long-Term Agents via Typed Memory Representation"
source_url: https://arxiv.org/abs/2605.25869
source_type: paper
author: "MemIR authors"
published: 2026-05-25
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - memory
  - provenance
  - agents
status: active
related:
  - "[[concepts/RAG与Memory边界]]"
---

# Mitigating Provenance-Role Collapse in Long-Term Agents via Typed Memory Representation

**来源**：arXiv:2605.25869
**发布时间**：2026-05-25

## 摘要

MemIR 指出长期 agent memory 若存成非结构化平面文本，会导致 provenance-role collapse：agent 混淆证据、检索线索和事实 claim 的角色，从而出现 source-monitoring 错误。

## 关键贡献

- Memory 需要 typed representation，而不是仅靠相似度检索。
- MemIR 将 memory 写成 grounded atoms，区分 raw evidence、retrieval cues 和 truth-bearing claims。
- 对 RAG/memory 边界的启发：RAG 需要出处，memory 更需要角色和来源约束，否则会把旧交互误当事实。

## 对 AI 知识体系的归属

- 主归属：4. 上下文与知识层
- 交叉链接：6. 评估与可靠性层、8. 自我改进与前沿层

## 关联

- [[concepts/RAG与Memory边界]]
- [[concepts/AgentMemoryAPI]]
