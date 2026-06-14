---
address: c-000229
type: source
title: "Building with extended thinking"
source_url: https://platform.claude.com/docs/en/build-with-claude/extended-thinking
source_type: documentation
author: "Anthropic"
published: 2026-05-30
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - reasoning
  - extended-thinking
  - anthropic
status: active
related:
  - "[[concepts/TestTimeCompute]]"
  - "[[concepts/AdaptiveThinking]]"
  - "[[concepts/EffortDial]]"
  - "[[concepts/TaskBudgets]]"
---

# Building with extended thinking

**来源**：Claude API Docs
**URL**：https://platform.claude.com/docs/en/build-with-claude/extended-thinking

## 摘要

Anthropic 文档把 extended thinking、adaptive thinking、effort、thinking budget 和 tool use 组合成 API 控制面。文档强调 thinking 可以与 tool use 一起使用，但在同一 assistant turn 中需要保持 thinking mode 和 thinking blocks 的连续性。

## 关键贡献

- Extended thinking 把推理 token 变成可配置资源。
- Adaptive thinking 让模型按步骤校准是否需要 deeper reasoning。
- Effort 是质量、延迟、token 使用之间的控制旋钮。
- 与 tool use 结合时，thinking blocks 必须被保留，tool loop 属于同一 assistant turn。
- 对长程 agentic coding、computer use 和混合难度任务，文档建议评估 medium/high effort。

## 对 AI 知识体系的归属

- 主归属：3. 推理与能力层
- 交叉链接：5. Agent 系统层、6. 评估与可靠性层
- 作用：说明推理时计算在产品 API 中如何被控制和约束。

## 关联

- [[concepts/TestTimeCompute]]
- [[concepts/AdaptiveThinking]]
- [[concepts/EffortDial]]
- [[Research: 推理时计算与 reasoning]]
