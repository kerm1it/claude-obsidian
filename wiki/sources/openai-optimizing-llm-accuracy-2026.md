---
address: c-000187
type: source
title: "Optimizing LLM accuracy"
source_url: https://developers.openai.com/api/docs/guides/optimizing-llm-accuracy
source_type: documentation
author: "OpenAI"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - fine-tuning
  - evaluation
  - rag
status: active
related:
  - "[[concepts/微调RAG上下文工程选择框架]]"
---

# Optimizing LLM accuracy

**来源**：OpenAI Docs
**URL**：https://developers.openai.com/api/docs/guides/optimizing-llm-accuracy

## 摘要

该指南强调 fine-tuning 前应先有 prompt-engineering 基线和 eval 集；训练数据质量比数量重要；如果错误来自上下文缺失，fine-tuning 不是首选。

## 关键贡献

- 先从 prompt engineering 开始，并用 eval 集作为 baseline。
- Fine-tuning 数据质量优先于数量；可以从 50+ 样例开始评估。
- 训练样例必须代表生产输入。RAG 应用如果要 fine-tune，训练样例也应包含 RAG 上下文，否则模型没有学会如何使用运行时上下文。
- 需要 hold-out eval 以检测过拟合。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层、4. 上下文与知识层

## 关联

- [[concepts/微调RAG上下文工程选择框架]]
- [[sources/openai-model-optimization-2026]]
