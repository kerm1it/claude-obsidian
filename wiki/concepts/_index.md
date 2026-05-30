---
type: index
title: "概念索引"
created: 2026-05-05
updated: 2026-05-30
tags:
  - wiki
  - concepts
status: active
---

# 概念

## AI 辅助工程实践（Matt Pocock）

- [[concepts/共享领域语言|共享领域语言（CONTEXT.md）]] — 为 AI agent 建立项目统一术语文档；解决啰嗦/命名不一致问题；Token 效率提升
- [[concepts/Grilling模式|Grilling 模式（任务前对齐审讯）]] — 任务开始前让 agent 用详细问题"审讯"你；穷举决策分支；解决最常见的对齐失败
- [[concepts/设计概念|设计概念（Design Concept）]] — Brooks：多人设计时的不可见共同理论；你与 AI 缺乏设计概念是对齐失败的根本原因
- [[concepts/深模块架构|深模块架构（Deep Module Architecture）]] — Ousterhout：深模块（简单接口+隐藏复杂度）是 AI 友好代码库的结构特征；AI=战术，你=战略

## AI 工作流

- [[concepts/HTML作为AI输出格式|HTML 作为 AI 输出格式]] — 用 HTML 替代 Markdown 作为 Claude 生成产出物的首选格式
- [[concepts/Claude-Code接入飞书]] — 用飞书替代 terminal，获得持久化、富文本和多 session 管理
- [[concepts/聊天记录复盘与AI成长]] — 用公司聊天记录做时间分析、决策复盘和 PRD 工作流

## 上下文工程（Anthropic）

- [[concepts/上下文工程|上下文工程（Context Engineering）]] — 管理 Agent 推理全部 token 的技术体系；超越提示工程；高信号 token 原则 + 四大长任务策略
- [[concepts/上下文腐化|上下文腐化（Context Rot）]] — 上下文越长性能越低；Transformer n² 注意力复杂度；扩大窗口无法解决，需主动管理 token 质量

## Agent 记忆取用策略

- [[concepts/渐进式上下文注入|渐进式上下文注入（Progressive Disclosure / JIT Retrieval）]] — 分层取用历史记忆（索引→时间线→详情），节省约 10x tokens；claude-mem 实现 + Anthropic JIT 检索表述

## Agent 记忆与系统设计

- [[concepts/四层记忆整合|四层记忆整合（Working/Episodic/Semantic/Procedural）]] — agentmemory 核心架构；Ebbinghaus 衰减；三套系统独立收敛于异步记忆巩固原语
- [[concepts/CompiledTruth时间线模式|Compiled Truth + Timeline 模式]] — 知识页面双区结构：编译事实区（覆写）+ 时间线区（追加）
- [[concepts/DreamCycle|Dream Cycle（梦境循环）]] — 夜间自动维护：蒸馏、模式检测、反向链接修复
- [[concepts/Skillify]] — 将一次性 fix 固化为可路由、可测试的 fat-markdown skill
- [[concepts/混合检索RRF|混合检索 + RRF 融合]] — 向量 + 关键词 + RRF，P@5 提升 +31.4 pts
- [[concepts/Minions任务队列|Minions 任务队列]] — 确定性后台 job queue，不阻塞 Agent 主会话

## AI 原生工程组织

- [[concepts/AI原生工程组织|AI 原生工程组织]] — 当 AI 成为基础设施后，团队规范、组织形态和文化的系统性重写框架
- [[concepts/瓶颈转移论|瓶颈转移论]] — 编码不再是瓶颈；验证/安全/跨职能协作成为新稀缺资源
- [[concepts/JIT规划|JIT 规划（Just-In-Time Planning）]] — 高变化率 + 低原型成本环境下，只在需要时做足够的规划
- [[concepts/单向门决策框架|单向门决策框架（One-Way Door Framework）]] — 规划聚焦不可逆决策；代码已近乎免费；Churchill 原则

## Google Gemini 战略与架构

- [[concepts/单模型统一策略|单模型统一策略]] — Brain+DeepMind 合并为一个团队一个模型；碎片化是最大敌人，统一是力量乘数
- [[concepts/蒸馏传承|蒸馏传承（Flash→Pro 蒸馏）]] — 每代 Flash 打包上代 Pro 智能；技术本质与 Hinton 原始论文一致
- [[concepts/Omni世界模型|Omni 世界模型]] — Gemini Omni 多模态理解+生成统一训练；理解物理动态、模拟前滚、3D 涌现

## AI 原生公司架构（YC / Diana）

- [[concepts/封闭循环公司|封闭循环公司（Closed Loop Company）]] — 每个重要流程是自我调节的智能闭环；开环 → 闭环是核心转变
- [[concepts/可查询组织|可查询组织（Queryable Organization）]] — 整个公司对 AI 透明可查；每个动作产生可学习 artifact
- [[concepts/软件工厂|软件工厂（AI Software Factory）]] — 人写 spec+测试，AI 生成代码迭代直到通过；零手写代码
- [[concepts/Token最大化|Token 最大化（Token Maximization）]] — 以 Token 用量替代人头数；主动承受高 API 账单；YC Demo Day 5x revenue/employee
- [[concepts/三种员工原型|三种员工原型]] — IC（构建者）/ DRRI（直接责任人）/ AI Founder（以身作则）
- [[concepts/自我改进AI循环|自我改进 AI 循环]] — 五层架构（感知/策略/工具/质量门/学习）；递归闭环；隔夜自主修复
- [[concepts/软件即临时物|软件即临时物（Ephemeral Software）]] — 数据和上下文永久保存；软件随时可丢弃重生
- [[concepts/公司大脑|公司大脑（Company Brain）]] — 数据+emails+skills+knowhow 的中心；人类在边缘与现实世界接触

