---
address: c-000190
type: source
title: "Fine-Tuning for retrieval augmented generation (RAG) with Qdrant"
source_url: https://developers.openai.com/cookbook/examples/fine-tuned_qa/ft_retrieval_augmented_generation_qdrant
source_type: cookbook
author: "OpenAI Cookbook"
published: 2023-09-04
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - rag
  - fine-tuning
  - qdrant
status: active
related:
  - "[[concepts/微调RAG上下文工程选择框架]]"
---

# Fine-Tuning for retrieval augmented generation (RAG) with Qdrant

**来源**：OpenAI Cookbook
**URL**：https://developers.openai.com/cookbook/examples/fine-tuned_qa/ft_retrieval_augmented_generation_qdrant
**发布时间**：2023-09-04

## 摘要

该 notebook 演示 fine-tuning 与 RAG/Qdrant 的组合，用于提升问答正确性并减少幻觉。页面也提示：在更强模型上，同样设置的 fine-tuning 收益可能很小，因此此材料更适合作为流程参考。

## 关键贡献

- RAG 与 fine-tuning 可以组合，不是互斥关系。
- 训练数据选择会影响正确率与 hallucination trade-off。
- 对“答案不在上下文中”的场景，需要专门评估模型是否会正确拒答。

## 对 AI 知识体系的归属

- 主归属：4. 上下文与知识层
- 交叉链接：2. 模型构建层、6. 评估与可靠性层

## 关联

- [[concepts/微调RAG上下文工程选择框架]]
- [[sources/rag-2020]]
