---
address: c-000070
type: source
title: "AI Agents Run My Business and Life — Andrew Wilkinson（Greg Isenberg，2026-05-12）"
created: 2026-05-12
updated: 2026-05-12
tags:
  - agent
  - automation
  - business
  - family-office
  - vibe-coding
  - openclaw
status: active
source_url: "https://www.youtube.com/watch?v=65IAqRUxg3c"
source_kind: youtube
people:
  - "[[people/AndrewWilkinson]]"
  - "[[people/GarryTan]]"
entities:
  - "[[entities/Tiny]]"
  - "[[entities/OpenClaw]]"
  - "[[entities/GBrain]]"
concepts:
  - "[[concepts/自主商业运营]]"
  - "[[concepts/软件护城河侵蚀]]"
related:
  - "[[sources/gbrain-2026-05-11]]"
  - "[[sources/boris-cherny-coding-solved-2026-05-12]]"
---

# AI Agents Run My Business and Life — Andrew Wilkinson（Greg Isenberg，2026-05-12）

**嘉宾：** [[people/AndrewWilkinson]]（[[entities/Tiny]] 创始人）  
**主持：** Greg Isenberg（Startup Ideas 播客）  
**录制：** 2026-04-29（视频发布约 2026-05-12）  
**来源：** [YouTube](https://www.youtube.com/watch?v=65IAqRUxg3c)

---

## 嘉宾背景

Andrew Wilkinson 是加拿大连锁企业家，旗下 [[entities/Tiny]] 持有约 24 家业务，并有个人 family office **Folly Partners**（个人控股公司的别称）。2025 年 12 月某一时刻突然"觉醒"，此后每天 3-4 点醒来开始疯狂用 Claude Code。

---

## 一、自主运营的 SaaS 业务：Deep Personality

Andrew 用 Claude Code 从零构建了一个个性化测试产品 **Deep Personality**，并几乎全部交给 AI Agent 运营。

### 产品起源
与女友做了 15 项心理测试（Claude Code 40 分钟构建多选题+评分+JSON），放进 ChatGPT，输出了一份精准分析两人关系的报告 → 看到商业机会 → 产品化。

产出物：~100 页报告，Robert Green 文风，涵盖性格原型、超能力/弱点、附着风格、家庭系统、ADHD/ASD 倾向等。

### Agent 运营架构（使用 Harbor）
使用朋友 Gavin 开发的 **Harbor**（`github/geekforbrains/harbor`）——一个 Agent 编排 GUI：

| Agent | 职责 |
|---|---|
| Dev Agent | P0 Bug → 直接修复并合并 PR |
| Support Agent | 邮件工单分类 → 自动处理或转 Dev |
| Marketing Agent | 连接 PostHog + Meta/Reddit 广告账户；多变量测试；创意素材；预算管理 |

> "Support 很快就不再是一份工作了。"

目前营收约 $20K；下一步目标：给 Marketing Agent 配 $10万/月广告预算。

---

## 二、Family Office AI：替换 Addepar

Addepar 是面向富人的投资组合管理软件，收费 $5-10 万/年。Andrew 的 CFO（从未写过代码）两周内用 Claude Code 构建了完整替代品。

功能：
- 全局资产负债表（实时）
- 132 笔直接投资跟踪（投入 1600 万 → 现值 3600 万）
- 投资组合压力测试、风险分析
- 自然语言查询 API（"回顾上季度，找出任何冰山或问题"）
- Tiny 旗下 24 家公司的综合数据

> "作为眼里的眼睛，能盯着整个公司——我觉得这太强大了。"

---

## 三、个人 AI 助理栈

### 数据管道
- Fireflies 录制所有会议 → 每晚 cron → Markdown → [[entities/GBrain]]
- Hearsay（Gavin 开发）：手机全天录音 → 转录 → iCloud → GBrain
- Apple Health 数据（Apple Watch）→ Google Drive JSON

### OpenClaw Agent（Ava — 个人助理）
- 读取全部邮件，自动分类和判断优先级
- 识别正在进行的项目，生成每日任务报告
- 把高优先级邮件/iMessage 发到 Telegram，提供 A/B/C 多选回复
- 例："全程把我的商务日历变成一道多选题"

### 个性化播客（Gemini Voice）
每天从 Readwise Reader + 邮件订阅中挑选 Andrew 感兴趣的内容（AI、健康、当地城市、商业），用 **Gemini Voice** 生成 7 分钟自定义音频播客，在淋浴时收听。包含：倒计时（"你还有 X 个夏天陪孩子"）+ Seneca 每日引言。

### 健康 Agent（Mara — 医生 Agent）
- 分析 HRV、静息心率、睡眠、呼吸频率
- 发现：神经痛每次发作前 3 天腕温会异常 → 提前预警
- 医疗咨询时：调用 8 个专家子 Agent（风湿科、内科等），用 extra high thinking 综合全部医疗数据给出建议

---

## 四、投资观与软件未来

### 软件护城河侵蚀（[[concepts/软件护城河侵蚀]]）
> "软件现在比五年前是个更差的生意。"  
> "以前软件像报纸业——你需要贵重的印刷机。现在软件是免费的，任何人都能做，任何人都能抄。"

类比：400 家殡仪馆，以前只有一个"网络侄子"给你做软件，所以你垄断了。现在 20 个殡仪馆主都会 AI，全都自己做，定价暴跌。

**Andrew 的实际做法**：
- 不买 SaaS → 自建（CFO 两周替换 Addepar）
- 不扩招人 → 扩 Claude API 调用 → **家族办公室月均 Claude 账单 $4 万**，替代了部分薪资

**给创业者的建议**（悲观但诚实）：
- 用 AI vibe code 目标赚 $1-200 万
- 剩余资金投数据中心股票（TSMC、Iron Mountain 等）
- 寻找有护城河的传统业务（家庭服务、现金流稳定的老行业）

---

## 五、提示技巧

**技巧 1 — 问题工具（Question Interview Prompting）**：
> "我会说：这是我的目标。我想让你采访我，问我一堆问题来确定你的 prompt，使用问题工具。"

Claude 会用多选题形式采访用户 5-10 分钟，自动构建最优 prompt。Andrew 认为"没有人需要手写 prompt，AI 应该直接采访你"。

**技巧 2 — Agent 团队**：
> "我总是说：请用一个由 8 个子 Agent 组成的团队。答案质量会大幅提升。"

---

## 关联

- [[people/AndrewWilkinson]] — 嘉宾
- [[entities/Tiny]] — Andrew 的企业集团
- [[entities/OpenClaw]] — 核心 Agent 框架（已有 wiki 页面）
- [[entities/GBrain]] — 记忆系统（已有 wiki 页面，Garry Tan 开发，Andrew 是朋友）
- [[concepts/自主商业运营]] — AI Agent 运营完整业务
- [[concepts/软件护城河侵蚀]] — 软件商业模式的结构性变化
- [[sources/gbrain-2026-05-11]] — GBrain 详细介绍
- [[sources/boris-cherny-coding-solved-2026-05-12]] — 同期 Boris Cherny 的观点互相印证