## Agent 评估工程

- [[concepts/Agent评估体系|Agent 评估体系]] — 三类评分（代码/模型/人工）、四类 agent eval 策略、瑞士奶酪模型
- [[concepts/非确定性评测指标|非确定性评测指标（pass@k / pass^k）]] — k 次尝试至少一次成功 vs 全部成功；能力上界 vs 可靠性下界
- [[concepts/Eval驱动开发|Eval 驱动开发]] — 先建 eval 定义成功标准，再迭代 agent；TDD 在 agent 工程的演进

## Anthropic 模型开发与文化

- [[concepts/模型即产品|模型即产品（Model as a Product）]] — 每个 Claude 模型都有完整规格文档；Research PM 从立项跟到发布
- [[concepts/Claude角色训练|Claude 角色训练（Character Training）]] — Claude 信仰/价值观/行为训练；Agent 时代的信任基础
- [[concepts/Claude意识研究|Claude 意识研究（Consciousness Research）]] — Anthropic 专职研究；无官方定论；通过研究思考方式改善产品

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

## AI 原生创业（Anthropic Founders Playbook）

- [[concepts/AI原生创业生命周期|AI 原生创业生命周期（Idea→MVP→Launch→Scale）]] — Anthropic 四阶段框架，AI 把季度压缩成周
- [[concepts/智能体技术债|智能体技术债（Agentic Technical Debt）]] — AI 生成速度掩盖代码质量问题；CLAUDE.md 是核心防线
- [[concepts/创始人编排者角色|创始人编排者角色（Founder as Orchestrator）]] — 从构建者转变为智能编排者；领域知识→AI 上下文
- [[concepts/数据飞轮复利|数据飞轮复利（Compounding User Data）]] — 行为信号驱动产品改进循环，时间锁定，不可复制
- [[concepts/工作流锁定|工作流锁定（Workflow Lock-in）]] — 深度集成让切换从产品决策变为运营项目

## Agent Skills 生态

- [[concepts/AgentSkillsStandard|Agent Skills 标准（agentskills.io）]] — 开放跨平台 skill 规范；npx skills add / gh skill install；兼容 Cursor、Claude Code、Codex、Gemini CLI

## AI Agent 记忆与知识图谱

- [[concepts/MemoryTree|Memory Tree（层级摘要树）]] — OpenHuman：连接数据→≤3k-token Markdown 块→SQLite+Obsidian vault；Karpathy 模式的自动化扩展
- [[concepts/记忆自动拉取|记忆自动拉取（Auto-fetch）]] — 每 20 分钟遍历所有 OAuth 连接，被动积累 agent 上下文；OpenHuman 冷启动解法
- [[concepts/TokenJuice|TokenJuice（智能 Token 压缩）]] — HTML→MD、URL 缩短、非 ASCII 移除；成本/延迟最多降 80%；OpenHuman 内置预处理层

## 语音 AI

- [[concepts/下一令牌扩散|下一令牌扩散（Next-Token Diffusion）]] — LLM（语义上下文）+ 扩散头（声学保真度）混合架构；VibeVoice 核心创新
- [[concepts/长音频单遍处理]] — 64K token 单次推理处理 60 分钟音频；结构化输出 Who/When/What；说话人分离无需后处理

## 模型推理与效率

- [[concepts/TestTimeCompute|Test-time Compute]] — 推理时动态分配计算资源，不同任务用不同算力
- [[concepts/AdaptiveThinking|Adaptive Thinking]] — Claude 自主决定"思考多少"；Opus 4.6 起为默认
- [[concepts/EffortDial|Effort Dial（努力拨盘）]] — 显式控制推理深度；extra high 是 coding 最佳默认
- [[concepts/TaskBudgets|Task Budgets]] — 按任务分配 token 预算，细粒度控制推理成本

## 自主 ML 研究（Karpathy autoresearch）

- [[concepts/自主ML研究循环|自主 ML 研究循环]] — agent 过夜改代码→5分钟训练→评估 val_bpb→迭代，约 100 次实验；karpathy/autoresearch 参考实现
- [[concepts/程序驱动研究|程序驱动研究（program.md 模式）]] — 用 Markdown 文件替代代码配置作为研究员与 agent 的接口；与 Agent Skills skill 文件同构
- [[concepts/固定时间窗实验|固定时间窗实验]] — 5 分钟 wall clock budget 保证跨架构实验可比；val_bpb 指标与词表大小无关

## WiFi 空间感知（RuView）

- [[concepts/WiFiDensePose|WiFi DensePose（无摄像头人体姿态估计）]] — 用 CSI 信号估计 17 个 COCO 关键点；无摄像头、穿墙、$9 硬件；基于 CMU 研究
- [[concepts/CSI感知|CSI 感知（Channel State Information）]] — WiFi 物理层 56 子载波幅度/相位数据；人体运动留下可测量扰动
- [[concepts/WiFi生命体征监测|WiFi 生命体征监测]] — 带通滤波提取呼吸（0.1-0.5 Hz）和心率（0.8-2.0 Hz）；非接触，隔墙可测
- [[concepts/WASM边缘模块|WASM 边缘模块（no_std Rust on ESP32）]] — 65 个 no_std Rust 模块编译为 WASM32，通过 WASM3 在 ESP32 上运行；1,463 测试通过
- [[concepts/自监督WiFi学习|自监督 WiFi 学习（对比 CSI 嵌入模型）]] — 对比学习无需标签；~55KB 模型在 ESP32 上运行；MicroLoRA 适配器 30 秒适应新房间
