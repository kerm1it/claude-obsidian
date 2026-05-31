---
address: c-000192
type: synthesis
title: "Research: RAG 与 Memory 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - rag
  - memory
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/RAG与Memory边界]]"
  - "[[concepts/渐进式上下文注入]]"
  - "[[concepts/四层记忆整合]]"
sources:
  - "[[sources/anthropic-context-engineering-cookbook-2026]]"
  - "[[sources/openai-agent-memory-2026]]"
  - "[[sources/openai-retrieval-docs-2026]]"
  - "[[sources/google-vertex-rag-engine-2026]]"
  - "[[sources/himem-2026]]"
  - "[[sources/memir-typed-memory-2026]]"
  - "[[sources/claude-mem-2026-05-13]]"
  - "[[sources/agentmemory-2026-05-13]]"
  - "[[sources/memory-dreaming-self-learning-agents-2026-05-11]]"
---

# Research: RAG 与 Memory 边界

## Overview

RAG 与 Memory 共享检索、索引、chunking 和上下文注入技术，但它们的系统角色不同。RAG 面向外部知识，目标是让模型回答有依据、可更新、可追溯；Memory 面向长期主体连续性，目标是让 agent 跨任务保留状态、偏好、经验和程序化规则。

## Key Findings

- Anthropic 的 context engineering cookbook 将 memory、compaction、tool clearing 放在长任务上下文管理策略中，强调上下文 token 有递减收益。（Source: [[sources/anthropic-context-engineering-cookbook-2026]]）
- OpenAI Agents SDK memory 使用 progressive disclosure：先注入小摘要，再按需搜索 memory index，只有相关时打开详细 rollout summary；并提醒 memory 可能 stale，应信任当前环境。（Source: [[sources/openai-agent-memory-2026]]）
- OpenAI Retrieval 文档中的 vector store 是 semantic search / file search 的容器，适合做 RAG 的外部知识检索底座。（Source: [[sources/openai-retrieval-docs-2026]]）
- Google Vertex RAG Engine 把 RAG 定义为 context-augmented LLM 应用的数据框架，并在 API 中区分 document corpus 与 memory corpus。（Source: [[sources/google-vertex-rag-engine-2026]]）
- HiMem 认为长期 memory 系统仍存在适应性、可扩展性和自演化限制，因此提出层级长期记忆框架支持 construction、retrieval、dynamic updating。（Source: [[sources/himem-2026]]）
- MemIR 指出把长期交互存成非结构化平面文本会造成 provenance-role collapse；memory 需要区分证据、检索线索和事实 claim。（Source: [[sources/memir-typed-memory-2026]]）
- 本 vault 已有 [[concepts/渐进式上下文注入]]、[[concepts/四层记忆整合]]、[[concepts/AgentMemoryAPI]]，三者共同说明 memory 不只是向量检索，而是写入、巩固、衰减、冲突解决和权限控制。

## Boundary

| 判断问题 | 如果是 | 归属 |
|---|---|---|
| 信息来自可引用外部资料吗？ | 文档、网页、代码库、政策 | RAG |
| 信息来自交互历史吗？ | 用户偏好、历史任务、失败模式 | Memory |
| 信息需要频繁更新且可重新索引吗？ | 产品文档、API、政策 | RAG |
| 信息需要随 agent 使用而演化吗？ | 经验、偏好、程序规则 | Memory |
| 信息是当前任务临时状态吗？ | checklist、scratchpad | Short-term memory / context |
| 信息可变且旧值危险吗？ | 账号状态、配置、任务进度 | Memory with provenance + staleness guard |

## Open Questions

- Memory 的最小可用 schema 应该是文件系统、关系表、图，还是 typed atom。
- RAG corpus 与 memory store 什么时候应该共享索引，什么时候必须隔离权限和 lifecycle。
- Dream/consolidation 的触发条件应基于时间、任务结束、失败案例，还是 eval regression。

## Filed Result

本轮归档为 [[concepts/RAG与Memory边界]]，并回填 [[domains/AI知识体系]] 第 4 层；下一步继续研究 Agent harness 与 trace/eval。
