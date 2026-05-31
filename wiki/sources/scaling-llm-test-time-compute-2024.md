---
address: c-000230
type: source
title: "Scaling LLM Test-Time Compute Optimally"
source_url: https://arxiv.org/abs/2408.03314
source_type: paper
author: "Charlie Snell, Jaehoon Lee, Kelvin Xu, Aviral Kumar"
published: 2024-08-06
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - test-time-compute
  - reasoning
  - scaling
status: active
related:
  - "[[concepts/TestTimeCompute]]"
---

# Scaling LLM Test-Time Compute Optimally

**来源**：arXiv:2408.03314
**URL**：https://arxiv.org/abs/2408.03314

## 摘要

论文研究如何在推理阶段用固定但非平凡的额外计算提升 LLM 表现。作者比较搜索 verifier reward model 和 test-time adaptive distribution update，并提出 compute-optimal 分配策略。

## 关键贡献

- Test-time compute 的效果依赖 prompt 难度。
- 盲目 best-of-N 不是最优策略；按题目难度自适应分配计算更高效。
- Compute-optimal 策略可显著提高 test-time scaling 效率。
- 在部分问题上，小模型加推理时计算可以超过更大模型。

## 对 AI 知识体系的归属

- 主归属：3. 推理与能力层
- 交叉链接：2. 模型构建层、6. 评估与可靠性层
- 作用：给出“运行时算力 vs 模型参数规模”的权衡框架。

## 关联

- [[concepts/TestTimeCompute]]
- [[Research: 推理时计算与 reasoning]]
