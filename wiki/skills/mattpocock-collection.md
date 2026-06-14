---
type: skills-collection
address: c-000091
title: "mattpocock/skills — 工程师技能集"
source: https://github.com/mattpocock/skills
author: "[[people/MattPocock]]"
stars: 82759
created: 2026-05-15
updated: 2026-06-12
status: active
tags:
  - skills
  - engineering
  - claude-code
related:
  - "[[skills/_index]]"
  - "[[people/MattPocock]]"
  - "[[concepts/共享领域语言]]"
  - "[[concepts/Grilling模式]]"
  - "[[sources/mattpocock-skills-2026-05-15]]"
---

# mattpocock/skills — 工程师技能集

Matt Pocock（Total TypeScript）的 Claude Code skills 合集，⭐ 82,759。
安装：`npx skills@latest add mattpocock/skills`

---

## Engineering Skills

### `/grill-with-docs` ⭐ 最核心
**触发**：每次想做代码变更时。

任务前"审讯"会话，同时维护项目文档：
- 逐一提问（等回答再继续），每个问题附上推荐答案
- 发现 CONTEXT.md 已有定义时，挑战用词冲突："你的术语表定义 'cancellation' 是 X，但你好像在说 Y——哪个对？"
- 在对话中实时更新 CONTEXT.md 和 ADR（只有真正有内容时才创建文件）
- 支持 `CONTEXT-MAP.md`（多上下文 monorepo）

文件结构约定：
```
/CONTEXT.md           ← 单 context repo
/docs/adr/0001-*.md   ← 架构决策记录
```

---

### `/tdd`
**触发**：写新功能 / 修 bug。

红绿重构循环，按垂直切片推进：
1. 写一个**失败**测试（Red）
2. 让 agent 修到绿（Green）
3. 重构
4. 循环

---

### `/diagnose`
**触发**：遇到硬 bug / 性能回归。

纪律性 debug 循环：
> 复现 → 最小化 → 提出假设 → 插桩验证 → 修复 → 写回归测试

---

### `/to-prd`
**触发**：把对话综合成需求文档。

无需额外采访——直接把已有对话上下文综合成 PRD，提交为 GitHub issue。

---

### `/to-issues`
**触发**：把计划/spec/PRD 拆成任务。

使用**垂直切片**（vertical slice）方式拆分——每个 issue 可独立执行，包含完整的前端+后端+测试。

---

### `/triage`
**触发**：整理 issue 队列。

状态机式 triage，通过一系列 triage 角色流转来分类和优先级排序。

---

### `/zoom-out`
**触发**：进入陌生代码段 / 需要系统视角。

让 agent 在整个系统视角下解释当前代码的位置和作用，而不只是局部。

---

### `/prototype`
**触发**：需要快速验证设计方向。

两种形式：
- **终端 app**：验证状态机/业务逻辑
- **多 UI 变体**：几个截然不同的设计，挂在同一路由下可切换对比

---

### `/improve-codebase-architecture`
**触发**：代码库越来越复杂（建议每几天运行一次）。

基于 `CONTEXT.md` 和 `docs/adr/` 的决策，发现可以"深化"的地方——把浅层接口变深，减少调用复杂度（John Ousterhout："最好的模块是深模块"）。

---

### `/setup-matt-pocock-skills`
**触发**：新 repo 第一次使用这套技能时（运行一次）。

配置：issue tracker（GitHub / Linear / 本地文件）、triage 标签词汇表、文档存放位置。其他 engineering skills 依赖这里的配置。

---

## Productivity Skills

### `/grill-me`
**触发**：想在开始任何任务前把计划想清楚。

通用版 grilling，不涉及代码文档。逐一提问直到决策树所有分支解决。

---

### `/caveman`
**触发**：长会话需要省 token / 明确说 "caveman mode"。

超压缩通信模式，token 用量 ~75%↓。规则：
- 去掉：冠词、废话（just/really/basically）、礼貌用语（sure/certainly）、对冲词
- 保留：所有技术内容、代码块（原样）、精确错误信息
- 模式：`[thing] [action] [reason]. [next step].`

只有用户说"stop caveman"才退出。安全警告/破坏性操作时临时退出，说完继续。

---

### `/handoff`
**触发**：需要换一个 agent / 新会话继续当前工作。

压缩当前对话为 handoff doc，保存到 `mktemp -t handoff-XXXXXX.md`。
- 不重复已在 PRD/ADR/issue/commit 里的内容（用路径/URL 引用）
- 如果指定了下一个会话的目标，按此裁剪文档
- 推荐下一个会话应该用哪些 skills

---

### `/write-a-skill`
**触发**：想创建新的 skill。

SKILL.md 模板要求：
- `description` ≤ 1024 字符，第三人称，包含"Use when [具体触发词]"
- SKILL.md ≤ 100 行；超过则拆到 REFERENCE.md / EXAMPLES.md
- 只有在操作确定性强、会重复执行时才加 scripts/

---

## Misc Skills

### `/git-guardrails-claude-code`
配置 Claude Code hooks，拦截危险 git 命令（`push --force`、`reset --hard`、`clean -f` 等）。

### `/setup-pre-commit`
Husky + lint-staged + Prettier + TypeScript 类型检查 + 测试。一次配置，每次 commit 自动运行。

### `/scaffold-exercises`
创建练习目录结构（sections/problems/solutions/explainers）。Matt 的课程制作工具。

### `/migrate-to-shoehorn`
把 `as` 类型断言迁移到 `@total-typescript/shoehorn`。TypeScript 项目专用。

---

## Personal Skills（个人用）

### `obsidian-vault`
Matt 自己的 Obsidian vault 管理 skill，vault 路径：`/mnt/d/Obsidian Vault/AI Research/`

约定：
- 扁平结构（无文件夹），靠链接和 Index notes 组织
- Index notes 命名：`Ralph Wiggum Index.md`、`Skills Index.md`、`RAG Index.md`
- 标题大写（Title Case）

**注**：Matt 也在用 Obsidian 管理 AI 研究笔记，结构与本 vault 不同（扁平 vs 目录化），是有趣的对比案例。

---

## Deprecated（参考价值）

### `ubiquitous-language`（→ 被 `grill-with-docs` 取代）

早期 DDD 术语表工具，输出到 `UBIQUITOUS_LANGUAGE.md`。相比现在的 CONTEXT.md 更形式化：
- 按子域分组的术语表（带"避免使用的别名"列）
- 关系说明（基数）
- **示例对话**：3-5 轮开发者与领域专家的对话，展示术语如何在真实对话中被精确使用

示例对话格式（精髓所在）：
```
> Dev: "When a Customer places an Order, do we create the Invoice immediately?"
> Domain expert: "No — an Invoice is only generated once a Fulfillment is confirmed."
> Dev: "So if a Shipment is cancelled before dispatch, no Invoice exists for it?"
> Domain expert: "Exactly. The Invoice lifecycle is tied to the Fulfillment, not the Order."
```

规则要点：
- **有主见**：多个词对应同一概念时，选最好的，其余列为"避免"
- **明确标记冲突**："account 同时指代 Customer 和 User——这是两个不同概念"
- **只包含领域术语**，跳过通用编程概念（array、function、endpoint）

---

## In Progress（关注）

| Skill | 方向 |
|---|---|
| `review` | 代码 review（结构化） |
| `writing-shape` | 写作：整体形状/轮廓 |
| `writing-beats` | 写作：节拍/节奏 |
| `writing-fragments` | 写作：碎片整合 |
