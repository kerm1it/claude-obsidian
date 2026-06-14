---
address: c-000572
type: source
title: "Darwin Godel Machine"
source_url: https://arxiv.org/abs/2505.22954
source_type: paper
author: "Jenny Zhang, Shengran Hu, Cong Lu, Robert Lange, Jeff Clune"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - self-improvement
  - coding-agents
  - open-endedness
status: active
related:
  - "[[concepts/SelfImprovementGateChangeRiskBudget边界]]"
  - "[[concepts/Dream与SelfImprovement工程原语]]"
---

# Darwin Godel Machine

**来源**：arXiv:2505.22954
**URL**：https://arxiv.org/abs/2505.22954
**标题**：Darwin Godel Machine: Open-Ended Evolution of Self-Improving Agents

## 摘要

Darwin Godel Machine 是 self-improving coding agent 研究：系统迭代修改自己的代码，并用 coding benchmarks 经验验证候选版本。它维护 generated agents archive，通过 open-ended exploration 形成多条候选路径，并在 SWE-bench 与 Polyglot 等基准上展示改进。

## 对本体系的贡献

- 说明“自我改进”在工程上通常是 archive + proposal + benchmark validation，而不是数学上证明最优。
- 说明 self-modification 必须依赖 sandbox、benchmark、human oversight 等安全边界。
- 支撑 change-risk budget：候选分支可以大量探索，但进入真实系统必须有证据和筛选。

## 对 AI 知识体系的归属

- 主归属：8. 自我改进与前沿层
- 交叉链接：5. Agent 系统层、6. 评估与可靠性层

## 关联

- [[concepts/SelfImprovementGateChangeRiskBudget边界]]
- [[concepts/Dream与SelfImprovement工程原语]]
- [[Research: Self-improvement gate change-risk budget 边界]]
