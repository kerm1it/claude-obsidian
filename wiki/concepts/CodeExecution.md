---
address: c-000062
type: concept
title: "Code Execution Tool（代码执行工具）"
created: 2026-05-12
updated: 2026-05-12
tags:
  - anthropic
  - claude
  - tool-use
  - sandbox
  - agent
status: active
related:
  - "[[concepts/ExpandingToolkit]]"
  - "[[domains/Claude-Code]]"
  - "[[people/Lucas]]"
---

# Code Execution Tool（代码执行工具）

**来源：** [[people/Lucas]]（Anthropic Research PM），Code with Claude 2026  
**参见：** [[sources/the-expanding-toolkit-2026-05-12]]

---

## 是什么

Anthropic 提供的 Claude API 工具，给 Claude 一个**服务端托管的沙箱计算机**，可以在其中执行代码。

---

## 解决了什么问题

**旧范式（Before）**：
1. 开发者找 VM 提供商，启动沙箱
2. 模型输出代码
3. 开发者把代码放到 VM 上跑
4. 解析 traceback，喂回模型
5. 重复循环

每次迭代都有一次 harness 往返，开发者需要维护整套 write-run-fix 脚手架。

**新范式（After）**：
- Claude 获得服务端托管沙箱
- 整个 write-run-fix 循环**在单个 API turn 内完成**
- 无需 harness 往返

---

## 心智模型：两类"计算机"

| | Code Execution Tool | 本地 Bash |
|---|---|---|
| **类比** | Claude 的"暂存计算器" | 你的真实环境 |
| **适合** | 无状态计算、数据分析、安装自定义库 | 访问你的 repo、本地 Python 环境、真实数据 |
| **隔离性** | 不污染本地文件系统 | 直接操作本地 |
| **选择方** | Claude 自动判断 | Claude 自动判断 |

Claude 能智能判断哪个任务应该用 Code Execution Tool（隔离暂存），哪个任务应该用本地 Bash（访问真实环境）。

---

## Claude Code 应用

- `/schedule` 命令：把 Code Execution 的自迭代循环设定为 cron 定时任务，完全自主运行

---

## 与 ExpandingToolkit 的关系

Code Execution Tool 是 [[concepts/ExpandingToolkit]] 在代码执行维度的具体体现：原本开发者需要自己搭的 VM 管理脚手架，现在由模型层统一提供。

---

## 来源

- [[sources/the-expanding-toolkit-2026-05-12]]
