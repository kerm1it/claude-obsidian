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

## AI 知识体系

- [[concepts/AI系统生成链|AI 系统生成链]] — 稳定分类法：基础理论 → 模型构建 → 推理能力 → 上下文知识 → Agent 系统 → 评估可靠性 → 产品组织 → 自我改进，并用反馈环反哺前层
- [[concepts/微调RAG上下文工程选择框架|微调 RAG 上下文工程选择框架]] — 判断什么时候改 prompt/context、什么时候用 RAG、什么时候微调或蒸馏；连接模型构建层、上下文知识层和评估层
- [[concepts/RAG与Memory边界|RAG 与 Memory 边界]] — RAG 检索外部知识，Memory 维护 agent/用户/组织连续性；连接上下文工程、Agent 系统、eval 和 dream 巩固
- [[concepts/AgentHarness与TraceEval|Agent Harness 与 Trace Eval]] — agent 的运行时层与可靠性桥梁：harness 生产 trace，eval 消费 trace 并反哺 context、tools、memory 和 model
- [[concepts/Dream与SelfImprovement工程原语|Dream 与 Self-Improvement 工程原语]] — 第 8 层反馈环：trace → eval → dream/reflection → diff → gate → apply，反哺 memory、context、tools、harness、eval 和 weights
- [[concepts/Skill与ToolMemory边界|Skill 与 Tool / Memory / Workflow 边界]] — skill 是第 4 层可版本化程序性知识包，连接第 5 层 harness/tool use、第 6 层 eval/security 和第 8 层 self-improvement
- [[concepts/ReasoningEvalVerifier边界|Reasoning Eval / Verifier 边界]] — 第 6 层质量接口：outcome verifier、process verifier、trace grader、CoT monitor 和 reward model 如何约束 reasoning、agent trace、训练和自我改进
- [[concepts/MultimodalEvalSimulationEval边界|Multimodal Eval / Simulation Eval 边界]] — 第 6 层质量门：静态多模态、视频/音频、生成安全、世界模型和 embodied agent 如何被评估
- [[concepts/Serving成本延迟边界|Serving 成本延迟边界]] — 第 3 层 inference runtime 到第 7 层产品 SLO 的接口：prefill/decode、KV cache、batching、prompt caching、TTFT/TPOT、cost/success
- [[concepts/SkillLibraryRouting生命周期|Skill Library Routing 生命周期]] — 第 4 层程序性知识库治理：collection、metadata、retrieval、selection、execution、outcome attribution、update/retire
- [[concepts/ProductOrganizationLayer边界|Product / Organization Layer 边界]] — 第 7 层产品组织接口：把可靠能力嵌入产品表面、工作流、组织角色、单位经济和数据飞轮，并反哺 eval/context/model/self-improvement
- [[concepts/ModelRoutingMixture边界|Model Routing / Mixture 边界]] — 第 3 层 inference control：选择模型、effort、cascade、ensemble 或 per-module allocation，并由 eval 和产品 SLO 约束
- [[concepts/RewardHackingEvalOverfitting边界|Reward Hacking / Eval Overfitting 边界]] — 第 6 层质量门失效模式：reward、grader、benchmark、KPI 或反馈闭环被优化压力污染
- [[concepts/DataFlywheelFeedbackLoop边界|Data Flywheel / Feedback Loop 边界]] — 第 7 层反馈接口：把真实使用信号分流到 eval、RAG、memory、skill、router、training candidate 和 self-improvement
- [[concepts/ProductFeedbackClosureActionability边界|Product Feedback Closure / Actionability 边界]] — 第 7 层反馈闭环边界：证明真实反馈已进入有 owner、artifact、验证、关闭证据和 reopen 条件的行动，而不只是被收集或展示
- [[concepts/DataRightsPrivacyConsent边界|Data Rights / Privacy / Consent 边界]] — 第 7 层数据用途闸门：决定数据能否进入 service、memory、eval、training 或 vendor sharing，并约束保留、删除、导出和审计
- [[concepts/DataDeletionUnlearningImpact边界|Data Deletion / Unlearning Impact 边界]] — 第 7 层数据生命周期执行闭环：把删除/撤回/保留到期/事故请求落实到 logs、RAG、memory、eval、training、model weights、provider 和 audit
- [[concepts/ToolRiskPermissioning边界|Tool Risk / Permissioning 边界]] — 第 5 层动作准入：给 tool call 加风险层、scope、sandbox、approval、audit 和 rollback 边界
- [[concepts/AISafetyOpsGovernance边界|AI Safety Ops / Governance 边界]] — 第 7 层风险运行系统：把 eval、red-team、incident 和 monitoring 证据转成 owner、release gate、risk register、incident response 和 audit
- [[concepts/IntolerableRiskThresholdStopRule边界|Intolerable Risk Threshold / Stop Rule 边界]] — 第 7 层高风险停机边界：把 risk evidence 转成 no-go、pause、restrict、rollback、external review 和 required safeguards
- [[concepts/SafetyCaseAssuranceCase边界|Safety Case / Assurance Case 边界]] — 第 7 层高风险发布论证边界：把 eval、red-team、release card、monitoring、safeguard 和 residual risk 组织成 claims-arguments-evidence 审查包
- [[concepts/ModelReleaseRollbackGate边界|Model Release / Rollback Gate 边界]] — 第 7 层变更控制边界：把 eval、monitoring、lineage 和风险证据转成 model/prompt/router/skill/tool/provider 的发布、灰度、回滚和迁移决策
- [[concepts/ReleaseGateDebtBypassDetection边界|Release Gate Debt / Gate Bypass Detection 边界]] — 第 7 层发布治理健康边界：检测真实生产变更是否绕过 release gate、protected environment、approval、attestation 或 structured exception
- [[concepts/DashboardCalibrationGovernanceMetricQuality边界|Dashboard Calibration / Governance Metric Quality 边界]] — 第 7 层治理测量质量边界：校准 dashboard 指标的定义、血缘、新鲜度、覆盖、行动有效性和 anti-gaming 风险
- [[concepts/MonitorOwnershipEscalationLadder边界|Monitor Ownership / Escalation Ladder 边界]] — 第 7 层监控责任链：把 monitor、eval breach、stale evidence 和 user report 接到 owner、SLA、incident、release gate 或 risk elevation
- [[concepts/DataQualityLabelQuality边界|Data Quality / Label Quality 边界]] — 第 6 层数据质量门：判断反馈、label、trace、RAG 文档和训练候选是否可进入 eval、training、RAG、memory 或 skill
- [[concepts/HumanFeedbackAnnotationOps边界|Human Feedback / Annotation Ops 边界]] — 第 6 层人类判断证据生产系统：把示范、偏好排序、纠错、gold label 和 expert review 转成 eval、reward、training 或产品证据
- [[concepts/LLMJudgeAIFeedbackCalibration边界|LLM-as-Judge / AI Feedback Calibration 边界]] — 第 6 层自动判断校准边界：把 LLM judge、AI 标注、RLAIF teacher、rubric grader 和 judge panel 当成需要 human gold 与 bias tests 校准的测量仪器
- [[concepts/JudgeDriftGraderObservability边界|Judge Drift / Grader Observability 边界]] — 第 6 层评分器健康监控边界：持续观察 judge model、prompt、rubric、human anchor、score distribution、bias 和 production correlation 是否漂移
- [[concepts/EvalUncertaintyCommunicationReleaseCard边界|Eval Uncertainty Communication / Release Card 边界]] — 第 6 层证据表达边界：把 eval 分数、CI、slice、flakiness、judge health、limitation、owner 和 monitor 打包成第 7 层可审查 release/eval card
- [[concepts/OfflineOnlineEvalCorrelation边界|Offline / Online Eval Correlation 边界]] — 第 6 层预测有效性边界：验证离线 eval、release card 预测和线上 production outcome 是否同向，决定指标 trust tier、refresh 或 retire
- [[concepts/PostReleaseEvalDrift边界|Post-release Eval Drift 边界]] — 第 6 层发布后证据保鲜边界：监控 release card、threshold、judge、offline/online correlation 和 safety evidence 是否随生产变化而 stale
- [[concepts/EvalPortfolioMetricHierarchy边界|Eval Portfolio / Metric Hierarchy 边界]] — 第 6 层证据组合边界：把 benchmark、hold-out、regression、red-team、judge/human、online 和 SLO 组织成有优先级的质量门组合
- [[concepts/MetricConflictResolution边界|Metric Conflict Resolution 边界]] — 第 6 层证据冲突解释边界：当 hard stop、guardrail、primary、slice、online、SLO 和 business metric 冲突时定义优先级和行动
- [[concepts/EvidenceFreshnessStaleProof边界|Evidence Freshness / Stale Proof 边界]] — 第 6 层证据有效期边界：记录证据的适用范围、依赖、失效触发器和 fresh/stale/expired/invalidated 状态
- [[concepts/EvidenceAttestationSignedEvalArtifact边界|Evidence Attestation / Signed Eval Artifact 边界]] — 第 6 层证据完整性边界：给 eval result、model、prompt、judge、dataset、container 和 release evidence 加 digest、signature、producer、trust root 和 verifier policy
- [[concepts/VerifierPolicyTrustRootRotation边界|Verifier Policy / Trust Root Rotation 边界]] — 第 6 层证据验收策略边界：定义 signed evidence 通过验证所需的 identity、issuer、predicate、trust root、policy version、rotation 和 revocation
- [[concepts/CrossVerifierPolicyDriftConformanceTest边界|Cross-verifier Policy Drift / Conformance Test 边界]] — 第 6 层策略一致性边界：验证 CI、release gate、admission controller、本地 verifier 和第三方 verifier 是否执行同一 policy/root 语义
- [[concepts/EvidenceRetentionAuditPacketLifecycle边界|Evidence Retention / Audit Packet Lifecycle 边界]] — 第 7 层证据记录治理边界：把 release、eval、safety、incident 和 override evidence 变成可长期检索、重验、legal hold 和处置的 audit packet
- [[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界|Evidence Minimization / Privacy-preserving Audit Packet 边界]] — 第 7 层隐私化证据治理边界：用最小充分证据、private annex、选择性披露和处置记录证明 audit claim
- [[concepts/OverrideDebtExceptionAnalyticsDashboard边界|Override Debt / Exception Analytics Dashboard 边界]] — 第 7 层治理健康观测边界：把单条例外聚合为例外率、过期、续期、重复 owner、风险暴露和事故转化指标
- [[concepts/MonitorTabletopRunbookDrill边界|Monitor Tabletop / Runbook Drill 边界]] — 第 7 层组织演练边界：用场景、injects、runbook drill 和 AAR/IP 验证 monitor owner、on-call、IC、release gate、risk owner 和 provider handoff 是否可执行
- [[concepts/OverrideGovernanceResidualRiskAcceptance边界|Override Governance / Residual Risk Acceptance 边界]] — 第 7 层受控例外边界：把 exception、gray-zone evidence 和 residual risk acceptance 绑定到 hard-stop check、owner、authority、expiry、monitor、rollback 和审计
- [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界|Evaluation Dataset Lifecycle / Benchmark Governance 边界]] — 第 6 层 eval 数据资产治理：管理 dev/regression/private hold-out/public benchmark/red-team/canary 的 split、版本、泄漏、刷新、退役和 release gate 绑定
- [[concepts/MultiProviderGovernance边界|Multi-provider Governance 边界]] — 第 7 层供应商控制面：先按数据用途、地域、retention、training use、SLA 和风险过滤 provider，再交给 routing 或 tool use
- [[concepts/AgentIdentityDelegation边界|Agent Identity / Delegation 边界]] — 第 5 层身份委托边界：绑定 actor、principal、grant、scope、credential、audit 和 revocation
- [[concepts/AIIncidentResponsePostmortem边界|AI Incident Response / Postmortem 边界]] — 第 7 层事故闭环：把监控/eval/用户报告转成止血、取证、沟通、复盘、action item 和 regression eval
- [[concepts/SyntheticDataGovernance边界|Synthetic Data Governance 边界]] — 第 6 层合成样本准入门：判断 synthetic train/eval/RAG/memory/skill/self-improvement 候选能否成为证据
- [[concepts/DatasetLineageProvenanceGraph边界|Dataset Lineage / Provenance Graph 边界]] — 第 6 层证据血缘底座：追踪样本、trace、RAG、memory、skill、eval、training 和模型版本之间的来源、转换和影响面

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

