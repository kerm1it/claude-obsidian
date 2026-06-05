---
source_url: https://x.com/i/status/2061877533885473181
source_kind: tweet-article
fetched: 2026-06-05
published: 2026-06-02
author: Matt Van Horn (@mvanhorn)
author_followers: 29109
title: "Every Agentic Engineering Hack I Know (June 2026)"
platform: x
metrics:
  likes: 2496
  retweets: 269
  replies: 103
  quotes: 64
  bookmarks: 7596
  views: 669291
---

# Every Agentic Engineering Hack I Know (June 2026)

Matt Van Horn (@mvanhorn)，June（智能烤箱，被 Weber 收购）和 Lyft 前身联合创始人。分享 22 条 Agentic Engineering 实践技巧，涵盖 Claude Code + Codex 双引擎工作流、计划驱动执行、语音输入、远程控制、开源贡献和个人知识库整合。

## 22 Hacks 完整列表

### 1. 有想法立刻做 plan.md
`/ce-plan` 并行启动研究 Agent（代码库模式、历史方案、外部文档），生成结构化计划（问题/方案/文件/验收标准）。`/ce-work` 按计划执行。Compound Engineering 插件（@kieranklaassen, @trevin）驱动。

### 2. 不用读 plan.md
计划是给 Agent 的，不是给你的。直接 `/ce-work`，有问题就问 "TLDR?"、"eli5 this plan"。

### 3. /ce-plan 也用于非工程工作
策略文档、竞品分析、董事会更新都可用。关键技巧：先让 Agent 做"plan for the plan"再产出——"让 LLM 不偷懒的最强技巧"。

### 4. 语音驱动（Voice-Pilled）
LLM 理解上下文能力强→不需要完美转录。Mac: Monologue 或 Wispr Flow + 鹅颈麦。手机: Apple 内置听写。

### 5. cmux 大量 tab
4-6 个 cmux tab 并行：一个写计划、一个构建、一个修 bug。来回切换，完成率最大化。Orca 用于手机终端。

### 6. 终端默认打开 Claude Code
每新 tab 直接进 Claude，不先进 shell。配置 Ghostty config + launcher 脚本。不用 cd 到文件夹——"Agent 能找到你的项目。"

### 7. 远程控制 + 给 Claude 邮箱
`remoteControlAtStartup: true` → 手机继续任务。AgentMail 给 Claude 独立邮箱，白名单地址触发新 session 执行任务。开源: agentmail-to-claude-code。

### 8. dangerously skip permissions
跑 6 个 session 不可能逐个确认权限。`skipDangerousModePermissionPrompt: true`。Shift+Tab 切换。Codex: `codex --yolo`。声音 hook 通知完成。

### 9. 从不在 Codex CLI 里跑 Codex
三种方式：Codex IDE 扩展 / `/ce-work --codex` / Printing Press codex 模式。两个 $200 计划并行=第二引擎。

### 10. 研究先行: last30days
`/last30days <topic>` 在 `/ce-plan` 前运行。并行搜索 Reddit/X/YouTube/TikTok/HN/GitHub。开源 26K+ ⭐。

### 11. Granola 录一切，原始转录丢进 LLM
不摘要，直接丢原始转录给 `/ce-plan`。例：90 分钟午餐录音→一晚生成产品提案→候选人现在全职加入。

### 12. 人=信号（Human Signal）
跑 6 个 Agent 时你的角色："不是做工作，是提供信号。" Agent 提供量，你提供品味、方向和重定向。"Be the taste. Let them be the hands."

### 13. HyperFrames 做视频
视频=代码循环。每个视频是 `script.md`→Agent 渲染 MP4。GIF 上传 catbox.moe 用于 GitHub。

### 14. 笔记=Agent 知识库
Bear（十年笔记，CLI 接入）+ Obsidian + gbrain + supermemory。模式：选带 CLI/API 的笔记工具→指向 Agent→知识跨 session 复利。

### 15. 随处工作: Mac mini
Mosh（SSH 不卡）+ Tmux（飞机上工作）+ Hermes + OpenClaw + Agent Cookie（同步 cookies/.env）。

### 16. Proof: 把 plan.md 发给同事
plan.md 扔到 Proof→渲染为可读文档+内联评论→评论流回 Agent loop。

### 17. 写自己的 Skills
做超过两次就写成 skill。技巧：复制 Compound Engineering skill 的结构来搭新 skill。last30days 始于个人 skill（现 26K+ ⭐），Printing Press 320+ PR。

### 18. 开源贡献
同样 `/ce-plan`+`/ce-work` 循环。数百 PR 合并进 Python/Go/OpenCV/Vercel Agent Browser。加入 Discord 认识维护者→真朋友。X 上 $1-3/月订阅尊重的人。

### 19. 笔记本配置
M5 Max 64GB。6 个 Claude + Codex 全天→电池仅 1 小时。Anker 电池砖+车载充电器。`sudo pmset -a disablesleep 1`。

### 20. Printing Press: 运行真实生活的 CLI
Tesla 预热、Instacart 下单、ESPN 比赛监控、Alaska Airlines 比价——全部通过 Agent CLI。开源 3.7K+ ⭐。Agent Cookie 提供无密码认证。

### 21. AI 精神病（AI Psychosis）
Agent 本应做所有工作，但每个朋友都更努力了。"史上最好玩的电子游戏"——会上瘾。建议：问有没有人真的需要你做的东西；为自己做的项目也很好。

### 22. 本文就是这样写的
本文在 cmux 中用 Monologue 语音输入+Claude Code 写成，Proof 审查，last30days 提供素材。全栈：语音 app+计划插件+配置+tab+Mac Mini+远程+CLI 舰队。
