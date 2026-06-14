---
address: c-000263
type: source
title: "Solving math word problems"
source_url: https://openai.com/index/solving-math-word-problems/
source_type: research-blog
author: "OpenAI"
published: 2021-10-29
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - reasoning
  - verifiers
  - gsm8k
status: active
related:
  - "[[concepts/ReasoningEvalVerifier边界]]"
  - "[[concepts/TestTimeCompute]]"
sources:
  - "https://arxiv.org/abs/2110.14168"
---

# Solving math word problems

**来源**：OpenAI Research
**URL**：https://openai.com/index/solving-math-word-problems/
**论文**：https://arxiv.org/abs/2110.14168

## 摘要

OpenAI 在 GSM8K 数学文字题上训练 verifier 来判断模型生成解答是否正确。测试时先生成多个候选解，再用 verifier 选择最高分解答。

## 关键贡献

- 把 reasoning 任务从单次生成改成 `generate candidates → verify/rank → select`。
- 明确 verifier 受益于“验证比生成更简单”和候选解 optionality。
- GSM8K 成为评估多步自然语言数学推理的基础数据集。
- 也指出 verifier 数据太小时可能过拟合最终答案，而不是学习推理性质。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：3. 推理与能力层
- 作用：提供 outcome verifier 与 best-of-N reasoning 的早期工程模式。

## 关联

- [[concepts/ReasoningEvalVerifier边界]]
- [[concepts/TestTimeCompute]]
- [[Research: Reasoning eval verifier 边界]]
