---
address: c-000189
type: source
title: "What is Retrieval-Augmented Generation (RAG)?"
source_url: https://cloud.google.com/use-cases/retrieval-augmented-generation
source_type: documentation
author: "Google Cloud"
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - rag
  - retrieval
status: active
related:
  - "[[concepts/微调RAG上下文工程选择框架]]"
  - "[[concepts/渐进式上下文注入]]"
---

# What is Retrieval-Augmented Generation (RAG)?

**来源**：Google Cloud
**URL**：https://cloud.google.com/use-cases/retrieval-augmented-generation

## 摘要

Google Cloud 将 RAG 定义为结合传统检索系统和生成式 LLM 的 AI 框架，用外部数据和世界知识增强回答，使输出更准确、更新、更贴合特定需求。

## 关键贡献

- RAG pipeline 包括检索、预处理和 grounded generation。
- 检索质量是关键：如果取回信息不相关，生成可能“有依据但离题或错误”。
- RAG 需要用 coherence、fluency、groundedness、safety、instruction following、question answering quality 等指标评估。
- RAG 的优化点包括搜索引擎、数据源质量、文档布局解析、chunking 策略和用户问题改写。

## 对 AI 知识体系的归属

- 主归属：4. 上下文与知识层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[sources/rag-2020]]
- [[concepts/微调RAG上下文工程选择框架]]
