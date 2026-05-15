---
type: source
address: c-000094
title: "Software Fundamentals Matter More Than Ever — Matt Pocock（AI Engineer 会议）"
source_type: youtube-talk
url: https://www.youtube.com/watch?v=v4F1gFy-hqg
speaker: "[[people/MattPocock]]"
channel: AI Engineer
duration: 18:26
ingested_at: 2026-05-15
tags:
  - software-engineering
  - ai-coding
  - architecture
  - tdd
  - ddd
related:
  - "[[people/MattPocock]]"
  - "[[concepts/设计概念]]"
  - "[[concepts/深模块架构]]"
  - "[[concepts/共享领域语言]]"
  - "[[concepts/Grilling模式]]"
  - "[[skills/mattpocock-collection]]"
---

# Software Fundamentals Matter More Than Ever — Matt Pocock（AI Engineer 会议）

Matt Pocock，AI Engineer 会议，18 分 26 秒

18 个月教 AI 编码课程后的核心发现：成功的开发者不是那些把所有事情交给 AI 或什么都不交的人——而是那些在关键时刻回归软件工程基本功的人。

---

## 核心论点

> **"代码不便宜。实际上，坏代码是有史以来最贵的。"**

**Specs-to-code 运动的问题**（GSD / BMAD / Spec-Kit）：写 spec → AI 生成代码 → 有问题就改 spec 重新编译。Matt 的实验：每次迭代代码都更烂。本质是"另一个名字的 vibe coding"。

**核心洞察**：AI 在**好代码库**里表现非常好 → 好代码库比以前更重要 → 软件基本功比以前更重要。

---

## 五大主题

### 1. 对齐失败 → [[concepts/设计概念]]

根本原因：你和 AI 之间缺乏**设计概念**（Design Concept）。这是 Frederick P. Brooks（《设计的设计》）的概念：当多个人共同设计时，他们之间漂浮着一个无形的共同理念——对正在构建的事物的"不可见理论"。

你和 AI 没有这个共同理论 → 结果不是你想要的。

修复：[[concepts/Grilling模式]]（`/grill-me`）。Matt 认为这比 Claude Code 默认 Plan 模式更好：Plan 模式急于生成资产（计划文档），Grill Me 先建立共同的设计概念。

### 2. 啰嗦 / 术语鸿沟 → [[concepts/共享领域语言]]

根本原因：AI 不懂你的项目术语，用 20 个词描述本该 1 个词的东西。

修复：通用语言（Ubiquitous Language，DDD 概念）→ CONTEXT.md。"通过读取 AI 的思考链，我发现它不仅改善了规划，还让 AI 用更简洁的方式思考，并且实现与规划更加对齐。"

Skill 演化：`/ubiquitous-language`（已废弃）→ 集成进 `/grill-with-docs`。

### 3. 代码跑不起来 → 反馈闭环

根本原因：LLM "超出了它的车灯照射范围"（Pragmatic Programmer）——一次做太多，然后才去类型检查。**"反馈速率是你的速度上限。"**

修复：TDD（`/tdd`）——先写失败测试，再修，再重构。强迫 LLM 小步推进。

### 4. 代码库变泥球 → [[concepts/深模块架构]]

根本原因：AI 非常擅长创建**浅模块**代码库（大量小文件，复杂接口）。这类代码库 AI 自己都难以导航，更难以维护。

John Ousterhout（《软件设计哲学》）：
- **深模块**：简单接口后面隐藏大量功能。AI 在接口处测试，不需要穿透内部。
- **浅模块**：功能少，接口复杂。AI 迷失在大量小 blob 中。

修复：`/improve-codebase-architecture` — 找到可以把相关代码包进深模块的机会。

### 5. 大脑跟不上 → 灰盒策略

**设计接口，委托实现**：对非关键模块，不需要深入审查实现，只需设计好接口和在接口处测试。AI 负责内部实现，你负责外部设计。

Kent Beck：**"每天投资于系统的设计。"**

---

## 核心比喻

> **AI = 战术程序员**（排长，现场执行代码变更）
> **你 = 战略思考者**（指挥官，理解整体系统）

软件基本功（DDD、TDD、深模块、设计概念）是战略层的必要技能。

---

## 参考书目

| 书名 | 作者 | 贡献概念 |
|---|---|---|
| A Philosophy of Software Design | John Ousterhout | 深模块 vs 浅模块 |
| The Pragmatic Programmer | David Thomas & Andrew Hunt | 软件熵、超出车灯照射范围、反馈速率 |
| The Design of Design | Frederick P. Brooks | 设计概念 |
| Domain-Driven Design | Eric Evans | 通用语言（Ubiquitous Language） |
| Extreme Programming Explained | Kent Beck | 每天投资于系统设计 |

---

## 关联

- [[concepts/设计概念]]（Brooks：设计者之间的不可见共同理论）
- [[concepts/深模块架构]]（Ousterhout：深 vs 浅模块）
- [[concepts/共享领域语言]]（DDD 通用语言 → CONTEXT.md）
- [[concepts/Grilling模式]]（`/grill-me`，建立共同设计概念）
- [[concepts/瓶颈转移论]]（与 Fiona Fung 独立收敛：AI 加速代码后，理解/验证成为新瓶颈）
- [[concepts/AmdahlsLawInAI]]（Dario 的表述：AI 加速代码后，安全/验证成为约束）
- [[people/MattPocock]]
- [[skills/mattpocock-collection]]
