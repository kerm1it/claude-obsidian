---
address: c-000232
type: source
title: "Self-Consistency Improves Chain of Thought Reasoning in Language Models"
source_url: https://arxiv.org/abs/2203.11171
source_type: paper
author: "Xuezhi Wang et al."
published: 2023-03-07
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - reasoning
  - chain-of-thought
  - self-consistency
status: active
related:
  - "[[concepts/TestTimeCompute]]"
---

# Self-Consistency Improves Chain of Thought Reasoning in Language Models

**来源**：arXiv:2203.11171
**URL**：https://arxiv.org/abs/2203.11171

## 摘要

Self-consistency 把 CoT 从单条 greedy reasoning path 扩展为多条采样 reasoning paths，再通过答案一致性选择结果。它是最清晰的早期 test-time compute 策略之一。

## 关键贡献

- 多样化采样推理路径可以超过单条 greedy CoT。
- 对有唯一正确答案的复杂推理题，答案一致性可作为弱 verifier。
- 成本主要来自多次采样，收益必须用任务 eval 衡量。

## 对 AI 知识体系的归属

- 主归属：3. 推理与能力层
- 交叉链接：6. 评估与可靠性层
- 作用：提供“多路径推理 + 一致性选择”的运行时扩展模式。

## 关联

- [[concepts/TestTimeCompute]]
- [[Research: 推理时计算与 reasoning]]
