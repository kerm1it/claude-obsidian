---
address: c-000578
type: source
title: "Hidden in Memory"
source_url: https://arxiv.org/abs/2605.15338
source_type: paper
author: "Sidharth Pulipaka, Stanislau Hlebik, Leonidas Raghav, Sahar Abdelnabi, Vyas Raina, Ivaxi Sheth, Mario Fritz"
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - memory
  - sleeper-poisoning
  - security
status: active
related:
  - "[[concepts/MemorySkillGovernanceDrift边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
---

# Hidden in Memory

**来源**：arXiv:2605.15338
**URL**：https://arxiv.org/abs/2605.15338
**标题**：Hidden in Memory: Sleeper Memory Poisoning in LLM Agents

## 摘要

论文研究 sleeper memory poisoning：攻击者通过外部文档、网页或代码仓库等上下文诱导 assistant 写入伪造 memory。该 memory 可以休眠，并在多个后续会话中被检索和使用，影响 agent 行为。

## 对本体系的贡献

- 说明 memory poisoning 不需要立即触发，可能在未来任务中跨会话激活。
- 支撑 memory governance 需要 write/retrieve/use 三段评估，而不是只看写入时是否安全。
- 强化 memory expiry、scope、source trust、quarantine 和 periodic rescan 的必要性。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：4. 上下文与知识层、7. 产品与组织层

## 关联

- [[concepts/MemorySkillGovernanceDrift边界]]
- [[Research: Memory skill governance drift 边界]]
