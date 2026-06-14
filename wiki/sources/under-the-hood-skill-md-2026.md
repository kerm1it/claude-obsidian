---
address: c-000258
type: source
title: "Under the Hood of SKILL.md"
source_url: https://arxiv.org/abs/2605.11418
source_type: paper
author: "Shoumik Saha, Kazem Faghih, Soheil Feizi"
published: 2026-05-12
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - agent-skills
  - security
  - supply-chain
status: active
related:
  - "[[concepts/SkillLibraryRouting生命周期]]"
  - "[[concepts/MemorySkillGovernanceDrift边界]]"
---

# Under the Hood of SKILL.md

**来源**：arXiv:2605.11418
**URL**：https://arxiv.org/abs/2605.11418

## 摘要

论文研究 SKILL.md-only semantic supply-chain attacks，覆盖 Agent Skill lifecycle 中 registry-facing 的 discovery、selection、governance 三个阶段。结论是 metadata 和 instructions 不是被动文档，而是影响检索、选择和审查的 operational text。

## 关键贡献

- Discovery 阶段，文本 trigger 可以操纵 embedding-based retrieval。
- Selection 阶段，description framing 会影响 agent 在功能相近 skill 中选择哪一个。
- Governance 阶段，语义规避可以绕过部分阻断判断。
- 仅靠扫描脚本不足以治理 skill registry；自然语言 metadata 也需要安全评估。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：4. 上下文与知识层、5. Agent 系统层
- 作用：说明 skill routing surface 本身是供应链安全面。

## 关联

- [[concepts/SkillLibraryRouting生命周期]]
- [[concepts/MemorySkillGovernanceDrift边界]]
- [[Research: Skill library routing lifecycle]]
