---
type: log
title: "知识库日志"
created: 2026-05-05
updated: 2026-05-05
tags:
  - wiki
  - log
status: active
---

# 知识库日志

## 2026-05-14 ingest | agentmemory — AI 编码智能体持久记忆引擎（rohitg00）

- Source: `.raw/articles/agentmemory-2026-05-13.md`（GitHub repo，README，rohitg00/agentmemory，⭐ 7,121）
- Summary: [[sources/agentmemory-2026-05-13]]
- Pages created: [[sources/agentmemory-2026-05-13]], [[entities/AgentMemory]], [[concepts/四层记忆整合]]
- Pages updated: [[entities/GBrain]], [[entities/ClaudeMem]], [[entities/_index]], [[concepts/_index]], [[index]], [[hot]], [[log]]
- Key insight: agentmemory（rohitg00）是重型 Agent 记忆引擎；核心创新是四层记忆整合（Working/Episodic/Semantic/Procedural）+ 三流检索 RRF（BM25+Vector+Graph），R@5 95.2%，92% token 节省，0 外部 DB；与 claude-mem（75K ⭐）互补：高精度 vs 轻量安装；四层整合与 GBrain Dream Cycle 和 Anthropic Dreaming 三方独立收敛。

## 2026-05-13 ingest | claude-mem — 跨会话持久记忆系统（thedotmack）

- Source: `.raw/articles/claude-mem-2026-05-13.md`（GitHub repo，README + package.json）
- Summary: [[sources/claude-mem-2026-05-13]]
- Pages created: [[sources/claude-mem-2026-05-13]], [[entities/ClaudeMem]], [[concepts/渐进式上下文注入]]
- Pages updated: [[entities/GBrain]], [[concepts/AgentMemoryAPI]], [[entities/_index]], [[concepts/_index]], [[index]], [[hot]], [[log]]
- Key insight: claude-mem（75K ⭐）是目前最流行的 Claude Code 记忆插件；核心创新是渐进式上下文注入（3 层 MCP 工作流，节省 10x tokens）；与 GBrain 互补——轻量易装 vs 重型知识库。

## 2026-05-12 ingest | AI Agents Run My Business and Life — Andrew Wilkinson（Greg Isenberg）

- Source: `.raw/notebooklm/andrew-wilkinson-ai-agents-2026-05-12.md`（YouTube，NotebookLM fulltext，43,289 chars）
- Summary: [[sources/andrew-wilkinson-ai-agents-2026-05-12]]
- Pages created: [[sources/andrew-wilkinson-ai-agents-2026-05-12]], [[people/AndrewWilkinson]], [[entities/Tiny]], [[concepts/自主商业运营]], [[concepts/软件护城河侵蚀]]
- Pages updated: [[entities/GBrain]], [[entities/OpenClaw]], [[entities/_index]], [[people/_index]], [[concepts/_index]], [[index]], [[hot]], [[log]]
- Key insight: Andrew Wilkinson 用 Agent 运营完整 SaaS 业务（support/marketing/dev）和 family office（$4 万/月 Claude 账单替代薪资和 SaaS 费用）；软件护城河正在瓦解，纯功能性 SaaS 定价权崩塌；GBrain + OpenClaw 实战印证。

## 2026-05-12 ingest | Why Coding Is Solved — Boris Cherny（Sequoia Capital）

- Source: `.raw/notebooklm/boris-cherny-coding-solved-2026-05-12.md`（YouTube，NotebookLM fulltext，26,862 chars）
- Summary: [[sources/boris-cherny-coding-solved-2026-05-12]]
- Pages created: [[sources/boris-cherny-coding-solved-2026-05-12]], [[people/BorisCherny]], [[entities/SequoiaCapital]], [[concepts/软件民主化]], [[concepts/ProductOverhang]], [[concepts/Loop机制]]
- Pages updated: [[domains/Claude-Code]], [[entities/_index]], [[people/_index]], [[concepts/_index]], [[index]], [[hot]], [[log]]
- Key insight: Claude Code 的诞生逻辑是 Product Overhang；Boris 个人 100% 由模型写代码，每晚几千 Agent 并行；/loop 是最重要功能；编程将像读写一样民主化；最懂领域的人将是最好的软件作者。

## 2026-05-12 ingest | The Expanding Toolkit — Lucas（Anthropic，Code with Claude）