## 上下文压缩

- [[concepts/上下文压缩|上下文压缩]] — Headroom 驱动的 Agent 上下文 token 优化；6 种算法+可逆压缩；与上下文工程/腐化/JIT 四层体系

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
- [[concepts/Omni世界模型|Omni 世界模型]] — Gemini Omni 多模态理解+生成统一训练；连接多模态信号与世界动态模拟
- [[concepts/多模态与世界模型边界|多模态与世界模型边界]] — 区分多信号输入/输出、长程多模态上下文、动态模拟、行动条件预测和 VLA/embodied agent

## Claude Code 编排与多 Agent

- [[concepts/DynamicWorkflows|Dynamic Workflows]] — Claude Code 动态编写多 Agent harness；六种模式 + 三种单上下文失败模式；Opus 4.8 核心能力
- [[concepts/PlanExecute循环|Plan-Execute 循环]] — Matt Van Horn 推广的 Agentic Engineering 核心工作流；/ce-plan→/ce-work；计划给 Agent，人类提供信号
- [[concepts/MultimodalEvalSimulationEval边界|Multimodal Eval / Simulation Eval 边界]] — 多模态和世界模型的可靠性评估：MMMU、Video-MME、WorldModelBench、WorldSimBench、SIMA/EmbodiedBench

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
- [[concepts/ReasoningEvalVerifier边界|Reasoning Eval / Verifier 边界]] — 区分最终答案 verifier、过程 verifier、trace grader、CoT monitor、reward model 和 eval harness
- [[concepts/RewardHackingEvalOverfitting边界|Reward Hacking / Eval Overfitting 边界]] — 防止 eval、reward model、benchmark 和 KPI 被优化压力钻空子
- [[concepts/MultimodalEvalSimulationEval边界|Multimodal Eval / Simulation Eval 边界]] — 区分多模态理解 eval、生成安全 eval、世界模型 eval 和 simulation/embodied eval
- [[concepts/EvalResultInterpretationDecisionThreshold边界|Eval Result Interpretation / Decision Threshold 边界]] — 把 eval score、uncertainty、guardrail、slice 和风险容忍度转成 pass/fail/gray-zone/canary/rollback 决策
- [[concepts/EvalUncertaintyCommunicationReleaseCard边界|Eval Uncertainty Communication / Release Card 边界]] — 把不确定性、局限、hard stop、owner、exception 和 post-release monitor 写成 release/eval card，避免决策者误读 eval
- [[concepts/OfflineOnlineEvalCorrelation边界|Offline / Online Eval Correlation 边界]] — 比较离线 eval delta 和线上 production outcome 是否同向，并用真实反馈校准 eval、threshold、dataset 和 release gate
- [[concepts/PostReleaseEvalDrift边界|Post-release Eval Drift 边界]] — 发布后持续判断 release evidence 是否 stale，并触发 eval refresh、metric quarantine、canary、rollback 或 safety case refresh
- [[concepts/EvalPortfolioMetricHierarchy边界|Eval Portfolio / Metric Hierarchy 边界]] — 把多种 eval 资产按 hard stop、guardrail、primary、slice、online、diagnostic 分层，避免一个总分掩盖风险
- [[concepts/MetricConflictResolution边界|Metric Conflict Resolution 边界]] — 处理多指标互相打架时的优先级、gray-zone、override、canary、rollback 和 owner escalation
- [[concepts/EvidenceFreshnessStaleProof边界|Evidence Freshness / Stale Proof 边界]] — 判断每份 eval / release / safety evidence 当前是否仍能支持 claim，并给出降权、刷新、隔离或失效动作
- [[concepts/EvidenceAttestationSignedEvalArtifact边界|Evidence Attestation / Signed Eval Artifact 边界]] — 证明 eval artifact、模型、prompt、judge、dataset、container 和 release evidence 没被替换或篡改，并绑定签名、producer、policy 和 trust root
- [[concepts/VerifierPolicyTrustRootRotation边界|Verifier Policy / Trust Root Rotation 边界]] — 把 signed evidence 接到当前 verifier policy、trust root、root rotation、revocation 和 re-verification，避免签名通过但策略失效
- [[concepts/CrossVerifierPolicyDriftConformanceTest边界|Cross-verifier Policy Drift / Conformance Test 边界]] — 用 golden corpus 比较 local CLI、CI、release gate、admission controller 和 runtime guard 的 allow/deny/reason 是否一致
- [[concepts/EvidenceRetentionAuditPacketLifecycle边界|Evidence Retention / Audit Packet Lifecycle 边界]] — 让 release/eval/safety/incident/override evidence 在多年后仍能被找回、读懂、重验、解释和按政策处置
- [[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界|Evidence Minimization / Privacy-preserving Audit Packet 边界]] — 用字段级 minimization matrix、private annex 和 selective disclosure 控制 audit packet 的敏感数据暴露
- [[concepts/OverrideDebtExceptionAnalyticsDashboard边界|Override Debt / Exception Analytics Dashboard 边界]] — 把 override / exception / residual-risk record 变成治理债务和风险暴露看板，驱动 review、freeze、deny renewal 和 backlog
- [[concepts/ReleaseGateDebtBypassDetection边界|Release Gate Debt / Gate Bypass Detection 边界]] — 发现 admin bypass、shadow approval、direct-to-prod、stale exception 和 gate config drift，并转成 gate debt ledger 与行动闭环
- [[concepts/DashboardCalibrationGovernanceMetricQuality边界|Dashboard Calibration / Governance Metric Quality 边界]] — 判断治理 dashboard 的指标是否定义清楚、可追溯、可校准、可行动，并能避免指标剧场和 Goodhart 风险
- [[concepts/MonitorOwnershipEscalationLadder边界|Monitor Ownership / Escalation Ladder 边界]] — 把监控和 eval 信号分派给 owner、SLA、升级链和可执行动作，避免 orphan alerts
- [[concepts/MonitorTabletopRunbookDrill边界|Monitor Tabletop / Runbook Drill 边界]] — 用 tabletop、injects、runbook drill 和 after-action plan 验证监控责任链、事故角色、release gate 和 provider fallback 是否能在压力下执行
- [[concepts/OverrideGovernanceResidualRiskAcceptance边界|Override Governance / Residual Risk Acceptance 边界]] — 防止 exception 常态化为绕过质量门，要求残余风险接受有 owner、authority、expiry、monitor、rollback 和复审
- [[concepts/ProductionContractCompatibilityTest边界|Production Contract / Compatibility Test 边界]] — 把产品行为、schema、工具、安全、数据处理和 SLO 写成模型/provider 更新前的可测试契约
- [[concepts/JudgeDriftGraderObservability边界|Judge Drift / Grader Observability 边界]] — 监控 LLM judge 和 grader stack 的 human agreement、score drift、bias suite、prompt sensitivity 与生产相关性
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
- [[concepts/DataFlywheelFeedbackLoop边界|Data Flywheel / Feedback Loop 边界]] — 数据飞轮的工程分流：什么进 eval、RAG、memory、skill、training、router 或产品路线
- [[concepts/ProductFeedbackClosureActionability边界|Product Feedback Closure / Actionability 边界]] — 数据飞轮的闭环证明：feedback 绑定 trace、owner、target layer、artifact、验证结果和关闭证据
- [[concepts/SelfImprovementGateChangeRiskBudget边界|Self-Improvement Gate / Change-Risk Budget 边界]] — 第 8 层自我改进 diff 反哺各层前的准入、预算、灰度和回滚边界
- [[concepts/EvidenceRetentionAuditPacketLifecycle边界|Evidence Retention / Audit Packet Lifecycle 边界]] — AI 组织把证据变成可审计组织记忆的记录治理：manifest、storage tier、retrieval、reverify、legal hold、disposition
- [[concepts/OverrideDebtExceptionAnalyticsDashboard边界|Override Debt / Exception Analytics Dashboard 边界]] — AI 组织监控例外债务：例外率、过期、续期、重复 owner、risk-weighted exposure、incident conversion、monitor coverage
- [[concepts/DashboardCalibrationGovernanceMetricQuality边界|Dashboard Calibration / Governance Metric Quality 边界]] — AI 组织校准治理看板：decision inventory、metric definition sheet、lineage、freshness、coverage、action precision、missed risk 和 retire rule
- [[concepts/工作流锁定|工作流锁定（Workflow Lock-in）]] — 深度集成让切换从产品决策变为运营项目

