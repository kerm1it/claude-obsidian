---
type: source
title: "A harness for every task: Dynamic Workflows in Claude Code"
source_url: https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code
source_kind: blog
fetched: 2026-06-05
published: 2026-06-02
authors:
  - "[[Thariq|Thariq Shihipar]]"
  - "[[Sid Bidasaria]]"
address: c-000588
created: 2026-06-05
updated: 2026-06-12
tags:
  - claude-code
  - workflows
  - multi-agent
  - anthropic
  - orchestration
status: ingested
related:
  - "[[concepts/DynamicWorkflows]]"
  - "[[concepts/Loop机制]]"
  - "[[concepts/智能体GC]]"
  - "[[concepts/Agent评估体系]]"
  - "[[domains/Claude-Code]]"
---

# A harness for every task: Dynamic Workflows in Claude Code

Anthropic 官方博客（2026-06-02），由 Claude Code 团队成员 Thariq Shihipar 和 Sid Bidasaria 联合撰写。宣布 Claude Code 现在可以**动态编写并编排自己的多 Agent harness**——为每个任务即时定制工作流。

## 核心主张

> "Claude can now write its own harness on the fly, custom-built for the task at hand."

默认 Claude Code harness 为编码设计，大多数任务因结构性相似也能工作。但研究、安全分析、Agent 团队、Code Review 等任务类别此前需要自定义 harness 才能达到峰值性能。Dynamic Workflows 让 Claude 原生解决这些问题。

## Dynamic Workflows 机制

- 执行 JavaScript 文件，提供 `agent()`/`parallel()`/`pipeline()`/`phase()` 等特殊函数来生成和协调子 Agent
- 标准 JS 函数（JSON, Math, Array）可用
- 可决定每个 Agent 使用的**模型**和是否在 **worktree** 中运行
- 中断后可**续传**（resume）

## 三种单上下文失败模式 → [[concepts/DynamicWorkflows]]

| 失败模式 | 描述 |
|---------|------|
| Agentic Laziness | 完成部分工作就声称完成（如安全审查只处理了 35/50 项） |
| Self-Preferential Bias | 偏好自己的结果或发现，尤其在自我验证/评判时 |
| Goal Drift | 多轮+compaction 后目标保真度逐渐损失，边界条件消失 |

Workflows 通过"**独立子 Agent + 隔离上下文窗口 + 聚焦目标**"对抗三者。

## 六种 Workflow 模式 → [[concepts/DynamicWorkflows#六种模式]]

1. **Classify-and-act**：分类器先判定任务类型，再路由到不同 Agent
2. **Fan-out-and-synthesize**：拆分步骤 → 并行 Agent → barrier 合并
3. **Adversarial verification**：每个 Agent 输出由独立 Agent 对抗验证
4. **Generate-and-filter**：生成大量想法 → 按 rubric 过滤 → 去重 → 输出
5. **Tournament**：N 个 Agent 竞赛同一任务，两两评判决出胜者
6. **Loop until done**：未知工作量时循环生成 Agent 直到停止条件满足

## 适用场景

- **迁移/重构**：Bun 从 Zig 到 Rust 使用 workflows；拆步骤 → worktree 子 Agent → 对抗审查 → 合并
- **深度研究**：`/deep-research` skill 内部使用 dynamic workflows
- **深度验证**：识别所有事实主张 → 子 Agent 逐一核查 → 验证 Agent 检查来源质量
- **排序**：1000+ 项目时，tournament / 两两比较 pipeline（"比较判断比绝对评分更可靠"）
- **记忆与规则遵守**：每规则一个验证 Agent；逆向：挖掘 session 中的重复纠正 → 聚类 → 对抗验证 → 蒸馏回 CLAUDE.md
- **根因调查**：从**不相交证据**生成假设（日志/文件/数据各一个 Agent），每个假设面对验证+反驳 Agent 小组
- **大规模分类**：分类→去重→修复或升级。隔离模式（quarantine）：读取不受信内容的 Agent 禁止高权限操作
- **探索与品味**：探索→rubric 审查→满足则完成
- **Evals**：worktree 独立 Agent → 比较 Agent 按 rubric 评分
- **模型路由**：分类器先研究任务复杂度，再路由到 Sonnet 或 Opus

## 何时不用

Token 消耗显著更大。引导问题："**does it really need more compute?**" 大多数传统编码任务不需要 5 人审查小组。

## 技巧

- 详细 prompt + 特定模式 = 最佳结果
- 配合 `/loop` + `/goal` 做可重复 workflow
- 设置 token 预算："use 10k tokens"
- 按 "s" 保存 workflow 到 `~/.claude/workflows` 或通过 skill 分发
- 通过 skill 分发时："think of the workflows in the skill as a template"

## 关联

- [[concepts/DynamicWorkflows]] — 完整概念页，含六种模式、三种失败模式、与 Loop 的关系
- [[concepts/Loop机制]] — Loop 是 Workflow 的持续运行机制
- [[concepts/智能体GC]] — Agentic Laziness 和 Goal Drift 是 GC 要解决的问题的另一面
- [[concepts/Agent评估体系]] — Adversarial verification 与 Eval 驱动开发收敛
- [[domains/Claude-Code]] — Claude Code 能力扩展
- [[Thariq]] — 作者（更新：Claude Code TLM，此博文 + HTML 输出格式主张）
