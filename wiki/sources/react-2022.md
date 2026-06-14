---
address: c-000177
type: source
title: "ReAct: Synergizing Reasoning and Acting in Language Models"
source_url: https://arxiv.org/abs/2210.03629
source_type: paper
author: "Yao et al."
published: 2022
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - agents
  - react
  - paper
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/Loop机制]]"
---

# ReAct: Synergizing Reasoning and Acting in Language Models

**来源**：arXiv:2210.03629
**作者**：Shunyu Yao 等
**发布时间**：2022

## 摘要

ReAct 提出让语言模型交错生成 reasoning traces 和 task-specific actions。推理帮助模型计划、追踪和处理异常；行动让模型访问外部知识库或环境。

## 关键贡献

- 把 LLM 从单次回答推进到“推理 + 行动”的循环。
- 是上下文与知识层进入 Agent 系统层的关键桥梁。
- 它让 agent 的可解释性提升，因为 trace 暴露了计划与工具使用路径。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 上游：3. 推理能力层、4. 上下文与知识层
- 下游：6. 评估与可靠性层

## 关联

- [[concepts/Loop机制]]
- [[domains/AI知识体系]]
- [[Research: AI知识体系总览]]
