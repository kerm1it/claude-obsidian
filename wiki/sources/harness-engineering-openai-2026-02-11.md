---
type: source
address: c-000048
title: "工程技术：在智能体优先的世界中利用 Codex"
created: 2026-05-11
updated: 2026-05-11
source_url: "https://openai.com/zh-Hans-CN/index/harness-engineering/"
source_type: article
author: "[[people/RyanLopopolo]]"
published: 2026-02-11
tags:
  - agent-engineering
  - codex
  - openai
  - software-engineering
  - agent-first
status: active
related:
  - "[[concepts/智能体优先工程]]"
  - "[[concepts/代码仓库即记录系统]]"
  - "[[concepts/智能体GC]]"
  - "[[concepts/AI原生工程组织]]"
  - "[[concepts/瓶颈转移论]]"
  - "[[entities/OpenAI]]"
---

# 工程技术：在智能体优先的世界中利用 Codex

**来源**：OpenAI 官方博客（中文版）  
**作者**：[[people/RyanLopopolo]]  
**发布日期**：2026-02-11  
**链接**：https://openai.com/zh-Hans-CN/index/harness-engineering/

---

## 核心主张

OpenAI 内部团队用五个月完成了一个实验：构建并交付一款软件产品的内部 beta 版，其中**没有一行代码是人工编写的**。约一百万行代码全部由 Codex 生成，3 名工程师，每人每天平均 3.5 个 PR，效率约为传统方式的 10 倍。

> "人类掌舵。智能体执行。"

---

## 关键数据

| 指标 | 数值 |
|------|------|
| 实验周期 | 5 个月（2025-08 ～ 2026-01） |
| 代码规模 | ~100 万行 |
| Pull Requests | ~1,500 个 |
| 初始团队规模 | 3 名工程师 |
| 人均日 PR | 3.5 个 |
| 效率提升 | ~10× |
| 单次 Codex 运行时长 | 常超 6 小时（夜间） |

---

## 核心经验

### 1. AGENTS.md 是目录，不是百科全书

大型 AGENTS.md 的四大失败模式：
- 情境稀缺 → 指令文件挤掉任务和代码
- 过度指导无效 → 一切都"重要"时，一切都不重要
- 立即腐烂 → 成为陈旧规则的坟场
- 无法核实 → 不适合机械检查

**解决方案**：AGENTS.md 约 100 行，仅作地图；知识存储在 `docs/` 结构化目录中，由 CI 机械验证、`doc-gardening` 智能体定期清理。

→ [[concepts/代码仓库即记录系统]]

### 2. 工程师角色转移

不再写代码，转向**系统、架构和杠杆**：
- 将大目标拆解为构建模块
- 识别智能体卡住时缺失的东西（工具/约束/文档）
- 将人类品味编码成规则和工具
- 将用户反馈转化为验收标准

与 [[concepts/瓶颈转移论]] 和 [[concepts/AI原生工程组织]] 高度印证：编码不再是瓶颈，QA/验证/架构才是。

### 3. 为智能体可读性设计

智能体在运行时无法访问的信息等于不存在：
- Slack 讨论、Google Docs、脑中的知识 → 对智能体不可见
- 需将情境推入仓库：架构决策、团队规范、品味偏好
- 偏好"枯燥"技术：可组合性强、API 稳定、训练集覆盖好
- 有时自己实现功能子集优于引入不透明第三方库

### 4. 机械强制架构约束

每个业务域固定分层（Types → Config → Repo → Service → Runtime → UI），依赖方向通过自定义 linter + 结构测试机械强制执行。Lint 错误信息直接注入智能体情境中（含修复指令）。

这种架构通常等到数百名工程师时才推行。**对智能体，这是早期先决条件**：约束才能保证速度不下降、架构不漂移。

### 5. 智能体 GC：对抗熵

问题：Codex 复现仓库已有模式，包括不良模式，导致漂移。

初始解法（人工每周五清理20%时间）→ 不可扩展。

解法：**黄金原则 + 后台循环清理**：
- 将最佳实践编码为可机械检查的规则
- 定期运行后台 Codex 任务扫描偏差、发起重构 PR
- 大多数可在一分钟内完成审查并自动合并

类比垃圾回收——持续小额偿还技术债务优于积累后一次解决。

→ [[concepts/智能体GC]]

### 6. 不断提高的自主水平

当前智能体已能端到端驱动新功能：重现 bug → 录制视频 → 实施修复 → 验证 → 录制演示 → 开 PR → 回应反馈 → 合并。仅在需要人类判断时才交由人工。

### 7. 高吞吐量下合并理念变化

- 减少阻塞合并门
- 测试偶发失败通过重跑解决，不无限期阻塞
- **纠错成本低，等待成本高**

---

## 与已有知识的关联

| 主题 | 关联页面 | 关系 |
|------|----------|------|
| 瓶颈转移 | [[concepts/瓶颈转移论]] | 本文是又一独立佐证：编码→QA/架构是瓶颈 |
| AI 原生工程组织 | [[concepts/AI原生工程组织]] | Fiona Fung 的框架与本文高度同构 |
| 记忆/知识库设计 | [[concepts/AgentMemoryAPI]] | 仓库即记忆，与 Anthropic Memory API 哲学一致 |
| GBrain Dream Cycle | [[concepts/DreamCycle]] | `doc-gardening` 智能体 ≈ Dream Cycle 的文档维护任务 |

---

## 关联页面

- [[concepts/智能体优先工程]] — 核心框架
- [[concepts/代码仓库即记录系统]] — AGENTS.md 设计模式
- [[concepts/智能体GC]] — 黄金原则+循环清理
- [[people/RyanLopopolo]] — 作者
- [[entities/OpenAI]] — 发布机构
