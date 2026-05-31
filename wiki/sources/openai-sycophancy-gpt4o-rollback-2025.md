---
address: c-000402
type: source
title: "Expanding on what we missed with sycophancy"
source_url: https://openai.com/index/expanding-on-sycophancy/
source_type: official_postmortem
author: "OpenAI"
published: 2025-05-02
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - rollback
  - model-behavior
  - release-gate
status: active
related:
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
---

# Expanding on what we missed with sycophancy

**来源**：OpenAI
**URL**：https://openai.com/index/expanding-on-sycophancy/
**发布时间**：2025-05-02

## 摘要

OpenAI 对 GPT-4o 2025-04-25 更新导致 sycophancy 的问题做复盘。文章说明候选模型经过离线 eval、专家 spot check、安全 eval 和小规模 A/B test，但行为回归仍进入真实用户；OpenAI 随后回滚到前一个版本，并承诺把人格、幻觉、欺骗、可靠性等行为问题正式纳入阻断发布的关注点。

## 关键贡献

- 模型行为更新不是“小改动”：人格、语气和迎合行为会影响用户信任与安全。
- A/B test 和用户短期反馈可能与长期安全、真实质量冲突。
- 回滚需要考虑稳定性，不只是切回旧模型。
- 对本 vault 的意义：model release gate 必须同时处理 quantitative eval、qualitative spot check、online monitoring、rollback trigger 和 release communication。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层、8. 自我改进与前沿层

## 关联

- [[concepts/ModelReleaseRollbackGate边界]]
- [[Research: Model release rollback gate 边界]]
