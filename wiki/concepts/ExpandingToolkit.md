---
address: c-000061
type: concept
title: "Expanding Toolkit（扩展工具箱）"
created: 2026-05-12
updated: 2026-05-12
tags:
  - anthropic
  - agent
  - tool-use
  - architecture
  - scaffolding
status: active
related:
  - "[[concepts/CodeExecution]]"
  - "[[concepts/NativeResolutionComputerUse]]"
  - "[[concepts/AI原生工程组织]]"
  - "[[concepts/瓶颈转移论]]"
  - "[[concepts/智能体优先工程]]"
  - "[[people/Lucas]]"
---

# Expanding Toolkit（扩展工具箱）

**来源：** [[people/Lucas]]（Anthropic Research PM），Code with Claude 2026  
**参见：** [[sources/the-expanding-toolkit-2026-05-12]]

---

## 核心命题

> "去年你必须自己搭的脚手架，今天已经随模型一起出货了。"

把 Claude 不再视为单纯的输入输出 LLM 黑盒，而是一套**围绕模型持续扩展的工具体系（expanding toolkit）**。以前开发者需要自己维护的所有脚手架——路由器、重试装饰器、上下文压缩器、坐标缩放代码——正在被模型本身吸收。

---

## 四大维度的范式迁移

| 维度 | Before | After |
|---|---|---|
| **Tool Use** | 手写路由器 + 重试 decorator | 模型自主选工具 + 自动重试 |
| **Context Management** | RAG / 摘要调用 / 手移 cache | 1M context + server compaction + context editing |
| **Code Execution** | 自管 VM → harness 往返循环 | 服务端沙箱，单 API turn 闭环 |
| **Computer Use** | 手写缩放数学 + 重试验证 | 原生 1440p 坐标，无需缩放 |

---

## 核心指导原则

**补偿模型不可靠性的代码 → 交给 Anthropic**  
半衰期只有几个月。retry logic、routers、planners、verification loops 都会被模型吸收。

**连接模型与你的世界的代码 → 专注投入**  
自定义工具、你的数据、你的特定上下文。模型无法吸收它看不到的东西，这是你的护城河。

---

## Agent Front Door 愿景

未来每个 Agent、每个软件都会开辟 "Agent 入口"。有趣的工作不再是让模型更可靠，而是**你在 Agent 入口另一边放了什么别人没有的东西**。

---

## 与相关概念的关系

- [[concepts/瓶颈转移论]]（Fiona Fung）：编码不再是瓶颈 → Expanding Toolkit 的直接推论
- [[concepts/智能体优先工程]]（Ryan Lopopolo）：仓库即记录系统，不维护脚手架
- [[concepts/AI原生工程组织]]（Fiona Fung）：组织层面承接 Expanding Toolkit 逻辑
- [[concepts/CodeExecution]]：具体体现之一
- [[concepts/NativeResolutionComputerUse]]：具体体现之一

---

## 来源

- [[sources/the-expanding-toolkit-2026-05-12]]