- Source: `.raw/notebooklm/the-expanding-toolkit-2026-05-12.md`（YouTube，NotebookLM fulltext，17,207 chars）
- Summary: [[sources/the-expanding-toolkit-2026-05-12]]
- Pages created: [[sources/the-expanding-toolkit-2026-05-12]], [[people/Lucas]], [[concepts/ExpandingToolkit]], [[concepts/CodeExecution]], [[concepts/NativeResolutionComputerUse]]
- Pages updated: [[entities/CodeWithClaude]], [[domains/Claude-Code]], [[people/_index]], [[concepts/_index]], [[index]], [[hot]], [[log]]
- Key insight: 脚手架已随模型出货；补偿模型不可靠性的代码半衰期只有几个月；Opus 4.7 在 OSWorld 达 78%，原生支持 1440p 无需缩放；Code Execution Tool 让 write-run-fix 循环在单个 API turn 内完成。

## 2026-05-11 ingest | The Thinking Lever — Matt Bleifer（Anthropic）

- Source: `.raw/notebooklm/the-thinking-lever-2026-05-11.md`（YouTube，NotebookLM fulltext，21,308 chars）
- Summary: [[sources/the-thinking-lever-2026-05-11]]
- Pages created: [[sources/the-thinking-lever-2026-05-11]], [[people/MattBleifer]], [[concepts/TestTimeCompute]], [[concepts/AdaptiveThinking]], [[concepts/EffortDial]], [[concepts/TaskBudgets]]
- Pages updated: [[index]], [[hot]], [[log]]
- Key insight: Test-time compute 是第二条智能扩展路径；三类 token（thinking/tool/text）；Adaptive Thinking 自 Opus 4.6 起为默认；Effort 优于思考开关；extra high 是大多数 coding 场景最佳默认值；低 effort ≠ 低智能（Pokémon 速通实验）。

## 2026-05-11 ingest | 工程技术：在智能体优先的世界中利用 Codex — Ryan Lopopolo（OpenAI）

- Source: `.raw/articles/harness-engineering-openai-2026-02-11.md`（Playwright headless Chrome 抓取，Cloudflare 保护绕过）
- Summary: [[sources/harness-engineering-openai-2026-02-11]]
- Pages created: [[sources/harness-engineering-openai-2026-02-11]], [[people/RyanLopopolo]], [[entities/OpenAI]], [[concepts/智能体优先工程]], [[concepts/代码仓库即记录系统]], [[concepts/智能体GC]]
- Pages updated: [[index]], [[hot]], [[log]]
- Key insight: OpenAI 3 名工程师 5 个月 100 万行代码零人工编码，核心经验：AGENTS.md 是目录不是百科全书；仓库即记录系统；机械强制架构约束；黄金原则+后台 GC 对抗代码熵。与 Fiona Fung 框架和 GBrain DreamCycle 高度同构。

## 2026-05-11 ingest | Memory and Dreaming for Self-Learning Agents — Mahesh（Anthropic）

- Source: `.raw/notebooklm/memory-dreaming-self-learning-agents-2026-05-11.md`（YouTube，NotebookLM fulltext，23,279 chars）
- Summary: [[sources/memory-dreaming-self-learning-agents-2026-05-11]]
- Pages created: [[sources/memory-dreaming-self-learning-agents-2026-05-11]], [[people/Mahesh]], [[concepts/AnthropicDreaming]], [[concepts/AgentMemoryAPI]], [[concepts/乐观并发]]
- Pages updated: [[concepts/DreamCycle]], [[index]], [[hot]], [[log]]
- Key insight: Anthropic 正式发布 Memory API（公测）和 Dreaming（研究预览）。Memory 把记忆建模为文件系统；Dreaming 是离线批处理过程，跨多 Agent transcript 提取模式，与 GBrain DreamCycle 高度同构但独立实现。Harvey 部署后任务完成率 ↑ 6×。

## 2026-05-11 ingest | Running an AI-native engineering org — Fiona Fung（Code with Claude 2026）

- Source: `.raw/articles/ai-native-engineering-org-2026-05-11.md`（YouTube 字幕，yt-dlp auto-captions，约 30 分钟）
- Summary: [[sources/fiona-fung-ai-native-engineering-2026-05-11]]
- Pages created: [[sources/fiona-fung-ai-native-engineering-2026-05-11]], [[people/FionaFung]], [[concepts/AI原生工程组织]], [[concepts/JIT规划]], [[concepts/瓶颈转移论]]
- Pages updated: [[entities/CodeWithClaude]], [[domains/Claude-Code]], [[people/_index]], [[concepts/_index]], [[index]], [[hot]], [[log]]
- Key insight: Fiona Fung（Claude Code 工程负责人）的核心论点：编码吞吐量不再是瓶颈，验证/安全/跨职能协作才是新稀缺资源；团队需要主动重写规范（JIT 规划、代码赢技术争论、扁平 org、管理者先做 IC、明确许可干掉旧流程）。

