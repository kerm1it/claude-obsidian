---
address: c-000006
type: source
title: "AI Agent 实践分享会全程回放（2026-05-05）"
created: 2026-05-10
updated: 2026-05-10
source_type: video
original_file: ".raw/notebooklm/quanchenghuifang1-2026-05-10.md"
raw_video: "/Users/kermit/Downloads/全程回放1DemoD_20260505185557.mp4"
recorded: 2026-05-05
language: zh-TW
extraction_method: NotebookLM fulltext (ASR)
tags:
  - ai-agent
  - claude-code
  - workflow
  - source
  - video
status: ingested
---

# AI Agent 实践分享会全程回放（2026-05-05）

**形式：** 线上分享会（全程录像，繁体中文 ASR 转录）  
**主持：** [[people/Zara]]  
**录制：** 2026-05-05  
**提取：** NotebookLM fulltext，33,762 字符

---

## 内容概览

由 [[people/Zara]] 组织的小型邀请制线上活动，邀请了十余位在自己领域深度使用 AI Agent 的创业者、开发者和团队管理者分享内部实践。

---

## 嘉宾分享摘要

### [[people/Zara]]（主持 + 分享）

**主题：Claude Code 接入飞书**

- 将 Claude Code 作为 bot 接入飞书，日常在飞书群聊中与 Claude 交互，替代 terminal
- 优势：消息持久化、聊天记录可搜索、支持卡片/富文本/表情/图文混排
- 用飞书 thread 管理多 session：一个群 = 一个 project，一个 thread = 一个 session
- Claude 生成的文档自动变成飞书文档，可直接评论
- 使用 Hyperframes skill（黑帧）生成 HTML 视频合辑
- 正在内测"早鸟群"，计划支持 Claude Code / Codex 等多种 agent 接入

→ 详见 [[concepts/Claude-Code接入飞书]]

---

### [[people/Sparks]]（[[entities/Midas]] 创始人）

**主题：多 Agent 系统用于 AI 量化交易**

- 信息密集型工作的两大挑战：信息碎片化 + 文字不适合表达复杂信息
- 解决方案：两层 Agent 架构
  - **Agent A**：监控市场新闻/事件（BG、DV6 等），整理、压缩、去噪
  - **Agent B**：连接"认知层"（带时间维度的结构化存储），梳理推演、建模
- 输出结合文字 + 图像（SVG / 生成模型），增强可读性
- 整个流程包成 skill，接入 agent 后可直接对话调用
- 架构适用于任何信息密集型工作：科研、调研、监控等

---

### [[people/Brandon]]（[[entities/Instant]] 创始人）

**主题：用公司聊天记录做个人复盘与成长**

- 让 agent 读取飞书聊天记录，分析过去两周时间分配（产品 35%、技术探索、团队管理等）
- 用 AI 模拟自己过去的决策：发现 70% 的决策与 AI 完全一致 → "CEO 是最容易被替代的岗位"
- 让 AI 给出个人成长建议，评估 AI 使用水平与提升方向
- 工作流：先 web coding 实现功能 → 让 AI 反推 PRD → 再让 AI 重建验证文档完整性
- 核心原则：**宁可浪费 Token，也不浪费时间**

→ 详见 [[concepts/聊天记录复盘与AI成长]]

---

### [[people/Siqi]]（[[entities/Pika]] VP of Product）

**主题：AI 作为数字分身与生活伴侣**

- 养了一个名为"47"的 AI 分身，拥有公司所有 GitHub 和数据权限
- 日常职责：PM 工作（bug → Linear ticket 自动分类分配）、替代本人回复同事
- 每个 agent 有独立手机号，可打电话；接入视频会议（beta）
- 自动加入所有会议，会后写纪要到 Notion workspace
- 设有 cron job，每天发状态更新；帮忙和妈妈聊天
- 愿景：**每个人都有自己的机器人，陪伴生活与工作**

---

### [[people/Haoran]]（[[entities/MX]] 联合创始人）

**主题：MX——以文档为中心的多人 + AI 协作空间**

- 定位：面向团队的 AI 原生工作空间，类似"多人可用的 Cursor/Claude Code + AI 原生 Notion"
- 核心功能：
  - TeamSpace + 个人空间，接入 GitHub 仓库
  - 贴身助理 Momo（每人一个，与文档处于同一视角）
  - 数据分析 AI 员工（接入 ClickHouse + 订单数据，回答关键数据问题）
  - 调研 AI（按团队自定义框架执行调研，可在文档中直接对话迭代）
- 全团队约 50 个 agent（含不可见的个人 agent）
- 文档默认由 AI 起草，手动编辑为辅
- 通过 CLI 支持外部 agent 写入/读取 MX 空间

---

## 关键洞察

> [!key-insight] 本场核心主题
> AI Agent 正在从"工具"演变为"数字同事"乃至"数字分身"——有手机号、加入会议、管理项目、陪伴生活。架构上，多 Agent + Skill 模块化是共识；数据持久化和上下文管理是核心难点。

---

## 关联页面

**人物：** [[people/Zara]]、[[people/Sparks]]、[[people/Brandon]]、[[people/Siqi]]、[[people/Haoran]]  
**实体：** [[entities/Midas]]、[[entities/Pika]]、[[entities/MX]]、[[entities/Instant]]  
**概念：** [[concepts/Claude-Code接入飞书]]、[[concepts/聊天记录复盘与AI成长]]、[[concepts/HTML作为AI输出格式]]  
**工具：** [[domains/Claude-Code]]
