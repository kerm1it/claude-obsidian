---
address: c-000173
type: source
title: "Attention Is All You Need"
source_url: https://arxiv.org/abs/1706.03762
source_type: paper
author: "Vaswani et al."
published: 2017
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - transformer
  - paper
status: active
related:
  - "[[domains/AI知识体系]]"
---

# Attention Is All You Need

**来源**：arXiv:1706.03762
**作者**：Ashish Vaswani 等
**发布时间**：2017

## 摘要

这篇论文提出 Transformer：一个完全基于注意力机制的序列建模架构，去掉循环和卷积。它成为现代 LLM 的基础架构支点。

## 关键贡献

- Transformer 用 self-attention 建模 token 间关系，提高并行训练能力。
- 论文证明该架构在机器翻译任务上达到强结果，并显著降低训练时间。
- 对 AI 知识体系而言，它属于“基础理论层”：解释当前大模型为什么能用统一架构处理语言、代码、多模态等任务。

## 对 AI 知识体系的归属

- 主归属：1. 基础理论层
- 下游：2. 模型构建层、3. 推理与能力层
- 学习作用：先理解 attention 和 transformer，再学习 scaling、pretraining、RAG、agent。

## 关联

- [[domains/AI知识体系]]
- [[Research: AI知识体系总览]]
