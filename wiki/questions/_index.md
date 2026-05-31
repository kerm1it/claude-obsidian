---
type: index
title: "问题索引"
created: 2026-05-05
updated: 2026-05-30
tags:
  - wiki
  - questions
status: active
---

# 问题

## AI 知识体系

- [[Research: AI知识体系总览]] — 初始全景研究综述，合并现有 vault 知识和实时权威来源，建立 8 层系统生成链
- [[Review: AI知识体系稳定 v1 结构验收]] — 最终结构验收：确认 8 层链路、边界概念、学习路线和 research loop 合约已收口为 stable v1
- [[Research: 微调 vs RAG vs 上下文工程]] — 第一轮单点 research：什么时候改上下文、什么时候检索、什么时候改权重
- [[Research: RAG 与 Memory 边界]] — 第二轮单点 research：区分外部知识检索、长期主体连续性、短期上下文和可复用 skill
- [[Research: Agent harness 与 trace eval]] — 第三轮单点 research：把 harness 定义为 agent 运行时，并连接 trace、eval、sandbox 和可靠性
- [[Research: Dream 与 self-improvement 工程原语]] — 第四轮单点 research：把 dream/self-improvement 拆成记忆巩固、系统改造和权重更新三档成熟度
- [[Research: Skill 与 tool memory workflow 边界]] — 第五轮单点 research：把 skill 定义为第 4 层程序性知识包，并区分 tool、memory、workflow、eval 和安全边界
- [[Research: 推理时计算与 reasoning]] — 第六轮单点 research：把 reasoning / test-time compute 归入第 3 层，并连接 agent loop、verifier、eval 和成本约束
- [[Research: 多模态与世界模型边界]] — 第七轮单点 research：区分多模态、世界模型、VLA、embodied agent 和 simulation eval
- [[Research: Serving 成本 延迟 边界]] — 第八轮单点 research：把 serving 归入第 3 层 inference runtime，并连接第 7 层产品 SLO、unit economics 和第 6 层监控指标
- [[Research: Skill library routing lifecycle]] — 第九轮单点 research：skill library 的路由、归因、更新、退役和供应链治理
- [[Research: Reasoning eval verifier 边界]] — 第十轮单点 research：reasoning verifier、process supervision、trace grading、reward model 与 eval harness 的稳定边界
- [[Research: Multimodal eval simulation eval 边界]] — 第十一轮单点 research：静态多模态、视频/音频、生成安全、world-model 和 embodied simulation eval 的边界
- [[Research: Product organization layer 边界]] — 第十二轮单点 research：第 7 层如何把可靠 AI 能力变成产品表面、工作流、组织角色、单位经济和反馈飞轮
- [[Research: Model routing mixture 边界]] — 第十三轮单点 research：model selection、routing、cascade、MoE、MoA 和 compound system model allocation 的边界
- [[Research: Reward hacking eval overfitting 边界]] — 第十四轮单点 research：reward、grader、benchmark、KPI 和 self-improvement 反馈闭环如何被优化压力污染
- [[Research: Data flywheel feedback loop 边界]] — 第十五轮单点 research：真实使用反馈如何安全分流到 eval、RAG、memory、skill、router、training 和 self-improvement
- [[Research: Product feedback closure data flywheel actionability 边界]] — 第五十四轮单点 research：真实反馈如何证明已经被授权、归因、分流、行动、验证并关闭
- [[Research: Data rights privacy consent 边界]] — 第十六轮单点 research：数据权利、隐私和 consent 如何约束 service、memory、eval、training 和供应商共享
- [[Research: Tool risk permissioning 边界]] — 第十七轮单点 research：agent 工具动作如何进入权限、沙箱、审批、审计和回滚边界
- [[Research: AI safety ops governance 边界]] — 第十八轮单点 research：AI 风险证据如何变成组织里的 release gate、owner、monitoring、incident response 和 audit
- [[Research: Data quality label quality 边界]] — 第十九轮单点 research：反馈、label、trace、RAG 文档和训练候选如何通过第 6 层质量门
- [[Research: Multi-provider governance 边界]] — 第二十轮单点 research：多 provider/model/tool 进入 routing 前如何统一数据、地域、retention、training use、SLA、audit 和 fallback
- [[Research: Agent identity delegation 边界]] — 第二十一轮单点 research：agent 如何携带身份、委托链、scope、审计和撤销路径进入工具动作
- [[Research: AI incident response postmortem 边界]] — 第二十二轮单点 research：AI 事故如何进入分级、止血、取证、沟通、复盘和 regression eval
- [[Research: Synthetic data governance 边界]] — 第二十三轮单点 research：合成数据如何按用途进入训练、eval、RAG、memory、skill 或 self-improvement
- [[Research: Dataset lineage provenance graph 边界]] — 第二十四轮单点 research：样本、trace、RAG、memory、skill、eval、training 和模型版本如何形成可审计证据血缘
- [[Research: Data deletion unlearning impact 边界]] — 第二十五轮单点 research：删除请求如何穿透 AI 系统，并在必要时触发 retraining、machine unlearning、model replacement 或输出抑制
- [[Research: Human feedback annotation ops 边界]] — 第二十六轮单点 research：人类示范、偏好、纠错、gold label 和 expert review 如何经过 rubric、QA、仲裁和 lineage 变成可用证据
- [[Research: Evaluation dataset lifecycle benchmark governance 边界]] — 第二十七轮单点 research：eval set、hold-out、public benchmark、regression suite、red-team set 如何治理版本、泄漏、饱和、刷新和退役
- [[Research: Model release rollback gate 边界]] — 第二十八轮单点 research：模型、prompt、router、skill、tool、provider 变更如何进入发布、灰度、回滚和迁移 gate
- [[Research: LLM-as-judge AI feedback calibration 边界]] — 第二十九轮单点 research：模型裁判、AI 标注、RLAIF teacher 和 judge panel 如何用 human gold、bias suite 和生产结果校准
- [[Research: Eval result interpretation decision threshold 边界]] — 第三十轮单点 research：eval score、uncertainty、guardrail、slice、SLO 和风险阈值如何变成发布、回滚、灰区调查或人工复核决策
- [[Research: Production contract compatibility test 边界]] — 第三十一轮单点 research：产品行为契约如何变成模型/provider 更新前的 compatibility suite 和 release gate 证据
- [[Research: Judge drift grader observability 边界]] — 第三十二轮单点 research：LLM judge、rubric、prompt、human anchor 和 production correlation 如何被持续监控，防止评分器漂移污染决策
- [[Research: Intolerable risk threshold stop rule 边界]] — 第三十三轮单点 research：高风险 capability、法律禁止、safeguard 不足和 severe incident 如何触发 no-go、pause、restrict、rollback 或 external review
- [[Research: Eval uncertainty communication release card 边界]] — 第三十四轮单点 research：eval 分数、不确定性、局限、hard stop、owner 和 post-release monitor 如何写成 release/eval card 给第 7 层决策者审查
- [[Research: Offline online eval correlation 边界]] — 第三十五轮单点 research：离线 eval、release card 预测和线上 production outcome 如何比较同向性，并校准 eval trust tier、threshold、dataset 和 release gate
- [[Research: Safety case assurance case 边界]] — 第三十六轮单点 research：高风险 AI 系统如何把 eval、red-team、release card、monitoring 和 safeguards 组织成 claims-arguments-evidence 发布论证
- [[Research: Post-release eval drift 边界]] — 第三十七轮单点 research：发布后如何监控 release card、threshold、judge、offline/online correlation 和 safety evidence 是否 stale
- [[Research: Eval portfolio metric hierarchy 边界]] — 第三十八轮单点 research：第 6 层如何把 benchmark、hold-out、regression、red-team、judge/human、online 和 SLO 组成分层证据组合
- [[Research: Evidence freshness stale proof 边界]] — 第三十九轮单点 research：如何判断 eval、release card、safety case、monitor、judge 和 benchmark 证据是否仍 fresh
- [[Research: Monitor ownership escalation ladder 边界]] — 第四十轮单点 research：第 6 层监控/eval 信号如何接到 owner、SLA、incident、release gate 或 risk elevation
- [[Research: Metric conflict resolution 边界]] — 第四十一轮单点 research：hard stop、guardrail、primary、slice、online、SLO 和 business metric 冲突时如何排序、升级和行动
- [[Research: Evidence attestation signed eval artifact 边界]] — 第四十二轮单点 research：eval artifact、模型、prompt、judge、dataset、container 和 release evidence 如何通过 digest、signature、policy verification 和 trust root 变成可验证证据
- [[Research: Monitor tabletop runbook drill 边界]] — 第四十三轮单点 research：monitor owner、on-call、incident command、release gate、risk owner 和 provider POC 如何通过 tabletop、injects 和 runbook drill 被验证
- [[Research: Override governance residual risk acceptance 边界]] — 第四十四轮单点 research：exception、override 和 residual risk acceptance 如何在不绕过质量门的情况下进入 owner、expiry、monitor、rollback 和审计
- [[Research: Verifier policy trust root rotation 边界]] — 第四十五轮单点 research：verifier policy、trust root、签名身份轮换、失效处理和 re-verification 如何保护 signed evidence
- [[Research: Evidence retention audit packet lifecycle 边界]] — 第四十六轮单点 research：release/eval/safety/incident/override evidence 如何长期保留、检索、重验、legal hold、销毁和审计
- [[Research: Override debt exception analytics dashboard 边界]] — 第四十七轮单点 research：override rate、expired exception、renewal、repeat owner、risk exposure 和 incident conversion 如何变成治理反馈
- [[Research: Cross-verifier policy drift conformance test 边界]] — 第四十八轮单点 research：CI、release gate、admission controller、本地 verifier 和第三方 verifier 如何检测 policy/root/engine 漂移
- [[Research: Evidence minimization privacy preserving audit packet 边界]] — 第四十九轮单点 research：audit packet 如何在可审计、可重验和少留少披露敏感数据之间稳定取边界
- [[Research: Release gate debt gate bypass detection 边界]] — 第五十轮单点 research：release gate 如何检测 admin bypass、shadow approval、direct-to-prod、stale exception 和 gate config drift
- [[Research: Dashboard calibration governance metric quality 边界]] — 第五十一轮单点 research：治理 dashboard 指标如何避免指标剧场、统计错觉、漏报和无效行动
- [[Research: Self-improvement gate change-risk budget 边界]] — 第五十二轮单点 research：self-improvement proposed diff 如何按 target layer、risk budget、evidence、rollback 和 owner 准入
- [[Research: Memory skill governance drift 边界]] — 第五十三轮单点 research：长期 memory、skill 和 SKILL.md 如何避免过时、投毒、权限漂移、路由漂移和不可解释更新
