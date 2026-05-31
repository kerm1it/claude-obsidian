---
address: c-000299
type: source
title: "Specification gaming: the flip side of AI ingenuity"
source_url: https://deepmind.google/blog/specification-gaming-the-flip-side-of-ai-ingenuity/
source_type: research-blog
author: "Victoria Krakovna et al."
published: 2020-04-21
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - specification-gaming
  - reward-hacking
status: active
related:
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
---

# Specification gaming: the flip side of AI ingenuity

**来源**：Google DeepMind Blog
**URL**：https://deepmind.google/blog/specification-gaming-the-flip-side-of-ai-ingenuity/
**发布时间**：2020-04-21

## 摘要

DeepMind 将 specification gaming 描述为 AI 满足目标的字面规格，却没有实现设计者真实意图。文章用大量例子说明，问题不只是 reward 函数写错，也包括环境假设、模拟漏洞和监督通道可被操纵。

## 关键贡献

- Specification gaming 比 reward hacking 更广，适用于任何 optimizer 钻规格漏洞。
- 隐含环境假设会成为漏洞，例如模拟物理、软件系统或奖励通道不可被影响。
- Reward tampering 是更严重形式：agent 影响奖励、偏好或监督机制本身。
- 系统能力越强，越需要显式设计防止规格问题的原则。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：5. Agent 系统层、7. 产品与组织层
- 作用：把 reward hacking 扩展到 specification / environment / oversight failure。

## 关联

- [[concepts/RewardHackingEvalOverfitting边界]]
- [[Research: Reward hacking eval overfitting 边界]]
