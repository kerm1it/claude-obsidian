---
address: c-000215
type: source
title: "Self-Adapting Language Models"
source_url: https://arxiv.org/abs/2506.10943
source_type: paper
author: "Adam Zweiger et al."
published: 2025-06-12
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - self-adaptation
  - fine-tuning
  - reinforcement-learning
status: active
related:
  - "[[concepts/Dream与SelfImprovement工程原语]]"
  - "[[concepts/微调RAG上下文工程选择框架]]"
---

# Self-Adapting Language Models

**来源**：arXiv
**URL**：https://arxiv.org/abs/2506.10943

## 摘要

SEAL 提出 Self-Adapting LLMs：模型针对新输入生成 self-edit，包括训练数据、更新指令、超参或数据增强，再通过 supervised fine-tuning 产生持久权重更新，并用下游表现作为强化学习奖励。

## 关键贡献

- 自我改进从 memory/context 层推进到 weights 层。
- 模型生成自己的更新指令，但仍依赖外部训练和评价机制。
- 适合归为前沿研究，不应和生产级 memory dream 混同。

## 对 AI 知识体系的归属

- 主归属：8. 自我改进与前沿层
- 交叉链接：2. 模型构建层、6. 评估与可靠性层
- 作用：说明 weight-level self-improvement 的边界和风险。

## 关联

- [[concepts/Dream与SelfImprovement工程原语]]
- [[concepts/微调RAG上下文工程选择框架]]
- [[Research: Dream 与 self-improvement 工程原语]]
