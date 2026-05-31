---
address: c-000195
type: source
title: "Retrieval"
source_url: https://developers.openai.com/api/docs/guides/retrieval
source_type: documentation
author: "OpenAI"
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - retrieval
  - vector-store
  - rag
status: active
related:
  - "[[concepts/RAG与Memory边界]]"
  - "[[sources/rag-2020]]"
---

# Retrieval

**来源**：OpenAI Docs
**URL**：https://developers.openai.com/api/docs/guides/retrieval

## 摘要

OpenAI Retrieval 文档将 vector stores 定义为 Retrieval API 和 file search tool 的语义搜索容器。文件加入 vector store 后会被自动 chunk、embedding 和 indexing。

## 关键贡献

- Vector store 是 RAG 的基础设施，而不是完整 memory 系统。
- Retrieval 解决“找相关外部信息”问题；memory 还需要写入策略、生命周期、冲突处理和 stale guard。

## 对 AI 知识体系的归属

- 主归属：4. 上下文与知识层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/RAG与Memory边界]]
- [[sources/rag-2020]]
