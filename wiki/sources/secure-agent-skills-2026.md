---
address: c-000259
type: source
title: "Towards Secure Agent Skills"
source_url: https://arxiv.org/abs/2604.02837
source_type: paper
author: "Zhiyuan Li et al."
published: 2026-04-03
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - agent-skills
  - security
  - lifecycle
status: active
related:
  - "[[concepts/SkillLibraryRouting生命周期]]"
---

# Towards Secure Agent Skills

**来源**：arXiv:2604.02837
**URL**：https://arxiv.org/abs/2604.02837

## 摘要

论文对 Agent Skills framework 做系统安全分析，将完整生命周期拆成 Creation、Distribution、Deployment、Execution 四个阶段，并给出 threat taxonomy 和 defense directions。

## 关键贡献

- Agent Skill 生命周期不是只有执行阶段，创建、分发、部署都会引入攻击面。
- 结构性风险包括 data-instruction boundary 缺失、single-approval persistent trust、缺乏强制 marketplace security review。
- 论文用真实安全事件验证 taxonomy。
- 防御需要跨作者、registry、agent runtime、组织部署策略共同完成。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：4. 上下文与知识层、5. Agent 系统层
- 作用：提供 skill lifecycle 安全治理框架。

## 关联

- [[concepts/SkillLibraryRouting生命周期]]
- [[Research: Skill library routing lifecycle]]
