---
id: c-000097
type: source
title: "The Founder's Playbook — Anthropic（2026-05-16）"
source: "https://cdn.prod.website-files.com/6889473510b50328dbb70ae6/69fe2a55b93bb0732b1fe33c_The-Founders-Playbook-05062026_v3%20(1).pdf"
raw: ".raw/articles/founders-playbook-2026-05-16.md"
publisher: Anthropic
date: 2026-05-06
ingested: 2026-05-16
tags:
  - startup
  - ai-native
  - anthropic
  - claude-cowork
  - founder
status: active
---

# The Founder's Playbook — Anthropic（2026-05-16）

Anthropic 发布的 35 页创业者指南，系统描述 AI 原生创业公司从构想到规模化的完整路径。核心产品矩阵：**Claude**（研究与战略）、**Claude Code**（产品构建）、**Claude Cowork**（运营自动化）。

## 核心主张

> "The bottlenecks are no longer what you can build, but what you choose to build."
> "AI compresses quarters into weeks."

AI 时代创业者的工作未变——找真实问题、构建解决方案、规模化；变的是路径，AI 把过去以季度计的工作压缩成以周计。

## 四阶段创业生命周期

→ 详见：[[concepts/AI原生创业生命周期]]

| 阶段 | 核心任务 | Claude 角色 | 退出条件 |
|------|----------|-------------|----------|
| **Idea** | 验证 PMF 假设 | 研究、竞品分析、反驳 | 用户访谈+数据支撑的假设 |
| **MVP** | 构建可用原型 | 编码、架构决策、安全扫描 | 真实用户的可重复使用模式 |
| **Launch** | 建立可持续系统 | 运营自动化、流程设计 | 系统在创始人缺席时仍运行 |
| **Scale** | 从构建者到对外执行官 | GTM 执行、企业基础设施 | 可持续盈利/IPO就绪/被收购 |

## 关键概念

### 创始人角色演变 → [[concepts/创始人编排者角色]]
创始人从"构建者"转变为"编排者"——把领域专业知识转化为 AI 可执行的上下文，而不是亲手执行每项任务。

### 智能体技术债 → [[concepts/智能体技术债]]
AI 生成代码速度极快，但会产生脆弱、无文档、难以维护的系统。核心防线：
- **CLAUDE.md**：产品目标、技术决策、边界约束、测试要求
- 每个 PR 都需要测试、文档、代码审查

### Claude Cowork → [[entities/ClaudeCowork]]
Anthropic 新产品。一个 AI 智能体团队，管理创始人的日历、收件箱、项目和运营层。在 Launch 和 Scale 阶段承担运营自动化：Sprint 安排、Bug 路由、指标汇编、企业支持工单。

### 数据飞轮 → [[concepts/数据飞轮复利]]
用户行为信号（接受/拒绝哪些输出）→ 产品改进 → 更多使用 → 更多反馈。这种数据是**时间锁定、上下文专有**的，竞争对手无法复制。

### 工作流锁定 → [[concepts/工作流锁定]]
深度集成让用户切换成本从"产品决策"变为"全面运营项目"。通过 API、Webhook、SDK 让客户不只是使用产品，而是在产品上层构建。

## 关键练习（可执行）

- **MVP 阶段**：建立 CLAUDE.md 记录技术决策，每次 AI 写代码后立刻补测试
- **Launch 阶段**：用 Claude 运行代码级安全审查（SOC 2/GDPR/HIPAA），输出优先级修复清单
- **Scale 阶段**：让 Claude 生成"瓶颈地图"——所有必须经过你的工作流；找出一周不在时会停摆的节点
- **Scale 阶段**：建立工作流集成审计（前 10 名客户的自动化、集成、切换成本）
- **Scale 阶段**：用"测试套件即护城河地图"——每发现一个竞品会出错的 edge case 就加一个测试

## 案例公司

| 公司 | 模式 |
|------|------|
| Carta Healthcare | 用 Claude 处理 22,000 例外科手术，数据抽取时间减少 66% |
| Anything | 让 150 万用户无需写代码即可构建软件产品 |
| Cogent | 用 Claude 自动化企业安全漏洞全生命周期管理 |
| Airtree | 用 Claude Cowork 统一原本散落在 12 个工具中的运营数据 |
| Duvo | 完全基于 Claude + Agent SDK 的采购/供应链 AI 代理 |
| Zingage | 家护机构 24/7 自动化运营，结构化工具调用协调 EMR |
| Kindora | 非营利人创建的慈善机构-资助方智能匹配平台，MCP 连接器直接在 Claude 内访问 |
| Wordsmith | 律师转 CTO 创建的法律合同 AI，工程团队用 Claude Code 构建 |
| GC AI | 用领域专业知识构建法务 AI，内置公司专属剧本和风险容忍阈值 |

## 资源

- Claude Code 文档、最佳实践、高级用户技巧
- Claude Cowork 入门
- Anthropic Startups Program（免费 API credits、最高速率限制、创始人活动邀请）

## 关联

- [[entities/Anthropic]]
- [[entities/ClaudeCowork]]
- [[concepts/AI原生创业生命周期]]
- [[concepts/智能体技术债]]
- [[concepts/创始人编排者角色]]
- [[concepts/数据飞轮复利]]
- [[concepts/工作流锁定]]
- [[domains/Claude-Code]]
