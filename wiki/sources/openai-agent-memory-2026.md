---
address: c-000194
type: source
title: "Agent memory"
source_url: https://openai.github.io/openai-agents-js/guides/sandbox-agents/memory/
source_type: documentation
author: "OpenAI Agents SDK"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - agents
  - memory
status: active
related:
  - "[[concepts/RAG与Memory边界]]"
  - "[[concepts/渐进式上下文注入]]"
  - "[[concepts/MemorySkillGovernanceDrift边界]]"
---

# Agent memory

**来源**：OpenAI Agents SDK
**URL**：https://openai.github.io/openai-agents-js/guides/sandbox-agents/memory/

## 摘要

OpenAI Agents SDK 的 memory 文档使用 progressive disclosure：运行开始时注入小型 memory summary；如果 prior work 相关，再搜索 memory index；必要时打开更详细的 prior rollout summaries。

## 关键贡献

- Memory 读取应分层：summary → index → detailed summaries。
- Memory 可能过时，agent 应把 memory 当 guidance，并优先信任当前环境。
- 默认 liveUpdate 允许 agent 在发现 stale memory 时更新 memory index；延迟敏感任务可关闭。

## 对 AI 知识体系的归属

- 主归属：4. 上下文与知识层
- 交叉链接：5. Agent 系统层、6. 评估与可靠性层

## 关联

- [[concepts/RAG与Memory边界]]
- [[concepts/渐进式上下文注入]]
- [[concepts/MemorySkillGovernanceDrift边界]]
