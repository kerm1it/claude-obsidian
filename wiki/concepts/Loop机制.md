---
address: c-000069
type: concept
title: "Loop 机制（cron 式重复 Agent 任务）"
created: 2026-05-12
updated: 2026-05-12
tags:
  - anthropic
  - claude-code
  - agent
  - automation
status: active
related:
  - "[[concepts/智能体GC]]"
  - "[[concepts/AnthropicDreaming]]"
  - "[[concepts/DreamCycle]]"
  - "[[domains/Claude-Code]]"
  - "[[people/BorisCherny]]"
---

# Loop 机制（cron 式重复 Agent 任务）

**来源：** [[people/BorisCherny]]（Claude Code 创始人，Anthropic）  
**参见：** [[sources/boris-cherny-coding-solved-2026-05-12]]

---

## 是什么

> "Loop 是我目前认为最重要的功能。最简单但最有效的东西。"

Claude Code 的 `/loop` 功能：让 Claude 用 **cron 调度一个重复任务**，可以按任意频率（每分钟、每五分钟、每天等）自动触发。**Routines** 是其服务端版本，关闭笔记本电脑后仍继续运行。

---

## Boris 实际运行的 Loop 示例

| Loop | 频率 | 功能 |
|---|---|---|
| PR 保姆 | 持续 | 自动修复 CI、自动 rebase |
| CI 健康维护 | 持续 | 检测并修复 flaky test |
| Twitter 反馈聚类 | 每 30 分钟 | 抓取反馈并聚类 |

Boris 目前有**几十个 Loop 在并行运行**，每晚有**几千个 Agent 做深度工作**。

---

## 模型自动发起 Loop（Opus 4.7）

4.7 会主动提议启动 Loop：
> "我注意到这个数据在随时间变化，我来每 30 分钟给你发一份报告，要发到 Slack 吗？"

→ 未来不需要用户手动决定何时用 Loop，**模型会自己判断**。

---

## 与同类概念的区别

| 概念 | 触发方 | 用途 |
|---|---|---|
| **Loop 机制**（本页） | 用户 / 模型 | 用户级重复任务（PR、CI、监控） |
| [[concepts/智能体GC]] | 自动后台 | 代码库/知识库熵的异步清理 |
| [[concepts/AnthropicDreaming]] | 离线批处理 | 跨 Agent transcript 提取策略，更新 memory |
| [[concepts/DreamCycle]]（GBrain） | 夜间 | 知识库蒸馏、反向链接修复 |

这四者都是"异步、周期性的 Agent 维护"模式，在不同层次独立收敛到同一原语。

---

## Claude Code 快速上手

```
# 在 Claude Code 中
/loop every 30 minutes: check CI and fix any failures
/schedule check PRs and auto-rebase
```

**Routines**（服务端版本）：即使关闭本地 Claude Code，循环仍在服务端继续。

---

## 来源

- [[sources/boris-cherny-coding-solved-2026-05-12]]