## 2026-05-11 ingest | GBrain — AI Agent 记忆与知识管理系统

- Source: `.raw/articles/gbrain-2026-05-11.md`（GitHub repo，garrytan/gbrain）
- Summary: [[sources/gbrain-2026-05-11]]
- Pages created: [[sources/gbrain-2026-05-11]], [[people/GarryTan]], [[entities/GBrain]], [[entities/YCombinator]], [[entities/OpenClaw]], [[concepts/CompiledTruth时间线模式]], [[concepts/DreamCycle]], [[concepts/Skillify]], [[concepts/混合检索RRF]], [[concepts/Minions任务队列]]
- Pages updated: [[people/_index]], [[entities/_index]], [[concepts/_index]], [[sources/_index]], [[index]], [[hot]], [[log]]
- Key insight: GBrain 是"给 AI Agent 的大脑"，核心创新是 Compiled Truth+Timeline 双区结构 + 混合检索 RRF，在 BrainBench 上 P@5 比向量 baseline 高 +31.4 pts；Skillify 模式（fat-markdown skill）与本 vault 的 skills/ 高度同构。

## 2026-05-10 ingest | Dario & Daniela Amodei 对谈 —— Code with Claude 开发者大会

- Source: `.raw/notebooklm/dario-daniela-amodei-2026-05-10.md`（NotebookLM ASR，原始 YouTube 64MB m4a，33:10）
- Summary: [[sources/dario-daniela-amodei-conversation-2026-05-10]]
- Pages created: [[sources/dario-daniela-amodei-conversation-2026-05-10]], [[people/DarioAmodei]], [[people/DanielaAmodei]], [[people/AmiVora]], [[entities/CodeWithClaude]], [[concepts/ScalingLaws]], [[concepts/国家级天才数据中心]], [[concepts/HoldLightAndShade]], [[concepts/AmdahlsLawInAI]], [[concepts/单人十亿美金公司]]
- Pages updated: [[people/_index]], [[entities/_index]], [[concepts/_index]], [[sources/_index]], [[index]], [[hot]], [[log]]
- Key insight: Q1 2026 年化增长 80x；Dario 预测 2026 年出现单人十亿美金公司；多 Agent 终极愿景是"数据中心里的天才国家"；Amdahl 定律提醒：AI 加速代码后，安全/验证/架构将成为新瓶颈。

## 2026-05-10 ingest | AI Agent 实践分享会全程回放（2026-05-05）

- Source: `.raw/notebooklm/quanchenghuifang1-2026-05-10.md`（NotebookLM fulltext，原始 MP4 125MB）
- Summary: [[sources/quanchenghuifang1-2026-05-10]]
- Pages created: [[sources/quanchenghuifang1-2026-05-10]], [[people/Zara]], [[people/Sparks]], [[people/Brandon]], [[people/Siqi]], [[people/Haoran]], [[entities/Midas]], [[entities/Pika]], [[entities/MX]], [[entities/Instant]], [[concepts/Claude-Code接入飞书]], [[concepts/聊天记录复盘与AI成长]]
- Pages updated: [[people/_index]], [[entities/_index]], [[concepts/_index]], [[sources/_index]], [[index]], [[hot]], [[log]]
- Key insight: AI Agent 正在从工具演变为数字同事和分身；Claude Code 接飞书、聊天记录复盘、多 Agent 量化交易是三个可直接复用的工作流。

## 2026-05-10 ingest | HTML 的非凡效能 —— Claude Code 最佳输出格式

- Source: `.raw/articles/twitter-2052809885763747935-2026-05-10.md`
- Summary: [[sources/twitter-2052809885763747935]]
- Pages created: [[sources/twitter-2052809885763747935]], [[people/Thariq]], [[entities/Anthropic]], [[concepts/HTML作为AI输出格式]], [[domains/Claude-Code]]
- Pages updated: [[sources/_index]], [[index]], [[hot]], [[log]]
- Key insight: Claude Code 团队建议用 HTML 替代 Markdown 作为 AI 生成产出物的首选格式，信息密度和交互性显著提升，代价是生成时间增加 2–4 倍。

## 2026-05-05

- 将目录名恢复为英文以兼容工具链，保留中文索引内容：[[goals/_index|目标]]、[[learning/_index|学习]]、[[people/_index|人物]]、[[areas/_index|领域]]、[[resources/_index|资源]]、[[projects/_index|项目]]、[[decisions/_index|决策]]、[[reflections/_index|复盘]]。
- 新增个人知识库区域：目标、学习、人物、领域、资源、项目、决策、复盘。
- 清空自带演示 wiki 内容，让 vault 从用户自己的材料开始。
