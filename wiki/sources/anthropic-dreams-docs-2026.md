---
address: c-000211
type: source
title: "Dreams - Claude Managed Agents"
source_url: https://platform.claude.com/docs/en/managed-agents/dreams
source_type: documentation
author: "Anthropic"
published: 2026-05-30
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - dreaming
  - managed-agents
  - memory
status: active
related:
  - "[[concepts/Dream与SelfImprovement工程原语]]"
  - "[[concepts/AnthropicDreaming]]"
---

# Dreams - Claude Managed Agents

**来源**：Claude API Docs
**URL**：https://platform.claude.com/docs/en/managed-agents/dreams

## 摘要

Claude Managed Agents 的 Dreams 文档把 dream 定义为异步 job：读取已有 memory store 和历史 sessions，生成一个新的 output memory store，用来清理重复、替换过时或矛盾条目，并提取新洞察。

## 关键贡献

- Dream 的输入是 memory store + 1 到 100 个 past sessions。
- Dream 不修改原始输入 store，而是生成独立输出 store，便于审查、替换或丢弃。
- Dream 有明确 lifecycle：pending、running、completed、failed、canceled。
- 运行中的 dream 可通过 session event stream 观察，失败后输出 store 仍可检查。

## 对 AI 知识体系的归属

- 主归属：8. 自我改进与前沿层
- 交叉链接：4. 上下文与知识层、6. 评估与可靠性层
- 作用：把 dream 从隐喻变成可审查、可回滚的 memory consolidation job。

## 关联

- [[concepts/Dream与SelfImprovement工程原语]]
- [[concepts/AnthropicDreaming]]
- [[Research: Dream 与 self-improvement 工程原语]]
