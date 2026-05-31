---
address: c-000580
type: source
title: "Memory Poisoning Attack and Defense on Memory Based LLM-Agents"
source_url: https://arxiv.org/abs/2601.05504
source_type: paper
author: "Balachandra Devarangadi Sunil, Isheeta Sinha, Piyush Maheshwari, Shantanu Todmal, Shreyan Mallik, Shuchi Mishra"
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - memory
  - security
  - defense
status: active
related:
  - "[[concepts/MemorySkillGovernanceDrift边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
---

# Memory Poisoning Attack and Defense on Memory Based LLM-Agents

**来源**：arXiv:2601.05504
**URL**：https://arxiv.org/abs/2601.05504

## 摘要

该论文系统评估 memory-based LLM agents 的 memory poisoning attack and defense，研究初始 memory state、诱导 prompt 数量和 retrieval parameters 对攻击鲁棒性的影响，并提出 input/output moderation 与 trust-aware memory sanitization 防御。

## 对本体系的贡献

- 给 memory governance 提供防御方向：composite trust scoring、temporal decay、pattern filtering、trust-aware retrieval。
- 说明防御阈值要校准：过严会阻断全部 memory，过松会漏掉 subtle attacks。
- 支撑 memory write precision、poison detection、stale/decay 和 retrieval trust tier 作为评估指标。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：4. 上下文与知识层

## 关联

- [[concepts/MemorySkillGovernanceDrift边界]]
- [[Research: Memory skill governance drift 边界]]
