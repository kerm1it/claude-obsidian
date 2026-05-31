---
address: c-000218
type: synthesis
title: "Research: Skill 与 tool memory workflow 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - agent-skills
  - context-engineering
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/Skill与ToolMemory边界]]"
  - "[[concepts/AgentSkillsStandard]]"
  - "[[concepts/Skillify]]"
  - "[[concepts/RAG与Memory边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
sources:
  - "[[sources/anthropic-skills-overview-2026]]"
  - "[[sources/agent-skills-specification-2026]]"
  - "[[sources/openai-agents-sdk-tools-2026]]"
  - "[[sources/agent-skills-architecture-survey-2026]]"
  - "[[sources/skillsbench-2026]]"
  - "[[sources/skill-text-to-structure-2026]]"
  - "[[sources/agent-skills-wild-security-2026]]"
  - "[[sources/malicious-agent-skills-wild-2026]]"
  - "[[sources/mattpocock-skills-2026-05-15]]"
  - "[[sources/scientific-agent-skills-2026-05-17]]"
---

# Research: Skill 与 tool memory workflow 边界

## Overview

本轮把 skill 稳定归入 [[domains/AI知识体系]] 第 4 层：它是模型权重外的程序性知识包，按需加载进上下文，服务第 5 层 agent harness。Skill 不是 tool 本身，也不是 memory 本身；它是把反复任务、专家流程、工具用法和组织规范编译成可路由能力的封装。

稳定链路：`trace / repeated workflow → reflection or curation → candidate skill → eval / scan → install → harness route and execute`。

## Key Findings

- Anthropic 文档把 skills 定义为包含 instructions、scripts、resources 的目录，并用 progressive disclosure 控制上下文成本。（Source: [[sources/anthropic-skills-overview-2026]]）
- Agent Skills 规范把 `SKILL.md`、`scripts/`、`references/`、`assets/` 固化为跨 agent 的包结构，最小 frontmatter 是 `name` 和 `description`。（Source: [[sources/agent-skills-specification-2026]]）
- OpenAI Agents SDK 的 tools 是可执行动作，包括托管工具、运行时工具、函数工具和 agents-as-tools；这给出边界：tool 执行动作，skill 组织程序性知识。（Source: [[sources/openai-agents-sdk-tools-2026]]）
- Agent Skills survey 把 skill 视为从单体模型走向模块化 agent 的抽象层，强调 progressive disclosure、MCP 互补、skill acquisition、deployment 和 security。（Source: [[sources/agent-skills-architecture-survey-2026]]）
- SkillsBench 显示人工策划 skill 平均提升 agent 任务 pass rate，但自生成 skill 平均无收益，且部分任务出现负增益；skill 必须评估而不是盲目安装。（Source: [[sources/skillsbench-2026]]）
- Skill Text to Structure 指出纯文本 skill 把触发条件、执行结构和副作用混在一起；结构化表示可提升 skill discovery 和风险评估。（Source: [[sources/skill-text-to-structure-2026]]）
- 大规模安全研究显示社区 skill 存在 prompt injection、数据外传、权限扩大和供应链风险；包含可执行脚本的 skill 风险更高。（Source: [[sources/agent-skills-wild-security-2026]]）
- 恶意 skill 研究进一步说明第三方 skill 可以用看似正常的 instructions 和隐藏脚本攻击用户机器或 agent 决策。（Source: [[sources/malicious-agent-skills-wild-2026]]）

## Stable Boundary

| 概念 | 主职责 | 归属 |
|---|---|---|
| Skill | 可版本化程序性知识包，告诉 agent 怎么做一类任务 | 4. 上下文与知识层 |
| Tool | 可执行动作、API、函数、电脑操作或子 agent | 5. Agent 系统层 |
| Memory | 跨任务保存事实、偏好、经验和历史 | 4. 上下文与知识层 |
| Workflow | 固定或半固定的步骤编排 | 5. Agent 系统层 |
| Eval | 判断 skill / tool / workflow 是否改善系统 | 6. 评估与可靠性层 |

## 什么时候把经验升级为 Skill

| 现象 | 处理方式 |
|---|---|
| 一次性事实或材料 | 放入 RAG / source / note |
| 用户偏好、历史选择、长期状态 | 放入 memory |
| 当前任务临时 checklist | 留在 short-term context |
| 反复出现的流程、错误修复、工具使用套路 | 升级为 skill |
| 严格固定、可完全自动化的流程 | 变成 workflow 或 script，被 skill 调用 |

## 工程实践

- skill 创建之前先看失败 trace 和成功 trace，避免把愿望写成 skill。
- skill 创建之后至少做三类测试：触发测试、任务成功测试、安全/权限测试。
- skill 不应长期替代坏工具文档；稳定工具说明应回填 tool schema 或 official docs。
- 团队内部 skill 应进入版本控制、code review、CI、变更日志和回滚策略。
- 社区 skill 只按最低权限安装，优先挑选有来源、许可证、测试和安全扫描记录的包。

## Open Questions

- 大型 skill library 的 routing 层应由检索模型、规则、agent 自判断，还是混合架构完成。
- Skill 自生成何时能稳定超过人工策划；目前 SkillsBench 给出的信号偏谨慎。
- Skill 的权限模型是否会发展成类似浏览器扩展或包管理器的 capability manifest。

## Filed Result

本轮归档为 [[concepts/Skill与ToolMemory边界]]，并回填 [[domains/AI知识体系]] 第 4 层。Skill 的归属不新增顶层：它是上下文与知识层的程序性知识包，连接 Agent 系统层、评估可靠性层和自我改进反馈环。
