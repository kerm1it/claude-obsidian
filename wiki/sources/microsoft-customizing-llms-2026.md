---
address: c-000184
type: source
title: "Getting started with customizing a large language model"
source_url: https://learn.microsoft.com/en-us/azure/foundry-classic/openai/concepts/customizing-llms
source_type: documentation
author: "Microsoft Learn"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - prompt-engineering
  - rag
  - fine-tuning
status: active
related:
  - "[[concepts/微调RAG上下文工程选择框架]]"
  - "[[domains/AI知识体系]]"
---

# Getting started with customizing a large language model

**来源**：Microsoft Learn
**URL**：https://learn.microsoft.com/en-us/azure/foundry-classic/openai/concepts/customizing-llms

## 摘要

Microsoft 将 prompt engineering、RAG、fine-tuning 定义为三种适配预训练模型到特定任务或领域的方法，并明确指出它们不是互斥关系，而是可以组合使用的互补方法。

## 关键贡献

- Prompt engineering 是生成期望输出的起点。
- RAG 将外部数据整合进 LLM prompt，适合组织私有知识、过期训练知识和大量非结构化文档。
- Fine-tuning 是用训练集迭代适配模型，适合小范围主题、特定技能、成本和延迟优化。

## 对 AI 知识体系的归属

- 主归属：4. 上下文与知识层
- 交叉链接：2. 模型构建层、7. 产品与组织层
- 贡献：为三者选择框架提供官方工程分类。

## 关联

- [[concepts/微调RAG上下文工程选择框架]]
- [[Research: 微调 vs RAG vs 上下文工程]]
