---
address: c-000576
type: source
title: "MemMorph: Tool Hijacking in LLM Agents via Memory Poisoning"
source_url: https://arxiv.org/abs/2605.26154
source_type: paper
author: "Xuanye Zhang, Yongsen Zheng, Zhuqin Xu, Kaiyu Zhou, Bowen Shen, Haoran Ou, Tianwei Zhang, Kwok-Yan Lam"
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - memory
  - security
  - tool-use
status: active
related:
  - "[[concepts/MemorySkillGovernanceDrift边界]]"
  - "[[concepts/ToolRiskPermissioning边界]]"
---

# MemMorph: Tool Hijacking in LLM Agents via Memory Poisoning

**来源**：arXiv:2605.26154
**URL**：https://arxiv.org/abs/2605.26154

## 摘要

MemMorph 研究通过长期记忆投毒来偏置 agent 的工具选择。攻击不是直接改 tool metadata，而是在 memory 中注入伪装成技术事实、事故报告或操作政策的记录，让 agent 在未来任务中自主推断并选择攻击者偏好的工具。

## 对本体系的贡献

- 说明 memory 不只是 personalization 资产，也是 tool selection 的长期控制面。
- 支撑 memory governance 必须检查 tool-selection hijack、memory provenance 和 retrieval/use 阶段影响。
- 将第 4 层 memory 与第 5 层 tool use、第 6 层安全 eval 连接起来。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：4. 上下文与知识层、5. Agent 系统层

## 关联

- [[concepts/MemorySkillGovernanceDrift边界]]
- [[Research: Memory skill governance drift 边界]]
