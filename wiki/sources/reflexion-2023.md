---
address: c-000214
type: source
title: "Reflexion: Language Agents with Verbal Reinforcement Learning"
source_url: https://arxiv.org/abs/2303.11366
source_type: paper
author: "Noah Shinn et al."
published: 2023-03-20
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - agents
  - reflection
  - memory
status: active
related:
  - "[[concepts/Dream与SelfImprovement工程原语]]"
---

# Reflexion: Language Agents with Verbal Reinforcement Learning

**来源**：arXiv
**URL**：https://arxiv.org/abs/2303.11366

## 摘要

Reflexion 提出让 language agent 不通过改权重学习，而是把反馈写成语言反思，存入 episodic memory，在后续尝试中使用。

## 关键贡献

- 将 scalar 或自然语言反馈转成 verbal reflection。
- 反思内容进入 episodic memory buffer，用来改进后续决策。
- 它是 self-improvement 的 L1 形式：外部记忆层学习，而不是模型权重学习。

## 对 AI 知识体系的归属

- 主归属：8. 自我改进与前沿层
- 交叉链接：4. 上下文与知识层
- 作用：提供“反思 → 记忆 → 下一次更好”的早期稳定原语。

## 关联

- [[concepts/Dream与SelfImprovement工程原语]]
- [[Research: Dream 与 self-improvement 工程原语]]
