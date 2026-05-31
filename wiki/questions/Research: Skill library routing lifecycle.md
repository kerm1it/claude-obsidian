---
address: c-000256
type: synthesis
title: "Research: Skill library routing lifecycle"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - agent-skills
  - routing
  - lifecycle
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/SkillLibraryRouting生命周期]]"
  - "[[concepts/Skill与ToolMemory边界]]"
sources:
  - "[[sources/skillsvote-2026]]"
  - "[[sources/under-the-hood-skill-md-2026]]"
  - "[[sources/secure-agent-skills-2026]]"
  - "[[sources/reusable-skill-md-files-2026]]"
  - "[[sources/skillsbench-2026]]"
  - "[[sources/skill-text-to-structure-2026]]"
  - "[[sources/agent-skills-wild-security-2026]]"
---

# Research: Skill library routing lifecycle

## Overview

单个 skill 的稳定归属是第 4 层；skill library routing / lifecycle 仍然不新增顶层。它是第 4 层程序性知识库的规模化治理问题：如何收集、结构化、检索、选择、执行、归因、更新和退役 skills。

稳定链路：`trace / human skill → metadata normalization → retrieval → selection → harness execution → outcome attribution → evidence-gated update or retirement`。

## Key Findings

- SkillsVote 把 skill governance 拆成 collection、recommendation、evolution，并强调只有 successful reusable discoveries 才能进入 evidence-gated updates。（Source: [[sources/skillsvote-2026]]）
- Under the Hood of SKILL.md 说明 SKILL.md metadata 本身会影响 discovery、selection 和 governance；攻击者不需要脚本 payload，也可通过文本操纵 registry-facing stages。（Source: [[sources/under-the-hood-skill-md-2026]]）
- Towards Secure Agent Skills 将生命周期分成 Creation、Distribution、Deployment、Execution，指出 single-approval persistent trust 和缺乏 mandatory marketplace review 是结构性风险。（Source: [[sources/secure-agent-skills-2026]]）
- 138K SKILL.md 实证研究显示大量公开 skill 存在 routing defect，说明可复用性不只是格式问题，也是 metadata、环境依赖和质量治理问题。（Source: [[sources/reusable-skill-md-files-2026]]）
- SkillsBench 显示 curated skills 能提升 pass rate，但 self-generated skills 不稳定，且部分 skill 带来负增益；library 必须有 eval 和退役机制。（Source: [[sources/skillsbench-2026]]）
- Skill Text to Structure 说明纯文本 skill 难以支撑大规模 discovery 和 risk assessment；结构化表示有助于检索和审查。（Source: [[sources/skill-text-to-structure-2026]]）

## Stable Boundary

| 概念 | 主职责 | 归属 |
|---|---|---|
| Skill | 单个可版本化程序性知识包 | 4. 上下文与知识层 |
| Skill library | 多个 skill 的索引、检索、版本和治理 | 4. 上下文与知识层 |
| Routing | 让正确 skill 在正确任务被候选召回和加载 | 4/5 交界 |
| Lifecycle governance | 创建、分发、部署、执行、更新、退役 | 6/8 交界 |
| Agent harness | 运行时加载 skill、执行脚本、记录 trace | 5. Agent 系统层 |

## Open Questions

- Skill routing 应主要依赖 metadata 检索、结构化 schema、agent 自判断，还是 hybrid ranker。
- Skill 更新应如何避免 eval overfitting 和 context poisoning。
- 社区 registry 的 trust model 是否会演化出 lockfile、签名、capability manifest 和强制安全审查。

## Filed Result

本轮归档为 [[concepts/SkillLibraryRouting生命周期]]，并回填 [[domains/AI知识体系]]。结论：skill library lifecycle 仍是第 4 层程序性知识库治理，不新增顶层；它通过第 5 层执行、第 6 层评估安全、第 8 层证据化演化。
