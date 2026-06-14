---
address: c-000196
type: source
title: "Vertex AI RAG Engine overview and API"
source_url: https://docs.cloud.google.com/vertex-ai/generative-ai/docs/rag-engine/rag-overview
source_type: documentation
author: "Google Cloud"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - rag
  - memory
  - google-cloud
status: active
related:
  - "[[concepts/RAG与Memory边界]]"
---

# Vertex AI RAG Engine overview and API

**来源**：Google Cloud Documentation
**URL**：https://docs.cloud.google.com/vertex-ai/generative-ai/docs/rag-engine/rag-overview

## 摘要

Vertex AI RAG Engine 是用于构建 context-augmented LLM 应用的数据框架。它通过 ingestion、transformation、indexing、retrieval 将私有知识补进模型上下文。

## 关键贡献

- RAG Engine 解决模型不了解组织私有知识的问题。
- API 中区分 document corpus 与 memory corpus；memory corpus 可作为 Gemini Live API 的 memory store。
- 这说明 RAG 与 memory 在平台层可能共享检索设施，但 corpus type 和生命周期需要区分。

## 对 AI 知识体系的归属

- 主归属：4. 上下文与知识层
- 交叉链接：5. Agent 系统层

## 关联

- [[concepts/RAG与Memory边界]]
- [[sources/google-cloud-rag-overview]]
