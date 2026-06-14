---
address: c-000223
type: source
title: "SkillsBench"
source_url: https://arxiv.org/abs/2602.12670
source_type: paper
author: "Xiangyi Li et al."
published: 2026-03-13
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - agent-skills
  - benchmark
  - evals
status: active
related:
  - "[[concepts/Skill与ToolMemory边界]]"
---

# SkillsBench

**来源**：arXiv:2602.12670
**URL**：https://arxiv.org/abs/2602.12670

## 摘要

SkillsBench 是评估 agent skills 是否真的提升任务表现的 benchmark。它包含 86 个任务、11 个领域、curated skills 和 deterministic verifiers，并比较 no skills、curated skills、self-generated skills 三种条件。

## 关键贡献

- Curated skills 平均提升 pass rate，但不同领域差异很大。
- 部分任务安装 skill 后表现下降，说明 skill 需要 eval，而不是越多越好。
- Self-generated skills 平均没有收益，说明当前模型还不能稳定自动写出有用程序性知识。
- 聚焦的 2-3 个模块式 skill 优于把完整文档全部塞入上下文。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：4. 上下文与知识层、5. Agent 系统层
- 作用：为 skill 提供任务级验收标准和“不要盲目安装”的证据。

## 关联

- [[concepts/Skill与ToolMemory边界]]
- [[Research: Skill 与 tool memory workflow 边界]]
