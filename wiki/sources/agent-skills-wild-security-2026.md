---
address: c-000225
type: source
title: "Agent Skills in the Wild"
source_url: https://arxiv.org/abs/2601.10338
source_type: paper
author: "Yi Liu et al."
published: 2026-01-15
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - agent-skills
  - security
  - supply-chain
status: active
related:
  - "[[concepts/Skill与ToolMemory边界]]"
---

# Agent Skills in the Wild

**来源**：arXiv:2601.10338
**URL**：https://arxiv.org/abs/2601.10338

## 摘要

这篇研究分析大规模社区 agent skill 生态中的安全风险。作者收集数万 skills，并用 SkillScan 结合静态分析和 LLM 语义分类识别 prompt injection、数据外传、权限扩大和供应链风险。

## 关键贡献

- Skill 是新的攻击面，因为它同时包含自然语言 instructions 和可执行代码。
- 风险类别包括 prompt injection、data exfiltration、privilege escalation、software supply chain。
- 带 executable scripts 的 skill 风险显著高于 instruction-only skill。
- 论文提出 vulnerability taxonomy、检测方法和开放数据集，支持后续 skill 安全研究。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：4. 上下文与知识层、5. Agent 系统层
- 作用：说明 skill 必须经过权限、依赖、代码和语义安全扫描。

## 关联

- [[concepts/Skill与ToolMemory边界]]
- [[Research: Skill 与 tool memory workflow 边界]]
