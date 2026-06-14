---
address: c-000265
type: source
title: "Prover-Verifier Games improve legibility of language model outputs"
source_url: https://openai.com/index/prover-verifier-games-improve-legibility/
source_type: research-blog
author: "OpenAI"
published: 2024-07-17
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - reasoning
  - verifier
  - legibility
status: active
related:
  - "[[concepts/ReasoningEvalVerifier边界]]"
sources:
  - "https://arxiv.org/abs/2407.13692"
---

# Prover-Verifier Games improve legibility of language model outputs

**来源**：OpenAI Research
**URL**：https://openai.com/index/prover-verifier-games-improve-legibility/

## 摘要

OpenAI 研究 prover-verifier games：训练强模型生成弱 verifier 和人类更容易检查的解答。核心问题不是只让答案正确，而是让答案在复杂任务中可读、可查、可验证。

## 关键贡献

- 指出只优化正确率可能让解答更难被人类快速验证。
- 将 legibility / checkability 纳入可靠性目标，而不仅是最终 accuracy。
- 证明让弱 verifier 更容易验证的输出，也能让人类更容易评估。
- 把 verifier 从“评分器”推进到“塑造模型输出可验证性”的训练目标。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：3. 推理与能力层、2. 模型构建层
- 作用：提醒 reasoning eval 不能只追正确率，还要关注可检查性和人类监督成本。

## 关联

- [[concepts/ReasoningEvalVerifier边界]]
- [[Research: Reasoning eval verifier 边界]]
