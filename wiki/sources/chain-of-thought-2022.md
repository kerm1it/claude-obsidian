---
address: c-000231
type: source
title: "Chain-of-Thought Prompting Elicits Reasoning in Large Language Models"
source_url: https://arxiv.org/abs/2201.11903
source_type: paper
author: "Jason Wei et al."
published: 2023-01-10
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - reasoning
  - chain-of-thought
status: active
related:
  - "[[concepts/TestTimeCompute]]"
---

# Chain-of-Thought Prompting Elicits Reasoning in Large Language Models

**来源**：arXiv:2201.11903
**URL**：https://arxiv.org/abs/2201.11903

## 摘要

Chain-of-Thought 论文提出用少量带中间推理步骤的示例，引导大模型在复杂推理任务中生成中间 reasoning steps。它是现代 reasoning / test-time compute 的早期基础之一。

## 关键贡献

- CoT 说明模型在推理阶段外显中间步骤可以提升复杂任务表现。
- 论文覆盖 arithmetic、commonsense、symbolic reasoning。
- CoT 的收益与模型规模相关，代表“同一模型运行方式不同，能力表现不同”。

## 对 AI 知识体系的归属

- 主归属：3. 推理与能力层
- 交叉链接：4. 上下文与知识层
- 作用：提供 reasoning trace 作为推理时计算最小形式的证据。

## 关联

- [[concepts/TestTimeCompute]]
- [[Research: 推理时计算与 reasoning]]
