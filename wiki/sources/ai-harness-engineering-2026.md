---
address: c-000207
type: source
title: "AI Harness Engineering: A Runtime Substrate for Foundation-Model Software Agents"
source_url: https://arxiv.org/abs/2605.13357
source_type: paper
author: "Hailin Zhong, Shengxin Zhu"
published: 2026-05-13
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - agents
  - harness
  - engineering
status: active
related:
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[domains/AI知识体系]]"
---

# AI Harness Engineering: A Runtime Substrate for Foundation-Model Software Agents

**来源**：arXiv
**URL**：https://arxiv.org/abs/2605.13357

## 摘要

AI Harness Engineering 将 harness 视为 foundation-model software agents 的 runtime substrate，而不是临时胶水代码。论文把软件工程能力定位为 model-harness-environment 系统能力。

## 关键贡献

- 论文列出 11 个 harness 职责：任务规格、上下文选择、工具访问、项目记忆、任务状态、观测、失败归因、验证、权限、熵审计、干预记录。
- H0-H3 ladder 描述 harness 支持从低到高的层次。
- Trace-based evaluation protocol 将每次 agent run 转成可审计 episode package。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：4. 上下文与知识层、6. 评估与可靠性层
- 作用：给 harness 提供稳定工程定义。

## 关联

- [[concepts/AgentHarness与TraceEval]]
- [[domains/AI知识体系]]
- [[Research: Agent harness 与 trace eval]]
