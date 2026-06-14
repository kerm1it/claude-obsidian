---
type: skills-collection
address: c-000092
title: "claude-obsidian — 知识管理技能集"
source: https://github.com/AgriciDaniel/claude-obsidian
created: 2026-05-15
updated: 2026-06-12
status: active
tags:
  - skills
  - knowledge-management
  - obsidian
  - wiki
related:
  - "[[skills/_index]]"
  - "[[concepts/渐进式上下文注入]]"
---

# claude-obsidian — 知识管理技能集

本 vault 自带的 Agent Skills 合集，基于 Karpathy LLM Wiki pattern。
路径：`skills/<name>/SKILL.md`

---

## 知识库核心

### `/wiki`
**触发**：set up wiki、scaffold vault、/wiki

建立/管理持久 wiki vault。Scaffold 结构、从一句话描述生成 vault、管理热缓存（hot.md）。路由到其他子 skills。

### `/wiki-ingest`
**触发**：ingest、add this to the wiki、process this source、batch ingest

素材摄入：读取源文件 → 提取实体/概念 → 创建/更新 wiki 页面 → 更新索引 → 记录日志。支持文件、URL、批量模式。

### `/wiki-query`
**触发**：what do you know about、query:、what is、explain、find in wiki

从 wiki 回答问题。先读 hot.md → 再读 index.md → 再读相关页面。附引用。好的答案会归档回 wiki。支持 quick/standard/deep 三个模式。

### `/wiki-lint`
**触发**：lint、health check、clean up wiki、wiki audit、find orphans

健康检查：孤儿页（无入链）、死 wikilink、过时信息、缺失交叉引用、frontmatter 缺失、空章节。生成 Dataview 仪表板和 canvas 地图。

### `/wiki-fold`
**触发**：fold the log、run a fold、log rollup

DragonScale Mechanism 1：把 `wiki/log.md` 最近 2^k 条条目滚动归档到 `wiki/folds/`。提取性摘要（不发明）。dry-run 默认（stdout only），commit 模式写入文件。

### `/save`
**触发**：save this、/save、file this、file this conversation、keep this

当前对话/洞察 → 结构化 wiki 页面。自动判断笔记类型，创建 frontmatter，归档到正确文件夹，更新 index/log/hot。

### `/autoresearch`
**触发**：autoresearch、research [topic]、deep dive into、investigate、find everything about

自主迭代研究循环：`program.md` 配置目标和约束，循环运行搜索→抓取→综合，直到达到深度。输出直接写入 wiki。

---

## 内容处理

### `/defuddle`
**触发**：clean this url、defuddle、strip this url、fetch and clean

网页去噪：移除广告/导航/页眉页脚/样板文字，留下干净可读的 markdown。摄入前用，节省 40-60% tokens。

### `obsidian-markdown`
**触发**：obsidian syntax、wikilink、callout、obsidian formatting

Obsidian Flavored Markdown 参考：wikilink（`[[Page]]`）、embed（`![[Page]]`）、callout（`> [!tip]`）、properties（frontmatter）、标签、高亮、数学公式、canvas 语法。

### `obsidian-bases`
**触发**：create a base、obsidian bases、dynamic table、task tracker base

Obsidian Bases（`.base` 文件）：动态表格/卡片/列表视图，过滤器、公式、汇总。Obsidian 原生数据库层。

---

## 可视化

### `/canvas`
**触发**：/canvas、add to canvas、create canvas、put this on the canvas

可视化层：图片/文字卡片/PDF/wiki 页面添加到 Obsidian canvas 文件，自动定位到区域（zone）。

---

## 与 mattpocock/skills 的互补关系

| 需求 | 用 mattpocock | 用 claude-obsidian |
|---|---|---|
| 任务前对齐 | `/grill-me` / `/grill-with-docs` | — |
| 代码质量 | `/tdd` / `/diagnose` | — |
| 素材消化归档 | — | `/wiki-ingest` |
| 知识检索 | — | `/wiki-query` |
| 网页内容清理 | — | `/defuddle` |
| 会话交接 | `/handoff` | `/save` |
| 自主研究 | — | `/autoresearch` |
| Token 压缩 | `/caveman` | — |
