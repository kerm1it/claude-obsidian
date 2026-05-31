---
address: c-000255
type: concept
title: "Skill Library Routing 生命周期"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - agent-skills
  - routing
  - lifecycle
  - security
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/Skill与ToolMemory边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[concepts/MemorySkillGovernanceDrift边界]]"
sources:
  - "[[Research: Skill library routing lifecycle]]"
  - "[[sources/skillsvote-2026]]"
  - "[[sources/under-the-hood-skill-md-2026]]"
  - "[[sources/secure-agent-skills-2026]]"
  - "[[sources/reusable-skill-md-files-2026]]"
  - "[[sources/skillsbench-2026]]"
  - "[[sources/skill-text-to-structure-2026]]"
  - "[[sources/agent-skills-wild-security-2026]]"
---

# Skill Library Routing 生命周期

单个 skill 的问题是“这个任务怎么做”；skill library 的问题是“成百上千个 skill 中，哪些应该被发现、安装、加载、执行、更新和退役”。

主归属：**4. 上下文与知识层**。Skill library 是程序性知识库，核心是把可复用 procedures 管理成可发现、可路由、可审查、可演化的外部知识。

交叉链接：
- **5. Agent 系统层**：harness/runner 在任务中检索、选择、加载、执行 skill。
- **6. 评估与可靠性层**：routing eval、risk assessment、安全扫描、回归测试决定 skill 是否能进入或留在库中。
- **8. 自我改进与前沿层**：agent trace 可以生成、修订或退役 skill，但必须 evidence-gated。

## 生命周期

```mermaid
flowchart LR
    A["Collect / create"] --> B["Normalize metadata / structure"]
    B --> C["Index / retrieve"]
    C --> D["Select / load"]
    D --> E["Execute in harness"]
    E --> F["Attribute outcome"]
    F --> G["Update / deprecate / retire"]
    G --> C
```

## 稳定边界

| 阶段 | 核心问题 | 评估方式 |
|---|---|---|
| Collection | 这个 skill 从哪里来，是否可信 | provenance、license、author、hash、review |
| Normalization | metadata 是否足够路由 | name/description、tags、capability、requirements |
| Retrieval | 应不应该被候选召回 | MRR、recall@k、误召回率 |
| Selection | 是否应该加载执行 | precision、task success、token overhead |
| Execution | 是否安全且有效 | tool-call 正确性、side effect、sandbox |
| Attribution | 成功/失败归因给 skill 还是 agent exploration | trace linkage、ablation |
| Evolution | 是否更新、合并、退役 | regression eval、security gate、usage evidence |

## 工程规则

- Library 越大，越不能把所有 skill metadata 无脑塞进上下文。
- `description` 不是说明书，而是 routing surface；它会影响 discovery、selection 和安全审查。
- 先检索候选 skill，再让 agent 决定是否加载完整 `SKILL.md`，最后按需读取 references/scripts/assets。
- Skill 更新必须有证据：成功 trace、失败修复、回归测试或人工审查。
- 退役和合并与新增同等重要；重复、陈旧、环境依赖强的 skill 会污染未来上下文。

## 安全边界

- SKILL.md 文本本身会影响 registry discovery 和 agent selection，因此属于供应链攻击面。
- Third-party skill 需要 provenance、签名/锁定版本、最低权限、dependency review 和 sandbox。
- 仅扫描脚本不够；metadata、description 和 instructions 也要做语义风险评估。
- 一次安装不应形成永久信任，更新和执行时都需要重新检查。
- 大型 skill library 需要 [[concepts/MemorySkillGovernanceDrift边界|governance drift]] 检查：metadata-only attack、routing drift、dependency/API drift、permission drift、overbroad skill、duplicate skill 和 orphaned skill 都要能 quarantine、deprecate 或 retire。

## 一句话归类

Skill library routing / lifecycle 是第 4 层程序性知识库治理问题，通过第 5 层 agent harness 暴露给运行时，由第 6 层 eval/security gate 控制，并可由第 8 层从 trace 中证据化演化。