## Agent Skills 生态

- [[concepts/AgentSkillsStandard|Agent Skills 标准（agentskills.io）]] — 开放跨平台 skill 规范；npx skills add / gh skill install；兼容 Cursor、Claude Code、Codex、Gemini CLI
- [[concepts/Skill与ToolMemory边界|Skill 与 Tool / Memory / Workflow 边界]] — 区分 skill、tool、memory、workflow、RAG 和 prompt；强调 routing、eval、token overhead 和供应链安全
- [[concepts/SkillLibraryRouting生命周期|Skill Library Routing 生命周期]] — skill 从单体文件扩展到库级治理后的路由、归因、演化、退役和安全边界

## AI Agent 记忆与知识图谱

- [[concepts/MemoryTree|Memory Tree（层级摘要树）]] — OpenHuman：连接数据→≤3k-token Markdown 块→SQLite+Obsidian vault；Karpathy 模式的自动化扩展
- [[concepts/MemorySkillGovernanceDrift边界|Memory / Skill Governance Drift 边界]] — 第 4 层长期 memory、skill、metadata、scripts 和 references 的过时、投毒、权限、路由与退役治理
- [[concepts/记忆自动拉取|记忆自动拉取（Auto-fetch）]] — 每 20 分钟遍历所有 OAuth 连接，被动积累 agent 上下文；OpenHuman 冷启动解法
- [[concepts/TokenJuice|TokenJuice（智能 Token 压缩）]] — HTML→MD、URL 缩短、非 ASCII 移除；成本/延迟最多降 80%；OpenHuman 内置预处理层

## 语音 AI

- [[concepts/下一令牌扩散|下一令牌扩散（Next-Token Diffusion）]] — LLM（语义上下文）+ 扩散头（声学保真度）混合架构；VibeVoice 核心创新
- [[concepts/长音频单遍处理]] — 64K token 单次推理处理 60 分钟音频；结构化输出 Who/When/What；说话人分离无需后处理

## 模型推理与效率

- [[concepts/TestTimeCompute|Test-time Compute]] — 第 3 层推理时计算：用 thinking、采样、搜索、verifier、tool-interleaved reasoning 和 effort/budget 把运行时预算变成能力，并连接 agent trace/eval
- [[concepts/ReasoningEvalVerifier边界|Reasoning Eval / Verifier 边界]] — 第 3 层 TTC 的第 6 层控制面：score、rerank、gate、train、monitor
- [[concepts/Serving成本延迟边界|Serving 成本延迟边界]] — 第 3 层推理能力进入产品前的成本、延迟、吞吐和 SLO 约束
- [[concepts/ModelRoutingMixture边界|Model Routing / Mixture 边界]] — 第 3 层多模型推理控制：model selection、routing、cascade、MoA 和 MoE 边界
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
