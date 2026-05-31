---
address: c-000270
type: source
title: "Process Reward Models That Think"
source_url: https://arxiv.org/abs/2504.16828
source_type: paper
author: "Muhammad Khalifa et al."
published: 2025-04-23
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - reasoning
  - process-reward-models
  - verifier
status: active
related:
  - "[[concepts/ReasoningEvalVerifier边界]]"
  - "[[concepts/TestTimeCompute]]"
---

# Process Reward Models That Think

**来源**：arXiv
**URL**：https://arxiv.org/abs/2504.16828

## 摘要

论文提出 ThinkPRM：一种会生成 verification CoT 的 generative process reward model。它尝试用更少 step-level 标签训练可解释 verifier，并在 best-of-N 与 reward-guided search 场景中使用。

## 关键贡献

- 将 PRM 从纯判别式 scorer 扩展为会生成验证推理的 generative verifier。
- 目标是减少对大规模人工 step labels 的依赖。
- 在 ProcessBench、MATH-500、AIME 2024 等任务中报告了对 LLM-as-a-Judge 和判别式 PRM 的改进。
- 强调 verification compute 也是 test-time compute 的一部分。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：3. 推理与能力层
- 作用：代表 2025 年后 PRM 从静态 scorer 向 reasoning verifier 演化的方向。

## 关联

- [[concepts/ReasoningEvalVerifier边界]]
- [[concepts/TestTimeCompute]]
- [[Research: Reasoning eval verifier 边界]]
