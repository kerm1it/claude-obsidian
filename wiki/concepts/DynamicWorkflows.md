---
type: concept
name: Dynamic Workflows
domain: claude-code
address: c-000590
created: 2026-06-05
tags:
  - claude-code
  - workflows
  - multi-agent
  - orchestration
  - anthropic
status: active
related:
  - "[[concepts/Loop机制]]"
  - "[[concepts/智能体GC]]"
  - "[[concepts/Agent评估体系]]"
  - "[[concepts/瓶颈转移论]]"
  - "[[domains/Claude-Code]]"
---

# Dynamic Workflows

Claude Code（Opus 4.8+）即时编写并编排多 Agent harness 的能力。Claude 为每个任务**动态定制**工作流，用 JavaScript 文件中的 `agent()`/`parallel()`/`pipeline()` 等函数生成和协调子 Agent。

## 核心突破

默认 Claude Code harness 在单一上下文窗口中做规划+执行——对大多数编码任务有效，但在**长时间运行、大规模并行、高度结构化或对抗性任务**上会崩溃。Dynamic Workflows 通过**独立子 Agent + 隔离上下文窗口 + 聚焦目标**解决此问题。

## 三种单上下文失败模式

Dynamic Workflows 旨在对抗：

1. **Agentic Laziness**：完成部分工作后声称完成（如安全审查 35/50 项就说"done"）
2. **Self-Preferential Bias**：偏好自己的结果，尤其在自我验证/评判时
3. **Goal Drift**：多轮 compaction 后目标保真度逐渐损失；边界条件、"不要做 X"约束消失

> 与 [[concepts/上下文腐化]] 互补：上下文腐化是注意力机制层面的退化，Goal Drift 是目标保真度层面的退化。

## 六种模式

### 1. Classify-and-act

分类器 Agent 判定任务类型 → 路由到不同 Agent/行为。分类器也可在末尾判定输出类型。

**适用**：多类型输入的管道（分类+路由）、模型智能路由（先研究任务复杂度再选 Sonnet/Opus）

### 2. Fan-out-and-synthesize

拆分任务 → 每个步骤一个 Agent 并行 → barrier 合并结构化输出。

**适用**：大量小步骤、需要隔离上下文避免交叉污染的场景。核心约束：synthesize 是 barrier——等待所有 fan-out Agent 后再合并。

### 3. Adversarial verification

每个 Agent 输出由另一个独立 Agent 按 rubric/标准对抗验证。

**适用**：深度验证（事实核查+来源质量）、规则遵守（每规则一个验证 Agent + skeptic 角色审查）、安全审查。→ 与 [[concepts/Agent评估体系]] 收敛

### 4. Generate-and-filter

生成大量想法 → 按 rubric 过滤/验证 → 去重 → 只返回最高质量、经过测试的想法。

**适用**：头脑风暴、探索性任务

### 5. Tournament

N 个 Agent 用不同方法竞赛同一任务 → 评判 Agent 两两比较 → 决出胜者。关键洞察："比较判断比绝对评分更可靠。"

**适用**：排序（1000+ 项目）、代码生成（不同方案竞争）、命名（CLI 工具名 tournament）

### 6. Loop until done

未知工作量时循环生成 Agent，直到停止条件满足（无新发现、日志无错误）——而非固定次数。

**适用**：根因调查（从不相交证据生成假设→验证/反驳→直到收敛）、bug 发现

## 关键技术特性

- **JS 执行**：标准 JavaScript（JSON, Math, Array），无 Node API、无 `Date.now()`/`Math.random()`
- **模型选择**：workflow 可决定每个子 Agent 使用的模型
- **Worktree 隔离**：子 Agent 可在独立 worktree 中运行，避免文件冲突
- **续传**：中断后 resume session 时 workflow 从断点继续
- **保存与分享**：按 "s" 保存到 `~/.claude/workflows`；通过 skill 分发

## 何时不用

引导问题："**does it really need more compute?**" Workflows token 消耗显著更大，不适合简单任务。

## 与 /loop 和 /goal 的组合

```text
/loop 每N分钟 → workflow（分类→修复/升级）
/goal 设定硬性完成要求
```

Workflow 提供**结构**，Loop 提供**持续性**，Goal 提供**终止条件**。

## 关联

- [[concepts/Loop机制]] — Loop 是 Boris Cherny 称为"最重要功能"的调度机制，Workflow 是其编排层
- [[concepts/智能体GC]] — GC 对抗代码熵积累，Workflow 对抗单上下文失败——同一问题的两个维度
- [[concepts/上下文腐化]] — 长上下文退化是 Goal Drift 的技术根因
- [[concepts/Agent评估体系]] — Adversarial Verification 是 eval 驱动的 workflow 实例化
- [[concepts/瓶颈转移论]] — 编码不再瓶颈，验证/协调成为瓶颈；Workflow 是协调瓶颈的解决方案
- [[concepts/自我改进AI循环]] — Workflow loop-until-done 模式可直接实现第五层"学习机制"

## 来源

- [[sources/claude-code-dynamic-workflows-2026-06-05|A harness for every task: Dynamic Workflows in Claude Code]]（2026-06-02）
