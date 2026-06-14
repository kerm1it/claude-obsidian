---
address: c-000268
type: source
title: "Rewarding Progress: Scaling Automated Process Verifiers for LLM Reasoning"
source_url: https://arxiv.org/abs/2410.08146
source_type: paper
author: "Amrith Setlur et al."
published: 2024-10-10
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - reasoning
  - process-verifiers
  - reinforcement-learning
status: active
related:
  - "[[concepts/ReasoningEvalVerifier边界]]"
  - "[[concepts/TestTimeCompute]]"
---

# Rewarding Progress: Scaling Automated Process Verifiers for LLM Reasoning

**来源**：arXiv
**URL**：https://arxiv.org/abs/2410.08146

## 摘要

论文研究如何设计自动化 process verifier。核心观点：process reward 不应只评价当前步骤是否看起来正确，而应衡量这一步是否提高未来得到正确答案的概率。

## 关键贡献

- 将 PRM 的目标定义为 progress / step-level advantage。
- 区分 base policy 与 prover policy，提出用不同 prover 生成信号来改进更强 base policy。
- Process advantage verifier 可用于 test-time search，也可作为 online RL 的 dense reward。
- 相比 ORM，PAV 在论文实验中提升搜索准确率和计算效率。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：3. 推理与能力层、2. 模型构建层
- 作用：把 PRM 从 step correctness 扩展为“是否推进解题状态”的过程信号。

## 关联

- [[concepts/ReasoningEvalVerifier边界]]
- [[concepts/TestTimeCompute]]
- [[Research: Reasoning eval verifier 边界]]
