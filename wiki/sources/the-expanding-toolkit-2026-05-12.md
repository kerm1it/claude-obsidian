---
address: c-000059
type: source
title: "The Expanding Toolkit — Lucas（Anthropic，Code with Claude 2026-05-12）"
created: 2026-05-12
updated: 2026-05-12
tags:
  - anthropic
  - claude
  - tool-use
  - computer-use
  - code-execution
  - code-with-claude
  - developer-conference
status: active
source_url: "https://www.youtube.com/watch?v=KLCuxMDZSDg"
source_kind: youtube
people:
  - "[[people/Lucas]]"
entities:
  - "[[entities/Anthropic]]"
  - "[[entities/CodeWithClaude]]"
concepts:
  - "[[concepts/ExpandingToolkit]]"
  - "[[concepts/CodeExecution]]"
  - "[[concepts/NativeResolutionComputerUse]]"
related:
  - "[[sources/the-thinking-lever-2026-05-11]]"
  - "[[sources/fiona-fung-ai-native-engineering-2026-05-11]]"
---

# The Expanding Toolkit — Lucas（Anthropic，Code with Claude 2026-05-12）

**演讲人：** [[people/Lucas]]（Research PM，[[entities/Anthropic]]）  
**活动：** [[entities/CodeWithClaude]]（2026-05-06，旧金山）  
**来源：** [YouTube](https://www.youtube.com/watch?v=KLCuxMDZSDg)  
**时长：** 约 25 分钟

---

## 核心论点

> "去年你必须自己搭的脚手架，今天已经随模型一起出货了。"

[[concepts/ExpandingToolkit]] 的核心主张：不要再把 Claude 当作一个纯粹的输入输出 LLM 黑盒，而要把它看作一套**围绕模型不断扩展的工具体系**。以前需要开发者自己写的路由器、重试装饰器、上下文压缩器、坐标缩放代码——这些脚手架并没有消失，但它们已经**移入了模型本身**。

核心原则：
- **补偿模型不可靠性的代码，半衰期只有几个月**——交给 Anthropic
- **连接模型与你的世界的代码，会持续增值**——专注于此

---

## 一、Tool Use：路由与重试

### Before（旧范式）
- 无法信任模型面对全工具集 → 自己写路由器（字符串匹配、启发式规则）
- 工具经常出错 → 手写重试 decorator + 退避逻辑

### After（新范式）
- 模型可以**自主搜索工具集并选择正确工具**
- 工具选择精度已足够高：路由器和预过滤通常让事情**更差**
- Claude 看到工具报错后，自动恢复并重试

### 实践技巧
**在工具描述中声明输出 schema**：
```
"search_docs: 搜索文档。返回字段：id, title, snippet, score"
```
Claude 提前知道返回结构 → 可以直接对 `score` 排序，节省一次 harness 往返。

**Claude Code Tip**：在 `settings.json` 中定义 pre/post tool use hooks → 可以在特定情况下拦截工具调用，或在调用后程序化记录输出。

---

## 二、Context Management：上下文管理

### Before（旧范式）
- 自建记忆系统（chunking、RAG）
- 每 N 轮调另一个模型做摘要
- 手动移动 cache breakpoint

### After（新范式）
- **1M context + flat pricing** → 消除大多数窗口压力
- **Server-side compaction**（API 层自动压缩）
- **Context editing**（外科手术式编辑上下文）
- 结果：从几百行配置变成几行 API 调用

### 实践技巧
**每 N 轮清除工具结果（stale tool outputs）**：
- 大文件读取、截图、搜索结果 → 决策完成后清除
- 保留：核心任务描述 + Claude 的决策与分析
- 效果：显著节省 token，不丢失推理链

**Claude Code Tip**：`/context` 命令 → 实时彩色可视化上下文窗口占用（messages、tool results、system、MCP 定义各占多少），并附优化建议。

---

## 三、Code Execution：代码执行

### Before（旧范式）
- 开发者自找 VM 提供商 → 启动沙箱
- 模型输出代码 → 放到 VM 跑 → 解析 traceback → 喂回模型 → 循环
- 每次迭代都有 harness 往返

### After（新范式）
- **Code Execution Tool**：Claude 获得服务端托管沙箱
- 整个 write-run-fix 循环**在单个 API turn 内完成**
- Claude 有"自己的计算机"：无状态计算、数据分析、安装自定义库
- 需要访问本地资源时（repo、本地 Python 环境），自动切回本地 Bash

### 实践技巧
**mental model**：Code Execution ≠ 本地 Bash  
- Code Execution Tool = Claude 的计算器/暂存器（不污染你的文件系统）  
- 本地 Bash = 访问真实环境（你的 repo、已装的依赖、真实数据）  
- Claude 能智能判断应该用哪个

**Claude Code Tip**：`/schedule` → 定时触发 cron 式自主运行，可以把上面的自迭代循环设定为定时任务。

---

## 四、Computer Use：电脑操控

### Before（旧范式）
- 1080p 截图 → 缩小到 Claude 的像素限制
- 记录缩放因子 → 模型输出点击坐标 → 放大回原分辨率
- 包一层重试 + 验证逻辑

### After（新范式）
- **Opus 4.7 原生支持 1440p 截图，返回 1:1 像素坐标**
- 缩放数学**完全消失**：直接发图，Claude 精确点击
- 评测：**OSWorld** 分 12 个月内从 <50% → **78%**（Opus 4.7，目标 80%）

### 实践技巧
- 4K 及以上：仍建议自行降采样
- 1440p 及以下：建议实验不同分辨率和图像格式（JPEG/PNG/WEBP），因压缩方式不同，对特定 UI 效果不同

**Claude Code Tip**：**Claude in Chrome 扩展**（`claude.ai/chrome`） → Claude Code 可以直接操控你的真实 Chrome 浏览器会话，含本地开发页面。

---

## Demo：Browser Use 自主 Debug 循环

演示场景：Project management dashboard（看板）有两个 Bug：
1. "New" 按钮不能添加 Card
2. 拖拽（Drag & Drop）列间移动不正常

Claude Code + Claude in Chrome 的工作流：
1. Claude 自行打开 Chrome，在浏览器中复现 Bug
2. 实时测试 → 发现问题 → 修改代码 → 重测（不需要开发者介入）
3. 修复 Card 创建 → 验证 → 继续检查其他功能 → 修复 Drag & Drop → 再次验证

**意义**：大多数软件是面向人类的，必须以人类方式测试。Computer use 让 Claude 能**在 dev cycle 中闭环测试**，而不需要开发者手把手带到 Bug 现场。

---

## 总结与指导原则

| 代码类型 | 走向 | 建议 |
|---|---|---|
| 补偿模型不可靠性（路由器、重试、验证循环） | 半衰期几个月，被模型吸收 | 交给 Anthropic，不要自己维护 |
| 连接模型与你的世界（自定义工具、数据、上下文） | 持续增值，无法被模型吸收 | 专注投入，这是护城河 |

**"Agent Front Door"愿景**：未来每个 Agent、每个软件都会为 Agent 开辟入口。有趣的工作不再是让模型更可靠，而是**你在 Agent 入口另一边放了什么别人没有的东西**。

---

## 关联

- [[concepts/ExpandingToolkit]] — 本次演讲的核心框架
- [[concepts/CodeExecution]] — Claude 服务端托管沙箱
- [[concepts/NativeResolutionComputerUse]] — Opus 4.7 1440p 原生坐标
- [[people/Lucas]] — 演讲人
- [[entities/CodeWithClaude]] — 活动
- [[sources/the-thinking-lever-2026-05-11]] — 同场活动，Matt Bleifer 讲 Test-time Compute
- [[sources/fiona-fung-ai-native-engineering-2026-05-11]] — 同场活动，Fiona Fung 讲 AI 原生工程组织
