---
address: c-000221
type: source
title: "Tools - OpenAI Agents SDK"
source_url: https://openai.github.io/openai-agents-python/tools/
source_type: documentation
author: "OpenAI"
published: 2026-05-30
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - agents
  - tools
  - openai
status: active
related:
  - "[[concepts/Skill与ToolMemory边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
---

# Tools - OpenAI Agents SDK

**来源**：OpenAI Agents SDK documentation
**URL**：https://openai.github.io/openai-agents-python/tools/

## 摘要

OpenAI Agents SDK 文档把 tools 定义为 agent 可以采取的动作，例如获取数据、运行代码、调用外部 API 或使用电脑。文档列出 hosted tools、runtime tools、function tools、agents as tools 和 Codex tool 等类别。

## 关键贡献

- Tool 的核心是“执行动作”，不是“描述怎么做”。
- Function tools 用 schema 把 Python 函数暴露给 agent。
- Agents as tools 把另一个 agent 暴露为可调用能力。
- Tool 需要 guardrails、timeouts、error handling、conditional enabling 等运行时约束。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：4. 上下文与知识层、6. 评估与可靠性层
- 作用：给 skill/tool 边界提供官方工程定义：skill 组织程序性知识，tool 执行动作。

## 关联

- [[concepts/Skill与ToolMemory边界]]
- [[concepts/AgentHarness与TraceEval]]
- [[Research: Skill 与 tool memory workflow 边界]]
