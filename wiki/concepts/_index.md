---
type: index
title: "概念索引"
created: 2026-05-05
updated: 2026-05-11
tags:
  - wiki
  - concepts
status: active
---

# 概念

## AI 工作流

- [[concepts/HTML作为AI输出格式|HTML 作为 AI 输出格式]] — 用 HTML 替代 Markdown 作为 Claude 生成产出物的首选格式
- [[concepts/Claude-Code接入飞书]] — 用飞书替代 terminal，获得持久化、富文本和多 session 管理
- [[concepts/聊天记录复盘与AI成长]] — 用公司聊天记录做时间分析、决策复盘和 PRD 工作流

## Agent 记忆与系统设计

- [[concepts/CompiledTruth时间线模式|Compiled Truth + Timeline 模式]] — 知识页面双区结构：编译事实区（覆写）+ 时间线区（追加）
- [[concepts/DreamCycle|Dream Cycle（梦境循环）]] — 夜间自动维护：蒸馏、模式检测、反向链接修复
- [[concepts/Skillify]] — 将一次性 fix 固化为可路由、可测试的 fat-markdown skill
- [[concepts/混合检索RRF|混合检索 + RRF 融合]] — 向量 + 关键词 + RRF，P@5 提升 +31.4 pts
- [[concepts/Minions任务队列|Minions 任务队列]] — 确定性后台 job queue，不阻塞 Agent 主会话

## AI 原生工程组织

- [[concepts/AI原生工程组织|AI 原生工程组织]] — 当 AI 成为基础设施后，团队规范、组织形态和文化的系统性重写框架
- [[concepts/瓶颈转移论|瓶颈转移论]] — 编码不再是瓶颈；验证/安全/跨职能协作成为新稀缺资源
- [[concepts/JIT规划|JIT 规划（Just-In-Time Planning）]] — 高变化率 + 低原型成本环境下，只在需要时做足够的规划

## AI 研究与产品理论

- [[concepts/ScalingLaws|规模律（Scaling Laws）]] — 模型能力随算力/数据/参数的幂律增长，Dario 等 10 年前的预测全部兑现
- [[concepts/国家级天才数据中心|数据中心里的天才国家]] — Dario 对多 Agent 终极形态的比喻，从单人工具 → 组织级 AI
- [[concepts/HoldLightAndShade|Hold Light and Shade]] — Anthropic 核心文化价值观，同时持有技术的光明潜力与潜在阴影
- [[concepts/AmdahlsLawInAI|Amdahl 定律在 AI 中的应用]] — AI 加速代码后，安全/验证/架构成为新瓶颈
- [[concepts/单人十亿美金公司]] — Dario 预测 2026 年将出现单人十亿美金公司

## Claude Code 产品策略与未来

- [[concepts/ProductOverhang|Product Overhang（产品过剩）]] — 模型能力已存在但产品尚未捕捉；提前建造等待模型赶上；Claude Code 的诞生逻辑
- [[concepts/自主商业运营|自主商业运营]] — AI Agent 运营完整业务（support/marketing/dev/family office）；3-6 个月内基础 SaaS 可完全交给 AI
- [[concepts/软件护城河侵蚀|软件护城河侵蚀]] — 软件开发成本趋零，纯功能性 SaaS 护城河瓦解；殡仪馆类比
- [[concepts/Loop机制|Loop 机制]] — cron 调度重复 Agent 任务；Boris Cherny 每晚几千 Agent；/loop + Routines
- [[concepts/软件民主化|软件民主化（印刷机类比）]] — 编程将像读写一样成为大众技能；领域专家是最佳软件作者

## Claude 模型能力扩展（Expanding Toolkit）

- [[concepts/ExpandingToolkit|Expanding Toolkit（扩展工具箱）]] — 去年要自己搭的脚手架今天已随模型出货；补偿模型不可靠性的代码半衰期只有几个月
- [[concepts/CodeExecution|Code Execution Tool（代码执行）]] — Claude 服务端托管沙箱；write-run-fix 循环在单个 API turn 内完成
- [[concepts/NativeResolutionComputerUse|Native Resolution Computer Use]] — Opus 4.7 原生支持 1440p 截图，返回 1:1 像素坐标；OSWorld 78%

## 模型推理与效率

- [[concepts/TestTimeCompute|Test-time Compute]] — 推理时动态分配计算资源，不同任务用不同算力
- [[concepts/AdaptiveThinking|Adaptive Thinking]] — Claude 自主决定"思考多少"；Opus 4.6 起为默认
- [[concepts/EffortDial|Effort Dial（努力拨盘）]] — 显式控制推理深度；extra high 是 coding 最佳默认
- [[concepts/TaskBudgets|Task Budgets]] — 按任务分配 token 预算，细粒度控制推理成本
