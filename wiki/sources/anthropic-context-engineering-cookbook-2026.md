---
address: c-000193
type: source
title: "Context engineering: memory, compaction, and tool clearing"
source_url: https://platform.claude.com/cookbook/tool-use-context-engineering-context-engineering-tools
source_type: cookbook
author: "Anthropic"
published: 2026-03-20
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - context-engineering
  - memory
status: active
related:
  - "[[concepts/RAG与Memory边界]]"
  - "[[concepts/上下文工程]]"
---

# Context engineering: memory, compaction, and tool clearing

**来源**：Claude Cookbook
**URL**：https://platform.claude.com/cookbook/tool-use-context-engineering-context-engineering-tools

## 摘要

Anthropic cookbook 比较长任务 agent 的上下文工程策略：memory、compaction、tool clearing。核心问题是工具结果、模型推理和用户消息会不断积累，最终触发硬性上下文上限或让模型为低价值 token 付出成本。

## 关键贡献

- Context 是有限资源，且有递减收益。
- 长任务需要组合策略：memory、compaction、tool clearing、subagents、programmatic tool calling。
- Memory 在这里不是普通文档检索，而是长任务和跨任务的状态管理原语。

## 对 AI 知识体系的归属

- 主归属：4. 上下文与知识层
- 交叉链接：5. Agent 系统层、8. 自我改进与前沿层

## 关联

- [[concepts/RAG与Memory边界]]
- [[concepts/上下文工程]]
