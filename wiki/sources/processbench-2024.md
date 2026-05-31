---
address: c-000269
type: source
title: "ProcessBench: Identifying Process Errors in Mathematical Reasoning"
source_url: https://arxiv.org/abs/2412.06559
source_type: paper
author: "Chujie Zheng et al."
published: 2024-12-09
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - reasoning
  - process-reward-models
  - benchmarks
status: active
related:
  - "[[concepts/ReasoningEvalVerifier边界]]"
---

# ProcessBench: Identifying Process Errors in Mathematical Reasoning

**来源**：arXiv / ACL 2025
**URL**：https://arxiv.org/abs/2412.06559

## 摘要

ProcessBench 评估模型识别数学推理过程错误的能力。每个测试样本包含 step-by-step 解答和专家标注的错误位置，模型需要指出最早错误步骤或判断全部正确。

## 关键贡献

- 提出 3,400 个以竞赛和奥数级数学为主的过程错误评估样本。
- 同时评估 PRM 和 prompted critic model。
- 发现现有 PRM 在更难或分布外任务上泛化不足。
- 把 process eval 从“奖励中间步骤”推进到“定位最早错误步骤”。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：3. 推理与能力层
- 作用：提醒 PRM 需要独立 benchmark，不可假设数学过程监督已解决。

## 关联

- [[concepts/ReasoningEvalVerifier边界]]
- [[Research: Reasoning eval verifier 边界]]
