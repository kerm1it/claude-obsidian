---
type: log
title: "知识库日志"
created: 2026-05-05
updated: 2026-06-10
tags:
  - wiki
  - log
status: active
---

# 知识库日志

## 2026-06-12 ingest | Hivemind — Agent 共享记忆与技能传播系统
- Source: `.raw/articles/activeloopai-hivemind-2026-06-12.md`
- Summary: [[sources/activeloopai-hivemind-2026-06-12]]
- Pages created: [[entities/Activeloop]], [[entities/Hivemind]], [[concepts/Agent共享记忆]], [[concepts/代码库图谱]], [[concepts/跨Agent规则系统]]
- Pages updated: [[concepts/Skillify]], [[entities/GBrain]]
- Key insight: Hivemind 的核心理念——"共享能力必须有共享数据基础"（shared capability intentionally requires shared substrate）——团队所有 Agent 的 traces 进入共享存储，自动挖掘为 SKILL.md，再传播回全团队。这是第 5 层（Agent trace）+ 第 8 层（self-improvement）的工程化组合。

## 2026-06-10 save | AI知识体系学习记录
- Type: learning-note
- Location: [[learning/2026-06-10 AI知识体系学习记录]]
- From: 今日围绕 eval 基线、上下文工程、RAG 与 Memory 边界的提问和澄清
- Pages updated: [[learning/_index]]，[[index]]，[[hot]]，[[log]]
- Key insight: Eval 基线是上下文工程的起点；上下文工程是把模型完成任务所需的高信号信息组织进推理现场；RAG 提供外部知识，Memory 维持用户、agent 或组织在时间中的主体连续性。

## 2026-06-09 save | AI知识体系学习记录
- Type: learning-note
- Location: [[learning/2026-06-09 AI知识体系学习记录]]
- From: 今日围绕 [[domains/AI知识体系]] 的提问和澄清
- Pages updated: [[learning/_index]]，[[learning/AI学习计划-2026]]，[[index]]，[[hot]]，[[log]]
- Key insight: 今日学习把 8 层从分类表串成系统生命周期：第 3 层是运行时能力，第 4 层是任务信息供应，第 5 层承接 agent/subagent/multi-agent，第 8 层通过证据化 diff 反哺第 6、4、2 层；并补充 serving、prefill、decode 和模型蒸馏的基础理解。

## 2026-06-05 canvas | AI知识体系总图
- Canvas: [[canvases/ai-knowledge-system.canvas|AI 知识体系 Canvas]]
- Pages updated: [[domains/AI知识体系]]，[[overview]]，[[hot]]，[[log]]
- Key insight: 将 [[domains/AI知识体系]] 开头的 Mermaid 主链替换为 Obsidian Canvas 嵌入；总图改为自底而上的竖向 ladder，主链展示 1-8 层递进，右侧紫色回流展示第 8 层反哺第 6、4、2 层。

## 2026-06-05 ingest | Dynamic Workflows in Claude Code — Anthropic
- Source: `.raw/articles/claude-code-dynamic-workflows-2026-06-05.md`

## 2026-06-05 ingest | Headroom — Tejas Chopra（14.1K ⭐）
- Source: `.raw/articles/headroom-2026-06-05.md`
- Summary: [[sources/headroom-2026-06-05|Headroom — The context compression layer for AI agents]]
- Pages created: [[sources/headroom-2026-06-05]]，[[entities/Headroom]]，[[TejasChopra]]，[[concepts/上下文压缩]]
- Pages updated: [[entities/_index]]，[[people/_index]]，[[concepts/_index]]，[[sources/_index]]，[[index]]，[[hot]]，[[log]]
- Key insight: 上下文压缩作为上下文工程第四层（工程/腐化/JIT/压缩），可逆压缩+跨 Agent 记忆。

## 2026-06-05 ingest | Every Agentic Engineering Hack I Know — Matt Van Horn
- Source: `.raw/articles/matt-vanhorn-agentic-hacks-2026-06-05.md`
- Summary: [[sources/matt-vanhorn-agentic-hacks-2026-06-05|Every Agentic Engineering Hack I Know (June 2026)]]
- Pages created: [[sources/matt-vanhorn-agentic-hacks-2026-06-05]]，[[MattVanHorn]]，[[concepts/PlanExecute循环]]
- Pages updated: [[people/_index]]，[[concepts/_index]]，[[sources/_index]]，[[index]]，[[hot]]，[[log]]
- Key insight: Plan-Execute 循环：有想法→ce-plan→ce-work；计划给 Agent，人类提供信号（taste/direction/redirect）。

## 2026-06-05 ingest | @trq212: Dynamic Workflows 发布推文
- Source: `.raw/articles/twitter-2061907337154367865-2026-06-05.md`
- Summary: [[sources/claude-code-dynamic-workflows-2026-06-05|A harness for every task: Dynamic Workflows in Claude Code]]
- Pages created: [[sources/claude-code-dynamic-workflows-2026-06-05]]，[[Sid Bidasaria]]，[[concepts/DynamicWorkflows]]
- Pages updated: [[Thariq]]，[[people/_index]]，[[concepts/_index]]，[[sources/_index]]，[[index]]，[[hot]]，[[log]]
- Key insight: Claude Code Opus 4.8 动态编写多 Agent harness；六种模式对抗三种单上下文失败模式。

## 2026-05-31 learning | AI体系学习路线与AI学习计划合并
- Topic: 将新建的 AI 体系学习路线和原有 AI 学习计划结合，避免两套学习入口割裂。
- Pages updated: [[learning/AI学习计划-2026]]，[[learning/AI体系学习路线]]，[[learning/_index]]，[[index]]，[[hot]]，[[log]]
- Key insight: [[learning/AI体系学习路线]] 负责 8 层顺序、概念归属和知识定位；[[learning/AI学习计划-2026]] 负责具体资源、任务、进度和学习产出。日常执行看计划，概念混乱回路线。

## 2026-05-30 review | AI知识体系稳定 v1 结构验收
- Topic: 验收 AI 知识体系是否已经从开放式 research loop 收口为 stable v1。
- Review: [[Review: AI知识体系稳定 v1 结构验收]]
- Pages created: [[Review: AI知识体系稳定 v1 结构验收]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[questions/_index]]，[[index]]，[[hot]]，[[log]]，`skills/autoresearch/references/program.md`
- Key insight: 当前体系已能用 8 层固定结构承接新概念，并形成基础理论 → 模型构建 → 推理能力 → 上下文知识 → Agent 系统 → 评估可靠性 → 产品组织 → 自我改进 → 前面各层的闭环；后续不需要默认继续研究轮。
- Address range: c-000587

## 2026-05-30 research | Product feedback closure data flywheel actionability 边界
- Topic: 第 7 层真实反馈如何证明已经被授权、归因、分流、行动、验证并关闭，而不是停在日志、dashboard 或 backlog。
- Synthesis: [[Research: Product feedback closure data flywheel actionability 边界]]
- Pages created: [[concepts/ProductFeedbackClosureActionability边界]]，[[Research: Product feedback closure data flywheel actionability 边界]]，[[sources/aws-genai-production-feedback-loops-2026]]，[[sources/langsmith-user-feedback-traces-2026]]，[[sources/adaptive-data-flywheel-mape-ai-agent-improvement-2025]]，[[sources/nvidia-data-flywheel-blueprint-distillation-2025]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/ProductOrganizationLayer边界]]，[[concepts/DataFlywheelFeedbackLoop边界]]，[[concepts/DashboardCalibrationGovernanceMetricQuality边界]]，[[concepts/OfflineOnlineEvalCorrelation边界]]，[[concepts/SelfImprovementGateChangeRiskBudget边界]]，[[sources/openai-model-optimization-2026]]，[[sources/openai-evals-business-framework-2025]]，[[sources/langchain-production-monitoring-regression-tests-2026]]，[[sources/aws-prescriptive-genai-production-monitoring-2026]]，[[sources/nvidia-ai-data-flywheel-2026]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Product feedback closure / actionability 主属第 7 层，是 data flywheel 的行动闭环证明：反馈必须绑定 trace、权限、owner、target layer、artifact、验证结果、关闭证据和 reopen 条件，才能真正反哺 eval、RAG/memory、skill/tool、router、training、product 或 incident/governance。
- Address range: c-000581 至 c-000586

## 2026-05-30 research | Memory skill governance drift 边界
- Topic: 第 4 层长期 memory、skill、SKILL.md metadata、scripts 和 references 如何避免过时、投毒、权限漂移、路由漂移和不可解释更新。
- Synthesis: [[Research: Memory skill governance drift 边界]]
- Pages created: [[concepts/MemorySkillGovernanceDrift边界]]，[[Research: Memory skill governance drift 边界]]，[[sources/memmorph-tool-hijacking-memory-poisoning-2026]]，[[sources/poison-once-exploit-forever-memory-poisoning-2026]]，[[sources/hidden-in-memory-sleeper-poisoning-2026]]，[[sources/shadowmerge-graph-memory-poisoning-2026]]，[[sources/memory-poisoning-attack-defense-llm-agents-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/RAG与Memory边界]]，[[concepts/Skill与ToolMemory边界]]，[[concepts/SkillLibraryRouting生命周期]]，[[concepts/SelfImprovementGateChangeRiskBudget边界]]，[[sources/openai-agent-memory-2026]]，[[sources/skillsvote-2026]]，[[sources/under-the-hood-skill-md-2026]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Memory / skill governance drift 主属第 4 层，是把 persistent memory、skill packages、SKILL.md metadata、scripts、references 和 routing hints 当作会影响未来 agent 行为的 operational artifacts 来治理；它要求 owner、scope、permission、provenance、freshness、eval、quarantine、rollback 和 retirement。
- Address range: c-000574 至 c-000580

## 2026-05-30 research | Self-improvement gate change-risk budget 边界
- Topic: 第 8 层 self-improvement proposed diff 如何按 target layer、risk budget、evidence、rollback 和 owner 准入到 memory、skill、tool、harness、eval、policy 或 weights。
- Synthesis: [[Research: Self-improvement gate change-risk budget 边界]]
- Pages created: [[concepts/SelfImprovementGateChangeRiskBudget边界]]，[[Research: Self-improvement gate change-risk budget 边界]]，[[sources/automated-self-testing-quality-gate-llm-applications-2026]]，[[sources/moss-self-evolution-source-rewriting-2026]]，[[sources/autogenesis-self-evolving-agent-protocol-2026]]，[[sources/darwin-godel-machine-self-improving-agents-2025]]，[[sources/nist-ai-rmf-core-manage-change-management-2023]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/Dream与SelfImprovement工程原语]]，[[concepts/自我改进AI循环]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/RewardHackingEvalOverfitting边界]]，[[concepts/DataFlywheelFeedbackLoop边界]]，[[concepts/SyntheticDataGovernance边界]]，[[concepts/EvalResultInterpretationDecisionThreshold边界]]，[[concepts/AISafetyOpsGovernance边界]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Self-improvement gate / change-risk budget 主属第 8 层，是把 dream、agent self-edit、feedback loop、source rewrite 或 weight update 生成的 proposed diff，按目标层级、影响面、可逆性、证据质量和预算消耗转成 auto-apply、sandbox、canary、human review、hold、rollback 或 reject 的准入边界。
- Address range: c-000567 至 c-000573

## 2026-05-30 research | Dashboard calibration governance metric quality 边界
- Topic: 第 7 层如何校准治理 dashboard 指标，避免指标剧场、低质量 signal、误行动和漏报。
- Synthesis: [[Research: Dashboard calibration governance metric quality 边界]]
- Pages created: [[concepts/DashboardCalibrationGovernanceMetricQuality边界]]，[[Research: Dashboard calibration governance metric quality 边界]]，[[sources/nist-sp800-55-vol2-measurement-program-2024]]，[[sources/google-sre-monitoring-distributed-systems-2016]]，[[sources/google-sre-alerting-on-slos-2018]]，[[sources/dora-software-delivery-performance-metrics-2026]]，[[sources/microsoft-responsible-ai-dashboard-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]，[[concepts/ReleaseGateDebtBypassDetection边界]]，[[concepts/EvalPortfolioMetricHierarchy边界]]，[[concepts/MetricConflictResolution边界]]，[[concepts/EvalResultInterpretationDecisionThreshold边界]]，[[concepts/MonitorOwnershipEscalationLadder边界]]，[[concepts/AISafetyOpsGovernance边界]]，[[sources/nist-sp800-55-measurement-guide-2024]]，[[sources/nist-sp800-137-continuous-monitoring-2011]]，[[sources/nist-ai-rmf-playbook-monitoring-responsibility-2026]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Dashboard calibration / governance metric quality 主属第 7 层，是治理看板指标进入 release、review、freeze、rollback、deny renewal 或 backlog 前的测量质量边界；它要求 decision inventory、metric definition sheet、lineage/freshness/coverage、outcome calibration、false/missed action review 和 retire/quarantine 规则。
- Address range: c-000560 至 c-000566

## 2026-05-30 research | Release gate debt gate bypass detection 边界
- Topic: 第 7 层如何发现 release gate 被 admin bypass、shadow approval、direct-to-prod、stale exception、unprotected environment 或 gate config drift 稀释。
- Synthesis: [[Research: Release gate debt gate bypass detection 边界]]
- Pages created: [[concepts/ReleaseGateDebtBypassDetection边界]]，[[Research: Release gate debt gate bypass detection 边界]]，[[sources/github-actions-deployment-protection-rules-2026]]，[[sources/github-actions-reviewing-deployments-admin-bypass-2026]]，[[sources/gitlab-protected-environments-deployment-approvals-2026]]，[[sources/gitlab-deployment-safety-2026]]，[[sources/google-cloud-deploy-approvals-policies-audit-2026]]，[[sources/nist-sp800-53-cm3-cm5-change-control-2025]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/OverrideGovernanceResidualRiskAcceptance边界]]，[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]，[[concepts/AISafetyOpsGovernance边界]]，[[concepts/MonitorOwnershipEscalationLadder边界]]，[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]，[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]，[[concepts/EvidenceAttestationSignedEvalArtifact边界]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Release gate debt / gate bypass detection 主属第 7 层，是证明真实生产变更经过 release gate、protected environment、approval、attestation 或 structured exception 的治理健康边界；它把隐藏绕过转成 gate debt ledger 和可关闭行动。
- Address range: c-000552 至 c-000559

## 2026-05-30 research | Evidence minimization privacy preserving audit packet 边界
- Topic: 第 7 层如何在 release/eval/safety/incident/override audit packet 中同时满足可审计、可重验和少留少披露敏感数据。
- Synthesis: [[Research: Evidence minimization privacy preserving audit packet 边界]]
- Pages created: [[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]，[[Research: Evidence minimization privacy preserving audit packet 边界]]，[[sources/eu-gdpr-article-5-data-minimization-storage-accountability-2016]]，[[sources/nist-privacy-framework-data-minimization-audit-log-2020]]，[[sources/nist-sp800-53-au3-pii-audit-record-minimization-2025]]，[[sources/ietf-rfc9901-sd-jwt-selective-disclosure-2025]]，[[sources/w3c-vc-bbs-selective-disclosure-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]，[[concepts/DataRightsPrivacyConsent边界]]，[[concepts/DataDeletionUnlearningImpact边界]]，[[concepts/EvidenceAttestationSignedEvalArtifact边界]]，[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]，[[sources/gdpr-data-subject-rights-2016]]，[[sources/nist-sp800-53-au11-audit-record-retention-2025]]，[[sources/nist-sp800-92r1-log-management-2023]]，[[sources/slsa-source-requirements-evidence-expunging-2026]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Evidence minimization / privacy-preserving audit packet 主属第 7 层，是把 audit claim、最小充分证据、字段级 minimization matrix、private annex、selective-disclosure proof 和 tombstone/disposition record 组合成隐私化证据治理边界。
- Address range: c-000545 至 c-000551

## 2026-05-30 research | Cross-verifier policy drift conformance test 边界
- Topic: 第 6 层如何检测 CI、release gate、admission controller、本地 verifier、runtime guard 和第三方 verifier 是否执行同一 policy/root 语义。
- Synthesis: [[Research: Cross-verifier policy drift conformance test 边界]]
- Pages created: [[concepts/CrossVerifierPolicyDriftConformanceTest边界]]，[[Research: Cross-verifier policy drift conformance test 边界]]，[[sources/sigstore-cosign-attestation-policy-cue-rego-2026]]，[[sources/open-policy-agent-policy-testing-2026]]，[[sources/open-policy-agent-gatekeeper-gator-verify-2026]]，[[sources/kyverno-policy-testing-ci-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/VerifierPolicyTrustRootRotation边界]]，[[concepts/EvidenceAttestationSignedEvalArtifact边界]]，[[concepts/ProductionContractCompatibilityTest边界]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/MultiProviderGovernance边界]]，[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]，[[concepts/MonitorOwnershipEscalationLadder边界]]，[[sources/sigstore-policy-controller-2026]]，[[sources/slsa-verification-summary-attestation-v1-2-2026]]，[[sources/in-toto-verify-2026]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Cross-verifier policy drift / conformance test 主属第 6 层，是用 canonical policy、trust root 和 golden corpus 比较 local CLI、CI、release gate、admission controller、runtime guard 和 delegated verifier 是否产生一致 allow/deny/reason 的策略一致性边界。
- Address range: c-000539 至 c-000544

## 2026-05-30 research | Override debt exception analytics dashboard 边界
- Topic: 第 7 层如何把 override rate、expired exception、renewal、repeat owner、risk exposure、monitor coverage 和 residual-risk incident conversion 变成治理反馈。
- Synthesis: [[Research: Override debt exception analytics dashboard 边界]]
- Pages created: [[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]，[[Research: Override debt exception analytics dashboard 边界]]，[[sources/nist-sp800-55-measurement-guide-2024]]，[[sources/nist-sp800-137-continuous-monitoring-2011]]，[[sources/google-sre-good-housekeeping-error-budget-debt-2018]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/OverrideGovernanceResidualRiskAcceptance边界]]，[[concepts/MetricConflictResolution边界]]，[[concepts/IntolerableRiskThresholdStopRule边界]]，[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/AISafetyOpsGovernance边界]]，[[concepts/MonitorOwnershipEscalationLadder边界]]，[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]，[[sources/google-sre-error-budget-policy-2018]]，[[sources/nist-sp800-37-risk-response-2018]]，[[sources/nist-ai-rmf-playbook-monitoring-responsibility-2026]]，[[sources/openai-preparedness-framework-2025]]，[[sources/microsoft-responsible-ai-standard-2022]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Override debt / exception analytics dashboard 主属第 7 层，是把单条例外和 residual risk acceptance 聚合成治理健康信号的边界；它要求 normalized override record、risk-weighted exposure、过期/续期/重复 owner、monitor coverage、hard-stop near miss、incident conversion 和 action backlog。
- Address range: c-000534 至 c-000538

## 2026-05-30 research | Evidence retention audit packet lifecycle 边界
- Topic: 第 6/7 层如何保留、压缩、检索、重验、legal hold 和销毁 release/eval/safety/incident/override evidence 包。
- Synthesis: [[Research: Evidence retention audit packet lifecycle 边界]]
- Pages created: [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]，[[Research: Evidence retention audit packet lifecycle 边界]]，[[sources/nist-sp800-53-au11-audit-record-retention-2025]]，[[sources/nist-sp800-92r1-log-management-2023]]，[[sources/nara-general-records-schedules-2025]]，[[sources/iso-15489-records-management-2016]]，[[sources/in-toto-archivista-2026]]，[[sources/slsa-source-requirements-evidence-expunging-2026]]，[[sources/slsa-verifier-provenance-bundle-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/EvidenceAttestationSignedEvalArtifact边界]]，[[concepts/EvidenceFreshnessStaleProof边界]]，[[concepts/VerifierPolicyTrustRootRotation边界]]，[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]，[[concepts/SafetyCaseAssuranceCase边界]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/AIIncidentResponsePostmortem边界]]，[[concepts/DataDeletionUnlearningImpact边界]]，[[concepts/OverrideGovernanceResidualRiskAcceptance边界]]，[[concepts/AISafetyOpsGovernance边界]]，[[concepts/MultiProviderGovernance边界]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Evidence retention / audit packet lifecycle 主属第 7 层，是第 6 层可信证据进入组织审计、事故、监管、复盘和长期学习前的记录治理边界；它要求 evidence manifest、retention class、storage tier、retrieval index、reverification hook、legal hold 和 disposition record。
- Address range: c-000525 至 c-000533

## 2026-05-30 research | Verifier policy trust root rotation 边界
- Topic: 第 6/7 层如何维护 attestation verifier policy、trust root、签名身份轮换、client compatibility、revocation 和 re-verification。
- Synthesis: [[Research: Verifier policy trust root rotation 边界]]
- Pages created: [[concepts/VerifierPolicyTrustRootRotation边界]]，[[Research: Verifier policy trust root rotation 边界]]，[[sources/slsa-verification-summary-attestation-v1-2-2026]]，[[sources/sigstore-cosign-custom-components-trust-root-2026]]，[[sources/sigstore-keyless-root-of-trust-2026]]，[[sources/sigstore-tuf-root-update-2024]]，[[sources/tuf-root-metadata-api-2021]]，[[sources/in-toto-verify-2026]]，[[sources/sigstore-policy-controller-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/EvidenceAttestationSignedEvalArtifact边界]]，[[concepts/EvidenceFreshnessStaleProof边界]]，[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/MultiProviderGovernance边界]]，[[concepts/OverrideGovernanceResidualRiskAcceptance边界]]，[[sources/slsa-verifying-artifacts-v1-2-2026]]，[[sources/sigstore-cosign-verifying-attestations-2026]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Verifier policy / trust root rotation 主属第 6 层，是 signed evidence 进入第 7 层 release gate、release card、safety case 和 provider governance 前的证据验收策略边界；它要求 expected identity、predicate、policy version、trust root、rotation、revocation 和 re-verification。
- Address range: c-000516 至 c-000524

## 2026-05-30 research | Override governance residual risk acceptance 边界
- Topic: 第 7 层如何防止 exception、override 和 residual risk acceptance 变成绕过 eval、release card、stop rule、safety case 和 release gate 的常态。
- Synthesis: [[Research: Override governance residual risk acceptance 边界]]
- Pages created: [[concepts/OverrideGovernanceResidualRiskAcceptance边界]]，[[Research: Override governance residual risk acceptance 边界]]，[[sources/nist-sp800-37-risk-response-2018]]，[[sources/nist-sp800-30-risk-assessment-2012]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/IntolerableRiskThresholdStopRule边界]]，[[concepts/MetricConflictResolution边界]]，[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]，[[concepts/SafetyCaseAssuranceCase边界]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/AISafetyOpsGovernance边界]]，[[concepts/MonitorOwnershipEscalationLadder边界]]，[[concepts/AIIncidentResponsePostmortem边界]]，[[sources/nist-ai-rmf-risk-tolerance-2023]]，[[sources/openai-preparedness-framework-2025]]，[[sources/microsoft-responsible-ai-standard-2022]]，[[sources/google-sre-error-budget-policy-2018]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Override governance / residual risk acceptance 主属第 7 层，是第 6 层证据不足、冲突、灰区或 stale 时进入组织决策的受控例外边界；它要求 hard-stop check、残余风险记录、approval authority、expiry、monitor、rollback 和复审，防止 exception 吞掉质量门。
- Address range: c-000512 至 c-000515

## 2026-05-30 research | Monitor tabletop runbook drill 边界
- Topic: 第 7 层如何演练 monitor owner、on-call、incident command、release gate、risk owner、provider POC 和 comms/legal/support 的交接，避免监控和 runbook 停在文档里。
- Synthesis: [[Research: Monitor tabletop runbook drill 边界]]
- Pages created: [[concepts/MonitorTabletopRunbookDrill边界]]，[[Research: Monitor tabletop runbook drill 边界]]，[[sources/google-sre-incident-management-guide-2026]]，[[sources/nist-sp800-84-tte-program-2006]]，[[sources/ncsc-effective-steps-cyber-exercise-creation-2026]]，[[sources/aws-security-ir-simulations-2026]]，[[sources/cisa-ai-cyber-tabletop-exercise-series-2025]]，[[sources/fema-hseep-exercise-evaluation-2020]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/MonitorOwnershipEscalationLadder边界]]，[[concepts/AIIncidentResponsePostmortem边界]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/AISafetyOpsGovernance边界]]，[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]，[[concepts/EvidenceFreshnessStaleProof边界]]，[[concepts/MetricConflictResolution边界]]，[[sources/microsoft-ai-incident-response-readiness-2026]]，[[sources/google-sre-managing-incidents-2016]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Monitor tabletop / runbook drill 主属第 7 层，是把第 6 层 monitor/eval/freshness/release-card/provider 信号转成场景、injects、role handoff、decision/action、after-action report 和 improvement plan 的组织演练验证边界。
- Address range: c-000504 至 c-000511

## 2026-05-30 research | Evidence attestation signed eval artifact 边界
- Topic: 第 6/7 层如何证明 eval artifact、模型版本、prompt、judge、dataset、container、release card 和来源声明没有被替换、篡改或错误绑定。
- Synthesis: [[Research: Evidence attestation signed eval artifact 边界]]
- Pages created: [[concepts/EvidenceAttestationSignedEvalArtifact边界]]，[[Research: Evidence attestation signed eval artifact 边界]]，[[sources/slsa-provenance-v1-2-2026]]，[[sources/slsa-verifying-artifacts-v1-2-2026]]，[[sources/in-toto-test-result-predicate-2026]]，[[sources/sigstore-cosign-verifying-attestations-2026]]，[[sources/openssf-model-signing-2026]]，[[sources/nist-ssdf-sp800-218-2022]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/DatasetLineageProvenanceGraph边界]]，[[concepts/EvidenceFreshnessStaleProof边界]]，[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]，[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]，[[concepts/ProductionContractCompatibilityTest边界]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/SafetyCaseAssuranceCase边界]]，[[concepts/MultiProviderGovernance边界]]，[[sources/attesting-llm-pipelines-release-claims-2026]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Evidence attestation / signed eval artifact 主属第 6 层，是 eval、model、prompt、judge、dataset、container 和 release evidence 进入第 7 层 release gate、release card 和 safety case 前的证据完整性边界；它要求 subject digest、signed bundle、producer identity、trust root、verifier policy 和 verification summary。
- Address range: c-000496 至 c-000503

## 2026-05-30 research | Metric conflict resolution 边界
- Topic: 第 6/7 层如何在 hard stop、guardrail、primary、slice、online、SLO、business metric 和 cost/latency 冲突时形成优先级、升级和行动。
- Synthesis: [[Research: Metric conflict resolution 边界]]
- Pages created: [[concepts/MetricConflictResolution边界]]，[[Research: Metric conflict resolution 边界]]，[[sources/google-sre-embracing-risk-2016]]，[[sources/google-sre-canarying-releases-2018]]，[[sources/responsible-ai-tensions-tradeoffs-2023]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/EvalPortfolioMetricHierarchy边界]]，[[concepts/EvalResultInterpretationDecisionThreshold边界]]，[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]，[[concepts/IntolerableRiskThresholdStopRule边界]]，[[concepts/OfflineOnlineEvalCorrelation边界]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/MonitorOwnershipEscalationLadder边界]]，[[concepts/RewardHackingEvalOverfitting边界]]，[[sources/google-sre-error-budget-policy-2018]]，[[sources/nist-ai-rmf-risk-tolerance-2023]]，[[sources/openai-evals-business-framework-2025]]，[[sources/openai-preparedness-framework-2025]]，[[sources/microsoft-responsible-ai-standard-2022]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Metric conflict resolution 主属第 6 层，是 hard stop、guardrail、primary、slice、online、SLO 和 business metric 冲突时的证据优先级与升级规则；它防止一个总分掩盖风险和关键 slice 退化。
- Address range: c-000491 至 c-000495

## 2026-05-30 research | Monitor ownership escalation ladder 边界
- Topic: 第 6/7 层如何把 monitor、eval breach、stale evidence、release-card watch item 和 user report 分派给 owner、SLA、incident、release gate 或 risk elevation。
- Synthesis: [[Research: Monitor ownership escalation ladder 边界]]
- Pages created: [[concepts/MonitorOwnershipEscalationLadder边界]]，[[Research: Monitor ownership escalation ladder 边界]]，[[sources/nist-ai-rmf-playbook-monitoring-responsibility-2026]]，[[sources/nist-sp800-61r3-incident-response-2025]]，[[sources/google-sre-being-on-call-2016]]，[[sources/google-sre-managing-incidents-2016]]，[[sources/microsoft-ai-incident-response-readiness-2026]]，[[sources/openai-frontier-governance-framework-2026]]，[[sources/ai-incident-escalation-criteria-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/EvidenceFreshnessStaleProof边界]]，[[concepts/PostReleaseEvalDrift边界]]，[[concepts/EvalPortfolioMetricHierarchy边界]]，[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/AIIncidentResponsePostmortem边界]]，[[concepts/AISafetyOpsGovernance边界]]，[[concepts/IntolerableRiskThresholdStopRule边界]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Monitor ownership / escalation ladder 主属第 7 层，是把第 6 层 monitor、eval breach、stale evidence 和 user report 接到 owner、SLA、incident、release gate 或 risk elevation 的责任链边界。
- Address range: c-000482 至 c-000490

## 2026-05-30 research | Evidence freshness stale proof 边界
- Topic: 第 6/7 层如何判断 eval、release card、safety case、monitor、judge、benchmark 和 production outcome 证据是否仍 fresh，什么时候 stale、expired、superseded、invalidated 或 unknown。
- Synthesis: [[Research: Evidence freshness stale proof 边界]]
- Pages created: [[concepts/EvidenceFreshnessStaleProof边界]]，[[Research: Evidence freshness stale proof 边界]]，[[sources/safety-case-maintenance-slr-2021]]，[[sources/dynamic-safety-cases-changing-world-2025]]，[[sources/runtime-confidence-safety-arguments-2026]]，[[sources/cmu-sei-drift-monitoring-ml-systems-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/PostReleaseEvalDrift边界]]，[[concepts/EvalPortfolioMetricHierarchy边界]]，[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]，[[concepts/SafetyCaseAssuranceCase边界]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]，[[concepts/DatasetLineageProvenanceGraph边界]]，[[sources/nist-deployed-ai-monitoring-challenges-2026]]，[[sources/openai-evaluation-best-practices-2026]]，[[sources/google-ml-test-score-2016]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Evidence freshness / stale proof 主属第 6 层，是 eval、release card、safety case、monitor、judge 和 benchmark 证据进入第 7 层决策前的有效期边界；它要求每份证据带 claim、scope、依赖、失效触发器和 refresh action。
- Address range: c-000476 至 c-000481

## 2026-05-30 research | Eval portfolio metric hierarchy 边界
- Topic: 第 6 层如何把 benchmark、private hold-out、regression、production contract、red-team、LLM judge、人类评审、online eval、business metric 和 SLO 组织成分层证据组合。
- Synthesis: [[Research: Eval portfolio metric hierarchy 边界]]
- Pages created: [[concepts/EvalPortfolioMetricHierarchy边界]]，[[Research: Eval portfolio metric hierarchy 边界]]，[[sources/openai-simple-evals-2026]]，[[sources/google-ml-test-score-2016]]，[[sources/openai-evals-business-framework-2025]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]，[[concepts/EvalResultInterpretationDecisionThreshold边界]]，[[concepts/RewardHackingEvalOverfitting边界]]，[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/PostReleaseEvalDrift边界]]，[[sources/openai-evaluation-best-practices-2026]]，[[sources/openai-evals-framework-2026]]，[[sources/helm-holistic-evaluation-2022]]，[[sources/openai-trustworthy-third-party-evaluations-2026]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Eval portfolio / metric hierarchy 主属第 6 层，是把多种 eval 和指标组织成 hard stop、guardrail、primary、slice、online、diagnostic 的分层证据组合；它避免用一个总分掩盖风险。
- Address range: c-000471 至 c-000475

## 2026-05-30 research | Post-release eval drift 边界
- Topic: 第 6/7 层如何在发布后监控 release card、threshold、offline/online correlation、judge、RAG/tool/provider 和 safety evidence 是否因生产变化而 stale。
- Synthesis: [[Research: Post-release eval drift 边界]]
- Pages created: [[concepts/PostReleaseEvalDrift边界]]，[[Research: Post-release eval drift 边界]]，[[sources/nist-deployed-ai-monitoring-challenges-2026]]，[[sources/aws-prescriptive-genai-production-monitoring-2026]]，[[sources/aws-prescriptive-genai-drift-detection-2026]]，[[sources/google-cloud-genai-monitoring-2024]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/OfflineOnlineEvalCorrelation边界]]，[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]，[[concepts/SafetyCaseAssuranceCase边界]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/JudgeDriftGraderObservability边界]]，[[concepts/AIIncidentResponsePostmortem边界]]，[[concepts/DataFlywheelFeedbackLoop边界]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Post-release eval drift 主属第 6 层，是 release card、offline/online correlation、production monitoring 和 safety case 之间的发布后证据保鲜边界；它不新增运维顶层。
- Address range: c-000465 至 c-000470

## 2026-05-30 research | Safety case assurance case 边界
- Topic: 第 6/7 层如何把 eval、red-team、release card、online monitor、safeguard evidence 和 residual risk 组织成高风险 AI 系统的 claims-arguments-evidence 发布论证。
- Synthesis: [[Research: Safety case assurance case 边界]]
- Pages created: [[concepts/SafetyCaseAssuranceCase边界]]，[[Research: Safety case assurance case 边界]]，[[sources/safety-cases-advanced-ai-systems-2024]]，[[sources/aisi-frontier-ai-safety-case-cyber-2024]]，[[sources/big-argument-ai-safety-cases-2025]]，[[sources/structured-safety-case-ai-systems-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/AISafetyOpsGovernance边界]]，[[concepts/IntolerableRiskThresholdStopRule边界]]，[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Safety case / assurance case 主属第 7 层，是高风险 AI 系统把第 6 层多源证据组织成可审查发布论证和残余风险接受包的治理边界；它不新增安全顶层。
- Address range: c-000459 至 c-000464

## 2026-05-30 research | Offline online eval correlation 边界
- Topic: 第 6/7 层如何验证离线 eval、LLM judge、release card 和真实生产 outcome 是否同向，并用线上结果校准 eval trust tier、threshold、dataset 和 release gate。
- Synthesis: [[Research: Offline online eval correlation 边界]]
- Pages created: [[concepts/OfflineOnlineEvalCorrelation边界]]，[[Research: Offline online eval correlation 边界]]，[[sources/offline-metrics-predict-online-recsys-2020]]，[[sources/offline-ab-testing-recommender-systems-2018]]，[[sources/amazon-offline-online-product-ranking-2023]]，[[sources/langsmith-evaluation-types-2026]]，[[sources/langchain-production-monitoring-regression-tests-2026]]，[[sources/evaluation-driven-development-operations-llm-agents-2025]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]，[[concepts/EvalResultInterpretationDecisionThreshold边界]]，[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/DataFlywheelFeedbackLoop边界]]，[[sources/openai-evaluation-best-practices-2026]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Offline / online eval correlation 主属第 6 层，是离线 eval、release card 和线上 production outcome 之间的预测有效性边界；它决定哪类离线证据仍能被第 7 层 release gate 信任。
- Address range: c-000451 至 c-000458

## 2026-05-30 research | Eval uncertainty communication release card 边界
- Topic: 第 6/7 层如何把 eval 分数、置信区间、方差、slice 风险、judge health、coverage gap、hard stop、例外和后续监控，整理成决策者能消费的 release / eval card。
- Synthesis: [[Research: Eval uncertainty communication release card 边界]]
- Pages created: [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]，[[Research: Eval uncertainty communication release card 边界]]，[[sources/nist-ai-evaluation-statistical-models-2026]]，[[sources/adding-error-bars-evals-2024]]，[[sources/model-cards-for-model-reporting-2019]]，[[sources/riskcards-language-model-deployment-2023]]，[[sources/sphere-evaluation-card-2025]]，[[sources/google-model-card-toolkit-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/EvalResultInterpretationDecisionThreshold边界]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/JudgeDriftGraderObservability边界]]，[[concepts/IntolerableRiskThresholdStopRule边界]]，[[sources/openai-gpt-4o-system-card-2024]]，[[sources/openai-trustworthy-third-party-evaluations-2026]]，[[sources/betterbench-benchmark-quality-2024]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Eval uncertainty communication / release card 主属第 6 层，是 eval evidence 进入第 7 层 release、rollback、safety governance 和组织 owner 前的证据表达边界；它把不确定性、灰区、局限、hard stop 和 post-release monitor 转成可审查的决策材料。
- Address range: c-000443 至 c-000450

## 2026-05-30 research | Intolerable risk threshold stop rule 边界
- Topic: 第 6/7 层如何把高风险能力阈值、法律禁止、safeguard 不足、severe incident 和 residual risk 证据转成 no-go、pause、restrict、rollback、external review 或 required safeguards。
- Synthesis: [[Research: Intolerable risk threshold stop rule 边界]]
- Pages created: [[concepts/IntolerableRiskThresholdStopRule边界]]，[[Research: Intolerable risk threshold stop rule 边界]]，[[sources/nist-ai-rmf-risk-tolerance-2023]]，[[sources/eu-ai-act-prohibited-practices-2024]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/AISafetyOpsGovernance边界]]，[[concepts/EvalResultInterpretationDecisionThreshold边界]]，[[concepts/ModelReleaseRollbackGate边界]]，[[sources/nist-ai-rmf-1-0-2023]]，[[sources/openai-preparedness-framework-2025]]，[[sources/anthropic-responsible-scaling-policy-v3-2026]]，[[sources/deepmind-frontier-safety-framework-2025]]，[[sources/iso-iec-42001-ai-management-system-2023]]，[[sources/microsoft-responsible-ai-standard-2022]]，[[sources/eu-ai-act-risk-management-post-market-2024]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Intolerable risk threshold / stop rule 主属第 7 层，是第 6 层风险证据进入组织 no-go、pause、restrict、rollback 和 external review 的 hard stop 边界；它保证某些风险不能被平均分、商业收益或灰区例外稀释。
- Address range: c-000439 至 c-000442

## 2026-05-30 research | Judge drift grader observability 边界
- Topic: 第 6 层如何持续监控 LLM judge、rubric grader、AI annotator 和 judge panel 的 human agreement、score distribution、bias、prompt sensitivity 与 production correlation，防止评分器漂移污染 release、training 和 self-improvement 决策。
- Synthesis: [[Research: Judge drift grader observability 边界]]
- Pages created: [[concepts/JudgeDriftGraderObservability边界]]，[[Research: Judge drift grader observability 边界]]，[[sources/judge-verdict-human-agreement-2025]]，[[sources/closer-look-automatic-evaluation-llms-2023]]，[[sources/empirical-finetuned-judge-not-general-substitute-2025]]，[[sources/langsmith-llm-judge-human-feedback-online-evals-2026]]，[[sources/phoenix-llm-evaluators-observability-2026]]，[[sources/human-anchored-longitudinal-llm-judge-2026]]，[[sources/galileo-continuous-llm-judge-calibration-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/LLMJudgeAIFeedbackCalibration边界]]，[[concepts/EvalResultInterpretationDecisionThreshold边界]]，[[concepts/ProductionContractCompatibilityTest边界]]，[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]，[[sources/openai-graders-docs-2026]]，[[sources/mt-bench-chatbot-arena-llm-as-judge-2023]]，[[sources/llm-judge-position-bias-2024]]，[[sources/llm-judges-alignment-vulnerabilities-2024]]，[[sources/poll-panel-llm-evaluators-2024]]，[[sources/llm-evaluators-self-preference-2024]]，[[sources/alternative-annotator-test-2025]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Judge drift / grader observability 主属第 6 层，是 LLM judge 和 grader stack 的持续健康监控边界；它位于 judge calibration 之后、decision threshold 之前，先判断“评分器是否还可信”，再允许分数进入 release gate、training feedback 或 self-improvement。
- Address range: c-000430 至 c-000438

## 2026-05-30 research | Production contract compatibility test 边界
- Topic: 第 6/7 层如何把产品行为、schema、工具、安全、数据处理、SLO 和供应链声明写成模型/provider 更新前的 compatibility suite 和 release gate 证据。
- Synthesis: [[Research: Production contract compatibility test 边界]]
- Pages created: [[concepts/ProductionContractCompatibilityTest边界]]，[[Research: Production contract compatibility test 边界]]，[[sources/attesting-llm-pipelines-release-claims-2026]]，[[sources/together-ai-deprecations-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/ModelReleaseRollbackGate边界]]，[[concepts/EvalResultInterpretationDecisionThreshold边界]]，[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]，[[concepts/MultiProviderGovernance边界]]，[[sources/test-before-you-deploy-llm-supply-chain-2026]]，[[sources/openai-model-deprecations-2026]]，[[sources/openai-model-release-notes-2026]]，[[sources/anthropic-model-deprecations-2026]]，[[sources/google-cloud-deploy-automation-2026]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Production contract / compatibility test 主属第 6 层，是模型和供应链更新进入第 7 层 release/rollback gate 前的可测试产品契约；它防止“新模型总体更强”掩盖产品关键行为不兼容。
- Address range: c-000426 至 c-000429

## 2026-05-30 research | Eval result interpretation decision threshold 边界
- Topic: 第 6/7 层如何把 eval score、置信区间、方差、guardrail、slice、SLO 和风险容忍度转成发布、回滚、灰区调查、canary 或人工复核决策。
- Synthesis: [[Research: Eval result interpretation decision threshold 边界]]
- Pages created: [[concepts/EvalResultInterpretationDecisionThreshold边界]]，[[Research: Eval result interpretation decision threshold 边界]]，[[sources/openai-trustworthy-third-party-evaluations-2026]]，[[sources/google-sre-service-level-objectives-2016]]，[[sources/google-sre-error-budget-policy-2018]]，[[sources/kohavi-controlled-experiments-web-2009]]，[[sources/chatbot-arena-human-preference-2024]]，[[sources/anytime-valid-confidence-sequences-ab-testing-2023]]，[[sources/betterbench-benchmark-quality-2024]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]，[[concepts/LLMJudgeAIFeedbackCalibration边界]]，[[concepts/ModelReleaseRollbackGate边界]]，[[sources/openai-evaluation-best-practices-2026]]，[[sources/anthropic-demystifying-evals-agents-2026-05-26]]，[[sources/nist-ai-rmf-1-0-2023]]，[[sources/google-mlops-continuous-delivery-2026]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Eval result interpretation / decision threshold 主属第 6 层，是 eval 分数进入 release gate、routing、training、rollback 和 self-improvement 前的证据解释边界；它把“模型得了多少分”变成“现在该做什么”。
- Address range: c-000417 至 c-000425

## 2026-05-30 research | LLM-as-judge AI feedback calibration 边界
- Topic: 第 6/2/7/8 层如何校准 LLM judge、AI 标注、RLAIF teacher、rubric grader 和 multi-judge panel，使其能作为 eval、training、release 或 self-improvement 证据。
- Synthesis: [[Research: LLM-as-judge AI feedback calibration 边界]]
- Pages created: [[concepts/LLMJudgeAIFeedbackCalibration边界]]，[[Research: LLM-as-judge AI feedback calibration 边界]]，[[sources/g-eval-2023]]，[[sources/mt-bench-chatbot-arena-llm-as-judge-2023]]，[[sources/llm-judge-position-bias-2024]]，[[sources/llm-judges-alignment-vulnerabilities-2024]]，[[sources/poll-panel-llm-evaluators-2024]]，[[sources/llm-evaluators-self-preference-2024]]，[[sources/alternative-annotator-test-2025]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/ReasoningEvalVerifier边界]]，[[concepts/HumanFeedbackAnnotationOps边界]]，[[concepts/SyntheticDataGovernance边界]]，[[concepts/RewardHackingEvalOverfitting边界]]，[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]，[[sources/openai-graders-docs-2026]]，[[sources/anthropic-demystifying-evals-agents-2026-05-26]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: LLM-as-judge / AI feedback calibration 主属第 6 层，是自动评分和 AI 标注进入 eval、RLAIF、reward、release gate 与 self-improvement 前的校准边界；AI 评 AI 必须有 human gold、bias suite、lineage、hold-out 和 downstream validation。
- Address range: c-000408 至 c-000416

## 2026-05-30 research | Model release rollback gate 边界
- Topic: 第 6/7 层如何把模型、prompt、router、skill、tool、provider 和 policy 变更纳入发布、灰度、回滚、迁移和 audit gate。
- Synthesis: [[Research: Model release rollback gate 边界]]
- Pages created: [[concepts/ModelReleaseRollbackGate边界]]，[[Research: Model release rollback gate 边界]]，[[sources/openai-sycophancy-gpt4o-rollback-2025]]，[[sources/openai-model-deprecations-2026]]，[[sources/openai-model-release-notes-2026]]，[[sources/anthropic-model-deprecations-2026]]，[[sources/google-cloud-deploy-automation-2026]]，[[sources/test-before-you-deploy-llm-supply-chain-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]，[[concepts/AISafetyOpsGovernance边界]]，[[concepts/AIIncidentResponsePostmortem边界]]，[[concepts/MultiProviderGovernance边界]]，[[concepts/ModelRoutingMixture边界]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Model release / rollback gate 主属第 7 层，是 AI 变更进入真实产品流量的组织执行边界；它消费第 6 层 eval 和 monitoring，约束第 2/3/4/5 层 artifact 的上线、灰度、回滚和迁移。
- Address range: c-000400 至 c-000407

## 2026-05-30 research | Evaluation dataset lifecycle benchmark governance 边界
- Topic: 第 6/7 层如何治理 eval set、private hold-out、public benchmark、regression suite、red-team set 的 split、版本、泄漏、饱和、刷新、退役和 release gate 绑定。
- Synthesis: [[Research: Evaluation dataset lifecycle benchmark governance 边界]]
- Pages created: [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]，[[Research: Evaluation dataset lifecycle benchmark governance 边界]]，[[sources/openai-evaluation-best-practices-2026]]，[[sources/openai-evals-framework-2026]]，[[sources/helm-holistic-evaluation-2022]]，[[sources/dynabench-2021]]，[[sources/livebench-2024]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/RewardHackingEvalOverfitting边界]]，[[concepts/DataQualityLabelQuality边界]]，[[concepts/DatasetLineageProvenanceGraph边界]]，[[concepts/HumanFeedbackAnnotationOps边界]]，[[concepts/AISafetyOpsGovernance边界]]，[[sources/benchmarking-benchmark-leakage-2024]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Evaluation dataset lifecycle / benchmark governance 主属第 6 层，是 eval 数据集作为质量门资产的生命周期治理；它防止 eval 泄漏、饱和、漂移和被反复优化后失真。
- Address range: c-000393 至 c-000399

## 2026-05-30 research | Human feedback annotation ops 边界
- Topic: 第 6/7/2 层如何把人类示范、偏好、纠错、gold label 和 expert review 变成 eval、reward model、SFT/RLHF、RAG/memory/skill 或产品证据。
- Synthesis: [[Research: Human feedback annotation ops 边界]]
- Pages created: [[concepts/HumanFeedbackAnnotationOps边界]]，[[Research: Human feedback annotation ops 边界]]，[[sources/deep-rl-from-human-preferences-2017]]，[[sources/learning-to-summarize-human-feedback-2020]]，[[sources/anthropic-hh-rlhf-2022]]，[[sources/label-studio-annotation-quality-2026]]，[[sources/labelbox-quality-analysis-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/DataQualityLabelQuality边界]]，[[concepts/DataFlywheelFeedbackLoop边界]]，[[concepts/RewardHackingEvalOverfitting边界]]，[[concepts/DatasetLineageProvenanceGraph边界]]，[[concepts/SyntheticDataGovernance边界]]，[[sources/instructgpt-rlhf-2022]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Human feedback / annotation ops 主属第 6 层，是把人类判断变成可靠 eval、preference、reward、training 和产品证据的质量系统；人类反馈需要 spec、pilot、rubric、calibration、QA、adjudication、lineage 和 downstream validation。
- Address range: c-000386 至 c-000392

## 2026-05-30 research | Data deletion unlearning impact 边界
- Topic: 第 7/6/2 层如何把删除/撤回/保留到期/事故请求落实到 logs、RAG、memory、eval、training、model weights、provider 和 audit。
- Synthesis: [[Research: Data deletion unlearning impact 边界]]
- Pages created: [[concepts/DataDeletionUnlearningImpact边界]]，[[Research: Data deletion unlearning impact 边界]]，[[sources/machine-unlearning-sisa-2019]]，[[sources/google-machine-unlearning-challenge-2023]]，[[sources/machine-unlearning-comprehensive-survey-2024]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/DataRightsPrivacyConsent边界]]，[[concepts/DatasetLineageProvenanceGraph边界]]，[[concepts/DataQualityLabelQuality边界]]，[[concepts/SyntheticDataGovernance边界]]，[[concepts/DataFlywheelFeedbackLoop边界]]，[[concepts/AIIncidentResponsePostmortem边界]]，[[sources/gdpr-data-subject-rights-2016]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Data deletion / unlearning impact 主属第 7 层，是 data rights 请求进入真实 AI 系统后的执行闭环；它依赖第 6 层 lineage/eval 定位和验证影响，在必要时调用第 2 层 retraining、model replacement 或 machine unlearning。
- Address range: c-000381 至 c-000385

## 2026-05-30 research | Dataset lineage provenance graph 边界
- Topic: 第 6 层如何追踪样本、trace、eval、training、RAG、memory、skill、synthetic data 和模型版本之间的来源、转换、污染、删除和回滚影响。
- Synthesis: [[Research: Dataset lineage provenance graph 边界]]
- Pages created: [[concepts/DatasetLineageProvenanceGraph边界]]，[[Research: Dataset lineage provenance graph 边界]]，[[sources/w3c-prov-overview-2013]]，[[sources/tensorflow-ml-metadata-2026]]，[[sources/openlineage-spec-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/DataQualityLabelQuality边界]]，[[concepts/SyntheticDataGovernance边界]]，[[concepts/DataRightsPrivacyConsent边界]]，[[concepts/DataFlywheelFeedbackLoop边界]]，[[concepts/AIIncidentResponsePostmortem边界]]，[[sources/eu-ai-act-data-governance-2024]]，[[sources/nist-genai-profile-data-privacy-2024]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Dataset lineage / provenance graph 主属第 6 层，是训练、eval、RAG、memory、skill、synthetic data、incident response 和 self-improvement 之间的证据血缘底座；它让污染检测、删除影响、事故取证、rollback 和审计成为可查询系统能力。
- Address range: c-000376 至 c-000380

## 2026-05-30 research | Synthetic data governance 边界
- Topic: 第 2/6/7/8 层如何判断合成数据能否进入训练、eval、RAG、memory、skill、router 或自我改进。
- Synthesis: [[Research: Synthetic data governance 边界]]
- Pages created: [[concepts/SyntheticDataGovernance边界]]，[[Research: Synthetic data governance 边界]]，[[sources/model-collapse-nature-2024]]，[[sources/is-model-collapse-inevitable-2024]]，[[sources/self-instruct-2022]]，[[sources/anthropic-constitutional-ai-rlaif-2022]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/DataQualityLabelQuality边界]]，[[concepts/DataRightsPrivacyConsent边界]]，[[concepts/DataFlywheelFeedbackLoop边界]]，[[concepts/RewardHackingEvalOverfitting边界]]，[[concepts/Dream与SelfImprovement工程原语]]，[[sources/openai-model-distillation-2024]]，[[sources/openai-fine-tuning-data-quality-2026]]，[[sources/data-cards-2022]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Synthetic data governance 主属第 6 层，是合成样本进入训练、eval、RAG、memory、skill、router 或 self-improvement 前的质量、权利、污染和下游验证门；合成数据可用，但不能替代真实 hold-out 和真实分布锚点。
- Address range: c-000370 至 c-000375

## 2026-05-30 research | AI incident response postmortem 边界
- Topic: 第 6/7 层如何把 AI 事故转成分级、止血、取证、沟通、复盘、action item 和 regression eval。
- Synthesis: [[Research: AI incident response postmortem 边界]]
- Pages created: [[concepts/AIIncidentResponsePostmortem边界]]，[[Research: AI incident response postmortem 边界]]，[[sources/nist-ai-rmf-core-incident-response-2023]]，[[sources/oecd-defining-ai-incidents-2024]]，[[sources/oecd-ai-incidents-monitor-methodology-2026]]，[[sources/google-sre-emergency-response-2016]]，[[sources/google-sre-postmortem-culture-2016]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/AISafetyOpsGovernance边界]]，[[concepts/ToolRiskPermissioning边界]]，[[concepts/MultiProviderGovernance边界]]，[[concepts/AgentIdentityDelegation边界]]，[[concepts/DataQualityLabelQuality边界]]，[[sources/nist-genai-profile-data-privacy-2024]]，[[sources/eu-ai-act-risk-management-post-market-2024]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: AI incident response / postmortem 主属第 7 层，是第 6 层监控/eval 信号进入止血、取证、沟通、复盘、action item 和 regression eval 的事故闭环；postmortem 的价值在于把事故转成可验证改进。
- Address range: c-000363 至 c-000369

## 2026-05-30 research | Agent identity delegation 边界
- Topic: 第 5/7 层如何表示 agent 身份、委托链、责任主体、scope、审计和撤销路径。
- Synthesis: [[Research: Agent identity delegation 边界]]
- Pages created: [[concepts/AgentIdentityDelegation边界]]，[[Research: Agent identity delegation 边界]]，[[sources/ietf-agent-identity-protocol-draft-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/ToolRiskPermissioning边界]]，[[concepts/DataRightsPrivacyConsent边界]]，[[concepts/AISafetyOpsGovernance边界]]，[[concepts/MultiProviderGovernance边界]]，[[sources/nist-ai-agent-identity-authorization-2026]]，[[sources/mcp-authorization-2025]]，[[sources/mcp-security-best-practices-2025]]，[[sources/aws-secure-agent-access-mcp-2026]]，[[sources/nsa-mcp-security-design-2026]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Agent identity / delegation 主属第 5 层，是 agent 动作携带 actor、principal、grant、scope、credential、audit 和 revocation 的身份委托边界；第 7 层定义责任，第 5 层把责任带入 runtime。
- Address range: c-000360 至 c-000362

## 2026-05-30 research | Multi-provider governance 边界
- Topic: 第 7 层如何在多 provider/model/tool 进入 routing 前统一数据、地域、retention、training use、SLA、audit 和 fallback。
- Synthesis: [[Research: Multi-provider governance 边界]]
- Pages created: [[concepts/MultiProviderGovernance边界]]，[[Research: Multi-provider governance 边界]]，[[sources/azure-foundry-models-data-privacy-2026]]，[[sources/aws-bedrock-data-protection-2026]]，[[sources/aws-bedrock-model-invocation-logging-2026]]，[[sources/anthropic-api-data-retention-2026]]，[[sources/anthropic-api-data-residency-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Multi-provider governance 主属第 7 层，是 provider/vendor 控制面；它先按 data rights、region、retention、training use、SLA 和风险过滤 provider，再让第 3 层 routing 或第 5 层 tool use 执行。
- Address range: c-000353 至 c-000359

## 2026-05-30 research | Data quality label quality 边界
- Topic: 第 6 层如何判断反馈、label、trace、RAG 文档和训练候选是否可进入 eval、training、RAG、memory 或 skill。
- Synthesis: [[Research: Data quality label quality 边界]]
- Pages created: [[concepts/DataQualityLabelQuality边界]]，[[Research: Data quality label quality 边界]]，[[sources/tensorflow-data-validation-2026]]，[[sources/datasheets-for-datasets-2021]]，[[sources/data-cards-2022]]，[[sources/data-cascades-high-stakes-ai-2021]]，[[sources/openai-fine-tuning-data-quality-2026]]，[[sources/label-errors-benchmarks-2021]]，[[sources/huggingface-dataset-cards-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/DataFlywheelFeedbackLoop边界]]，[[concepts/RewardHackingEvalOverfitting边界]]，[[concepts/AISafetyOpsGovernance边界]]，[[concepts/RAG与Memory边界]]，[[concepts/Skill与ToolMemory边界]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Data quality / label quality 主属第 6 层，是 data flywheel 产生的反馈、label、trace、RAG 文档和训练候选成为 eval、training、memory、skill 或 router 证据前的质量门。
- Address range: c-000344 至 c-000352

## 2026-05-30 research | AI safety ops governance 边界
- Topic: 第 6/7 层如何把 AI 风险管理从 eval、red-team 和 incident 证据变成可执行组织流程。
- Synthesis: [[Research: AI safety ops governance 边界]]
- Pages created: [[concepts/AISafetyOpsGovernance边界]]，[[Research: AI safety ops governance 边界]]，[[sources/nist-ai-rmf-1-0-2023]]，[[sources/iso-iec-42001-ai-management-system-2023]]，[[sources/openai-preparedness-framework-2025]]，[[sources/anthropic-responsible-scaling-policy-v3-2026]]，[[sources/deepmind-frontier-safety-framework-2025]]，[[sources/microsoft-responsible-ai-standard-2022]]，[[sources/eu-ai-act-risk-management-post-market-2024]]，[[sources/google-saif-controls-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/ProductOrganizationLayer边界]]，[[concepts/RewardHackingEvalOverfitting边界]]，[[concepts/DataRightsPrivacyConsent边界]]，[[concepts/ToolRiskPermissioning边界]]，[[concepts/AgentHarness与TraceEval]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: AI Safety Ops / Governance 主属第 7 层，是第 6 层 eval/red-team/incident 证据进入 risk register、release gate、owner、monitoring、incident response 和 audit trail 的风险运行系统。
- Address range: c-000334 至 c-000343

## 2026-05-30 research | Tool risk permissioning 边界
- Topic: 第 5 层 agent 工具动作如何按风险等级进入权限、沙箱、审批、审计和回滚边界。
- Synthesis: [[Research: Tool risk permissioning 边界]]
- Pages created: [[concepts/ToolRiskPermissioning边界]]，[[Research: Tool risk permissioning 边界]]，[[sources/openai-agents-sdk-tool-guardrails-2026]]，[[sources/anthropic-computer-use-security-2026]]，[[sources/mcp-authorization-2025]]，[[sources/mcp-security-best-practices-2025]]，[[sources/owasp-llm-excessive-agency-2025]]，[[sources/nist-ai-agent-identity-authorization-2026]]，[[sources/aws-secure-agent-access-mcp-2026]]，[[sources/nsa-mcp-security-design-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/AgentHarness与TraceEval]]，[[concepts/DataRightsPrivacyConsent边界]]，[[concepts/RewardHackingEvalOverfitting边界]]，[[concepts/Skill与ToolMemory边界]]，[[concepts/ModelRoutingMixture边界]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Tool risk / permissioning 主属第 5 层，是 agent 从 reasoning 进入 action 前的动作准入层；prompt 不是权限边界，高风险工具必须通过 scope、sandbox、approval、audit 和 rollback 控制。
- Address range: c-000324 至 c-000333

## 2026-05-30 research | Data rights privacy consent 边界
- Topic: 第 7 层 data rights / privacy / consent 如何约束 service、memory、eval、training、vendor sharing 和数据飞轮。
- Synthesis: [[Research: Data rights privacy consent 边界]]
- Pages created: [[concepts/DataRightsPrivacyConsent边界]]，[[Research: Data rights privacy consent 边界]]，[[sources/openai-api-data-controls-2026]]，[[sources/openai-model-improvement-data-policy-2026]]，[[sources/anthropic-privacy-policy-2026]]，[[sources/anthropic-consumer-model-training-controls-2026]]，[[sources/anthropic-commercial-data-controls-2026]]，[[sources/google-vertex-ai-data-governance-2026]]，[[sources/eu-ai-act-data-governance-2024]]，[[sources/gdpr-data-subject-rights-2016]]，[[sources/nist-genai-profile-data-privacy-2024]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/DataFlywheelFeedbackLoop边界]]，[[concepts/ProductOrganizationLayer边界]]，[[concepts/RAG与Memory边界]]，[[concepts/RewardHackingEvalOverfitting边界]]，[[concepts/Skill与ToolMemory边界]]，[[sources/openai-data-sharing-controls-2026]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Data rights / privacy / consent 主属第 7 层，是产品数据进入 service、memory、eval、training 或供应商共享前的用途闸门；“可用于本次请求”不等于“可长期保存、记忆、评估或训练”。
- Address range: c-000313 至 c-000323

## 2026-05-30 research | Data flywheel feedback loop 边界
- Topic: 第 7 层真实使用反馈如何安全反哺 eval、RAG、memory、skill、router、training 和 self-improvement。
- Synthesis: [[Research: Data flywheel feedback loop 边界]]
- Pages created: [[concepts/DataFlywheelFeedbackLoop边界]]，[[Research: Data flywheel feedback loop 边界]]，[[sources/nvidia-ai-data-flywheel-2026]]，[[sources/openai-data-sharing-controls-2026]]，[[sources/google-rules-of-ml-2026]]，[[sources/google-mlops-continuous-delivery-2026]]，[[sources/hidden-technical-debt-ml-systems-2015]]，[[sources/agent-in-the-loop-data-flywheel-2025]]，[[sources/characterflywheel-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/数据飞轮复利]]，[[concepts/ProductOrganizationLayer边界]]，[[concepts/RewardHackingEvalOverfitting边界]]，[[concepts/Dream与SelfImprovement工程原语]]，[[concepts/RAG与Memory边界]]，[[concepts/Skill与ToolMemory边界]]，[[sources/openai-model-optimization-2026]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Data flywheel / feedback loop 主属第 7 层，不是自动训练通道；真实使用信号必须按证据类型分流，失败进 eval，事实缺口进 RAG，偏好进 memory，重复流程进 skill，成本/延迟进 routing/serving，稳定授权行为才进入训练候选。
- Address range: c-000304 至 c-000312

## 2026-05-30 research | Reward hacking eval overfitting 边界
- Topic: reward hacking、specification gaming、eval overfitting、benchmark leakage、reward tampering 和 KPI gaming 的稳定边界。
- Synthesis: [[Research: Reward hacking eval overfitting 边界]]
- Pages created: [[concepts/RewardHackingEvalOverfitting边界]]，[[Research: Reward hacking eval overfitting 边界]]，[[sources/openai-faulty-reward-functions-2016]]，[[sources/deepmind-specification-gaming-2020]]，[[sources/anthropic-reward-tampering-2024]]，[[sources/openai-reward-model-overoptimization-2022]]，[[sources/benchmarking-benchmark-leakage-2024]]，[[sources/openai-chain-of-thought-monitoring-2025]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/ReasoningEvalVerifier边界]]，[[concepts/Agent评估体系]]，[[concepts/Dream与SelfImprovement工程原语]]，[[concepts/ProductOrganizationLayer边界]]，[[concepts/ModelRoutingMixture边界]]，[[sources/openai-cot-monitorability-2025]]，[[sources/rewardbench-2024]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Reward hacking / eval overfitting 主属第 6 层，是 reward、grader、benchmark、KPI 或反馈闭环在优化压力下的失效模式；它会污染第 2 层训练、第 3 层 routing、第 5 层 agent、第 7 层产品指标和第 8 层自我改进。
- Address range: c-000296 至 c-000303

## 2026-05-30 research | Model routing mixture 边界
- Topic: model selection、model routing、cascade、MoE、Mixture-of-Agents 和 compound system model allocation 的稳定边界。
- Synthesis: [[Research: Model routing mixture 边界]]
- Pages created: [[concepts/ModelRoutingMixture边界]]，[[Research: Model routing mixture 边界]]，[[sources/openai-model-selection-2026]]，[[sources/routellm-2024]]，[[sources/routerbench-2024]]，[[sources/frugalgpt-2023]]，[[sources/optimizing-model-selection-compound-ai-systems-2025]]，[[sources/mixture-of-agents-2024]]，[[sources/switch-transformers-2021]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/Serving成本延迟边界]]，[[concepts/TestTimeCompute]]，[[concepts/ReasoningEvalVerifier边界]]，[[concepts/ProductOrganizationLayer边界]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: 外部 model routing 主属第 3 层 inference control；内部 MoE 主属第 2 层模型构建；Mixture-of-Agents 和 compound system model allocation 跨到第 5 层，但都必须由第 6 层 eval 和第 7 层产品 SLO/单位经济约束。
- Address range: c-000287 至 c-000295

## 2026-05-30 research | Product organization layer 边界
- Topic: 第 7 层如何把可靠 AI 能力变成产品表面、工作流、组织角色、单位经济和反馈飞轮。
- Synthesis: [[Research: Product organization layer 边界]]
- Pages created: [[concepts/ProductOrganizationLayer边界]]，[[Research: Product organization layer 边界]]，[[sources/anthropic-building-effective-agents-2024]]，[[sources/openai-practical-guide-building-agents-2025]]，[[sources/openai-agents-sdk-docs-2026]]，[[sources/bvp-vertical-ai-playbook-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/模型即产品]]，[[concepts/软件工厂]]，[[concepts/公司大脑]]，[[concepts/数据飞轮复利]]，[[concepts/工作流锁定]]，[[sources/openai-model-optimization-2026]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Product / organization layer 主属第 7 层，是第 6 层可靠能力进入真实产品、工作流、组织角色、审批边界、单位经济和 telemetry/data flywheel 的接口；它不是商业杂项，也不是 UI 层。
- Address range: c-000281 至 c-000286

## 2026-05-30 research | Multimodal eval simulation eval 边界
- Topic: 第 6 层如何评估静态多模态、视频/音频、生成安全、world-model、simulation 和 embodied agent。
- Synthesis: [[Research: Multimodal eval simulation eval 边界]]
- Pages created: [[concepts/MultimodalEvalSimulationEval边界]]，[[Research: Multimodal eval simulation eval 边界]]，[[sources/mmmu-2023]]，[[sources/mathvista-2023]]，[[sources/video-mme-2024]]，[[sources/openai-gpt-4o-system-card-2024]]，[[sources/worldmodelbench-2025]]，[[sources/worldsimbench-2024]]，[[sources/deepmind-sima-2024]]，[[sources/embodiedbench-2025]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/多模态与世界模型边界]]，[[concepts/AgentHarness与TraceEval]]，[[concepts/Omni世界模型]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Multimodal eval / simulation eval 主属第 6 层，是第 3 层多模态/世界模型、第 5 层 embodied agent、第 7 层实时产品和第 8 层仿真反馈之间的质量门；视觉质量不能替代物理一致性、行动后果和环境状态检查。
- Address range: c-000271 至 c-000280

## 2026-05-30 research | Reasoning eval verifier 边界
- Topic: 第 6 层如何评估 reasoning trace、过程监督、trace grading、reward model 和 verifier。
- Synthesis: [[Research: Reasoning eval verifier 边界]]
- Pages created: [[concepts/ReasoningEvalVerifier边界]]，[[Research: Reasoning eval verifier 边界]]，[[sources/openai-math-verifiers-2021]]，[[sources/lets-verify-step-by-step-2023]]，[[sources/openai-prover-verifier-games-2024]]，[[sources/openai-graders-docs-2026]]，[[sources/rewardbench-2024]]，[[sources/rewarding-progress-process-verifiers-2024]]，[[sources/processbench-2024]]，[[sources/process-reward-models-that-think-2025]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/TestTimeCompute]]，[[concepts/AgentHarness与TraceEval]]，[[concepts/Agent评估体系]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Reasoning eval / verifier 主属第 6 层，是第 3 层 reasoning、第 5 层 agent trace、第 2 层训练和第 8 层 self-improvement 的质量接口；稳定边界是 outcome verifier、process verifier、trace grader、CoT monitor、reward model 和 eval harness。
- Address range: c-000261 至 c-000270

## 2026-05-30 research | Skill library routing lifecycle
- Topic: skill library 规模化后如何路由、归因、更新、退役和安全治理。
- Synthesis: [[Research: Skill library routing lifecycle]]
- Pages created: [[concepts/SkillLibraryRouting生命周期]]，[[Research: Skill library routing lifecycle]]，[[sources/skillsvote-2026]]，[[sources/under-the-hood-skill-md-2026]]，[[sources/secure-agent-skills-2026]]，[[sources/reusable-skill-md-files-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，[[concepts/Skill与ToolMemory边界]]，`skills/autoresearch/references/program.md`
- Key insight: Skill library routing / lifecycle 仍归入第 4 层程序性知识库治理；大型库必须管理 collection/provenance、metadata routing、selection/loading、execution sandbox、outcome attribution、update/merge/deprecation/retirement，并由第 6 层 eval/security gate 和第 8 层 evidence-gated evolution 约束。
- Address range: c-000255 至 c-000260

## 2026-05-30 research | Serving 成本 延迟 边界
- Topic: serving、成本和延迟如何把第 3 层推理能力接到第 7 层产品部署约束。
- Synthesis: [[Research: Serving 成本 延迟 边界]]
- Pages created: [[concepts/Serving成本延迟边界]]，[[Research: Serving 成本 延迟 边界]]，[[sources/openai-latency-optimization-2026]]，[[sources/openai-cost-optimization-2026]]，[[sources/anthropic-prompt-caching-2026]]，[[sources/pagedattention-vllm-2023]]，[[sources/distserve-2024]]，[[sources/huggingface-tgi-2026]]，[[sources/huggingface-continuous-batching-2026]]，[[sources/nvidia-genai-perf-2026]]，[[sources/nvidia-tensorrt-llm-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Serving 是第 3 层 inference runtime，不是独立顶层；它通过 prefill/decode、KV cache、batching、prompt caching、TTFT/TPOT、goodput 和 cost/success 把模型能力约束到第 7 层产品 SLO 与 unit economics。
- Address range: c-000244 至 c-000254

## 2026-05-30 research | 多模态与世界模型边界
- Topic: 区分多模态、世界模型、VLA、embodied agent 和 simulation eval，并归入 AI 系统生成链。
- Synthesis: [[Research: 多模态与世界模型边界]]
- Pages created: [[concepts/多模态与世界模型边界]]，[[Research: 多模态与世界模型边界]]，[[sources/gemini-1-5-multimodal-long-context-2024]]，[[sources/openai-gpt-4o-2024]]，[[sources/openai-sora-world-simulators-2024]]，[[sources/deepmind-genie-2-2024]]，[[sources/world-models-2018]]，[[sources/rt-2-vla-2023]]
- Pages updated: [[concepts/Omni世界模型]]，[[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: 多模态是多信号输入/输出和融合能力，世界模型是状态、时间动态和行动后果的模拟能力；二者主归属第 3 层，不新增顶层。进入机器人或仿真时才跨到第 5 层 embodied agent，并由第 6 层 simulation eval 约束。
- Address range: c-000236 至 c-000243

## 2026-05-30 research | 推理时计算与 reasoning
- Topic: 推理时计算如何把第 3 层能力连接到第 5 层 agent loop 和第 6 层 eval。
- Synthesis: [[Research: 推理时计算与 reasoning]]
- Pages created: [[Research: 推理时计算与 reasoning]]，[[sources/openai-learning-to-reason-2024]]，[[sources/anthropic-extended-thinking-docs-2026]]，[[sources/scaling-llm-test-time-compute-2024]]，[[sources/chain-of-thought-2022]]，[[sources/self-consistency-2022]]，[[sources/tree-of-thoughts-2023]]，[[sources/openai-process-supervision-2023]]，[[sources/openai-cot-monitorability-2025]]
- Pages updated: [[concepts/TestTimeCompute]]，[[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: 推理时计算是第 3 层运行时能力机制，不是 prompt 或 harness；它通过 thinking、采样、搜索、verifier/reranker 和 tool-interleaved reasoning 增强能力，再由第 5 层 harness 变成 agent trace，由第 6 层 eval 衡量成功率、成本、延迟和可监控性。
- Address range: c-000227 至 c-000235

## 2026-05-30 research | Skill 与 tool memory workflow 边界
- Topic: 区分 skill、tool、memory、workflow、RAG 和 prompt，并把 skill 放回 AI 系统生成链。
- Synthesis: [[Research: Skill 与 tool memory workflow 边界]]
- Pages created: [[concepts/Skill与ToolMemory边界]]，[[Research: Skill 与 tool memory workflow 边界]]，[[sources/anthropic-skills-overview-2026]]，[[sources/agent-skills-specification-2026]]，[[sources/openai-agents-sdk-tools-2026]]，[[sources/agent-skills-architecture-survey-2026]]，[[sources/skillsbench-2026]]，[[sources/skill-text-to-structure-2026]]，[[sources/agent-skills-wild-security-2026]]，[[sources/malicious-agent-skills-wild-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Skill 是第 4 层可版本化程序性知识包，不是 tool 本身；它由第 5 层 harness 路由和执行，由第 6 层 eval/security gate 验证，也可以由第 8 层从 trace、memory 和失败模式中生成或修订。
- Address range: c-000217 至 c-000226

## 2026-05-30 research | Dream 与 self-improvement 工程原语
- Topic: 哪些 self-improvement 是可落地工程原语，哪些仍属于高风险前沿研究。
- Synthesis: [[Research: Dream 与 self-improvement 工程原语]]
- Pages created: [[concepts/Dream与SelfImprovement工程原语]]，[[Research: Dream 与 self-improvement 工程原语]]，[[sources/anthropic-dreams-docs-2026]]，[[sources/claude-managed-agents-memory-2026]]，[[sources/claude-managed-agents-dreaming-outcomes-2026]]，[[sources/reflexion-2023]]，[[sources/seal-self-adapting-language-models-2025]]，[[sources/sia-self-improving-ai-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，[[concepts/DreamCycle]]，[[concepts/AnthropicDreaming]]，[[concepts/自我改进AI循环]]，`skills/autoresearch/references/program.md`
- Key insight: Dream/self-improvement 的稳定工程链路是 trace → eval/outcome → dream/reflection → proposed diff → gate → apply。生产级先改 memory/context/tool/harness/eval；weight-level self-adaptation 是前沿层，必须加 hold-out eval、审计和人工门。
- Address range: c-000209 至 c-000216

## 2026-05-30 research | Agent harness 与 trace eval
- Topic: 为什么 harness 是 agent 的运行时层，以及 trace/eval 如何把运行时接到可靠性层。
- Synthesis: [[Research: Agent harness 与 trace eval]]
- Pages created: [[concepts/AgentHarness与TraceEval]]，[[Research: Agent harness 与 trace eval]]，[[sources/openai-agents-sdk-tracing-2026]]，[[sources/openai-agents-sdk-running-2026]]，[[sources/openai-agent-evals-trace-grading-2026]]，[[sources/anthropic-managed-agents-2026]]，[[sources/anthropic-effective-harnesses-long-running-agents-2026]]，[[sources/harness-bench-2026]]，[[sources/ai-harness-engineering-2026]]，[[sources/harness-audit-2026]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: Harness 不是脚手架，而是 agent runtime：runner loop、tools、state/session、workspace/sandbox、permissions、guardrails 和 trace。Trace 是第 5 层进入第 6 层 eval 的接口；eval 消费 trace、最终状态和成本，再反哺 context、tools、memory 和 model。
- Address range: c-000199 至 c-000208

## 2026-05-30 research | RAG 与 Memory 边界
- Topic: 区分外部知识检索、长期主体连续性、短期上下文和可复用 skill。
- Synthesis: [[Research: RAG 与 Memory 边界]]
- Pages created: [[concepts/RAG与Memory边界]]，[[Research: RAG 与 Memory 边界]]，[[sources/anthropic-context-engineering-cookbook-2026]]，[[sources/openai-agent-memory-2026]]，[[sources/openai-retrieval-docs-2026]]，[[sources/google-vertex-rag-engine-2026]]，[[sources/himem-2026]]，[[sources/memir-typed-memory-2026]]
- Pages updated: [[domains/AI知识体系]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: RAG 负责把外部知识按出处和检索质量送进上下文；Memory 负责跨任务维护 agent/用户/组织的连续性，并要处理写入、巩固、遗忘、冲突、权限和 stale 风险。
- Address range: c-000191 至 c-000198

## 2026-05-30 research | 微调 vs RAG vs 上下文工程
- Topic: 什么时候改 prompt/context，什么时候加 RAG，什么时候微调或蒸馏。
- Synthesis: [[Research: 微调 vs RAG vs 上下文工程]]
- Pages created: [[concepts/微调RAG上下文工程选择框架]]，[[Research: 微调 vs RAG vs 上下文工程]]，[[sources/microsoft-customizing-llms-2026]]，[[sources/microsoft-fine-tuning-considerations-2026]]，[[sources/openai-model-optimization-2026]]，[[sources/openai-optimizing-llm-accuracy-2026]]，[[sources/openai-fine-tuning-techniques-2025]]，[[sources/google-cloud-rag-overview]]，[[sources/openai-fine-tuned-rag-qdrant-2023]]
- Pages updated: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/_index]]，[[questions/_index]]，[[sources/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: 三者不是互斥选项；稳定顺序是 eval 基线 → 上下文工程 → RAG 补外部知识 → 微调/PEFT 稳行为 → 蒸馏降成本。RAG 和上下文工程主归属第 4 层，微调主归属第 2 层，三者都由第 6 层 eval 约束。
- Address range: c-000182 至 c-000190

## 2026-05-30 research | AI 知识体系总览
- Objective: 建立稳定、分层、可串联的 AI 工程知识体系，作为后续单点 research loop 的总地图。
- Synthesis: [[Research: AI知识体系总览]]
- Pages created: [[domains/AI知识体系]]，[[learning/AI体系学习路线]]，[[concepts/AI系统生成链]]，[[Research: AI知识体系总览]]，[[sources/stanford-ai-index-2026]]，[[sources/attention-is-all-you-need-2017]]，[[sources/scaling-laws-neural-language-models-2020]]，[[sources/instructgpt-rlhf-2022]]，[[sources/rag-2020]]，[[sources/react-2022]]，[[sources/distilling-knowledge-neural-network-2015]]，[[sources/huggingface-peft-docs]]，[[sources/openai-model-distillation-2024]]，[[sources/openai-agents-sdk-evolution-2026]]
- Pages updated: [[domains/_index]]，[[learning/_index]]，[[questions/_index]]，[[sources/_index]]，[[concepts/_index]]，[[index]]，[[hot]]，`skills/autoresearch/references/program.md`
- Key insight: AI 知识体系按“基础理论 → 模型构建 → 推理能力 → 上下文知识 → Agent 系统 → 评估可靠性 → 产品组织 → 自我改进”组织；自我改进不是孤立层，而是反哺数据、上下文、工具、eval 和模型构建的反馈环。
- Address range: c-000168 至 c-000181

## 2026-05-30 ingest | Gemini 联合负责人谈项目起源与未来
- Source: `.raw/notebooklm/gemini-coleads-origins-2026-05-30.md`
- Summary: [[sources/gemini-coleads-origins-2026-05-30|Gemini 联合负责人谈项目起源与未来]]
- Pages created: [[sources/gemini-coleads-origins-2026-05-30]]，[[Jeff Dean]]，[[Koray Kavukcuoglu]]，[[Noam Shazeer]]，[[Oriol Vinyals]]，[[Logan Kilpatrick]]，[[entities/Gemini]]，[[entities/GoogleDeepMind]]，[[concepts/蒸馏传承]]，[[concepts/单模型统一策略]]，[[concepts/Omni世界模型]]
- Pages updated: [[people/_index]]，[[entities/_index]]，[[concepts/_index]]，[[sources/_index]]，[[index]]，[[hot]]，[[log]]
- Key insight: Jeff Dean 半页备忘录推动 Brain+DeepMind 合并 → Gemini 诞生；蒸馏技术本质与 Hinton 原始论文一致（只需一个好 teacher+好 student）；Koray 预测 IO 2027 将展示模型自我学习改进 Gemini 自身。

## 2026-05-26 ingest | Effective Context Engineering for AI Agents — Anthropic Engineering

- Source: `.raw/articles/anthropic-context-engineering-agents-2026-05-26.md`（Anthropic Engineering Blog）
- Summary: [[sources/anthropic-context-engineering-agents-2026-05-26]]（c-000154）
- Pages created: [[sources/anthropic-context-engineering-agents-2026-05-26]]（c-000154）, [[concepts/上下文工程]]（c-000155）, [[concepts/上下文腐化]]（c-000156）
- Pages updated: [[concepts/渐进式上下文注入]]（加入 Anthropic JIT 检索表述）, [[concepts/_index]], [[sources/_index]], [[index]], [[hot]], [[log]]
- Key insight: 上下文工程是提示工程的超集——管理多轮推理中全部 token；Context Rot 是 Transformer n² 注意力的必然结果；Compaction + 结构化笔记 + 子 Agent + JIT 检索四策略构成长任务上下文管理完整体系；Anthropic JIT 检索与 claude-mem 三层渐进式注入独立收敛于同一原语。

## 2026-05-26 ingest | Demystifying Evals for AI Agents — Anthropic Engineering

- Source: `.raw/articles/anthropic-demystifying-evals-agents-2026-05-26.md`（Anthropic Engineering Blog）
- Summary: [[sources/anthropic-demystifying-evals-agents-2026-05-26]]（c-000150）
- Pages created: [[sources/anthropic-demystifying-evals-agents-2026-05-26]]（c-000150）, [[concepts/Agent评估体系]]（c-000151）, [[concepts/非确定性评测指标]]（c-000152）, [[concepts/Eval驱动开发]]（c-000153）
- Pages updated: [[concepts/_index]], [[sources/_index]], [[index]], [[hot]], [[log]]
- Key insight: Agent eval 的三层评分（代码/模型/人工）+ 四类 agent 差异化策略；pass@k vs pass^k 区分能力上界与可靠性下界；Eval 驱动开发是软件工厂在 agent 工程的延伸；与 Alex Albert 的"模型即产品"和自我改进循环的质量门深度收敛。

## 2026-05-22 ingest | How to Build a Self-Improving Company with AI — YC Root Access

- Source: `.raw/notebooklm/yc-root-access-self-improving-company-2026-05-22.md`（YouTube t-G67yKAHBQ，YC Root Access，14,669 字符）
- Summary: [[sources/yc-root-access-self-improving-company-2026-05-22]]（c-000146）
- Pages created: [[sources/yc-root-access-self-improving-company-2026-05-22]]（c-000146）, [[concepts/自我改进AI循环]]（c-000147）, [[concepts/软件即临时物]]（c-000148）, [[concepts/公司大脑]]（c-000149）
- Pages updated: [[concepts/Token最大化]], [[concepts/_index]], [[sources/_index]], [[index]], [[hot]], [[log]]
- Key insight: 五层 AI 循环架构（感知→策略→工具→质量门→学习）是封闭循环公司的技术化详解；YC 内部案例：监控 Agent 隔夜自动修复查询、Haj 用 2000 小时录音再生用户手册；"软件即临时物"与数据/上下文永久是重要哲学分割；四方（YC/GBrain/Anthropic/OpenAI）独立收敛到异步自我改进原语。

## 2026-05-22 ingest | How To Build A Company With AI From The Ground Up — Diana (YC)

- Source: `.raw/notebooklm/yc-diana-ai-company-ground-up-2026-05-22.md`（YouTube EN7frwQIbKc，Y Combinator，9,389 字符）
- Summary: [[sources/yc-diana-ai-company-ground-up-2026-05-22]]（c-000139）
- Pages created: [[sources/yc-diana-ai-company-ground-up-2026-05-22]]（c-000139）, [[people/Diana]]（c-000140）, [[concepts/封闭循环公司]]（c-000141）, [[concepts/可查询组织]]（c-000142）, [[concepts/软件工厂]]（c-000143）, [[concepts/Token最大化]]（c-000144）, [[concepts/三种员工原型]]（c-000145）
- Pages updated: [[people/_index]], [[concepts/_index]], [[sources/_index]], [[index]], [[hot]], [[log]]
- Key insight: Diana（YC）将公司架构从"生产力工具"升级为"操作系统"视角；封闭循环 + 可查询组织 + 软件工厂三框架与 Fiona Fung / Dario / Ryan Lopopolo 框架多点收敛；Token 最大化是 AI 时代的新核心指标。

## 2026-05-21 ingest | Inside How Anthropic Is Building the Next Claude — Alex Albert

- Source: `.raw/notebooklm/alex-albert-building-next-claude-2026-05-21.md`（YouTube T4ieZPIEmd8，Peter Yang，38,880 字符）
- Summary: [[sources/alex-albert-building-next-claude-2026-05-21]]（c-000132）
- Pages created: [[sources/alex-albert-building-next-claude-2026-05-21]]（c-000132）, [[people/AlexAlbert]]（c-000133）, [[people/PeterYang]]（c-000134）, [[concepts/模型即产品]]（c-000135）, [[concepts/单向门决策框架]]（c-000136）, [[concepts/Claude角色训练]]（c-000137）, [[concepts/Claude意识研究]]（c-000138）
- Pages updated: [[concepts/AdaptiveThinking]], [[people/_index]], [[concepts/_index]], [[sources/_index]], [[index]], [[hot]], [[log]]
- Key insight: Alex Albert（第一位 prompt engineer）揭示 Anthropic 把每个模型当产品管理；"单向门框架"与瓶颈转移论独立收敛；Claude Character 在 Agent 时代变得极其重要——长时间自主运行需要价值观支撑判断。

## 2026-05-20 ingest | autoresearch — Karpathy 自主 ML 研究循环

- Source: `.raw/articles/autoresearch-2026-05-20.md`（GitHub karpathy/autoresearch，82.2K ⭐，Python+Jupyter）
- Summary: [[sources/autoresearch-2026-05-20]]（c-000126）
- Pages created: [[sources/autoresearch-2026-05-20]]（c-000126）, [[entities/Autoresearch]]（c-000127）, [[people/AndrejKarpathy]]（c-000128）, [[concepts/自主ML研究循环]]（c-000129）, [[concepts/程序驱动研究]]（c-000130）, [[concepts/固定时间窗实验]]（c-000131）
- Pages updated: [[entities/_index]], [[people/_index]], [[concepts/_index]], [[sources/_index]], [[index]], [[hot]], [[log]]
- Key insight: program.md 作为研究接口与本 vault 的 skill 文件结构完全同构；固定 5 分钟时间窗让 agent 过夜自主跑约 100 次实验，val_bpb 指标与词表大小无关，是 Karpathy 极简主义（one GPU, one file, one metric）在自主研究场景的完整实现。

## 2026-05-19 ingest | RuView — WiFi DensePose

- Source: `.raw/articles/ruview-2026-05-19.md`（GitHub README，ruvnet/RuView，59,973 ⭐，Rust，MIT）
- Summary: [[sources/ruview-2026-05-19]]（c-000116）
- Pages created: [[sources/ruview-2026-05-19]]（c-000116）, [[entities/RuView]]（c-000117）, [[people/ruvnet]]（c-000118）, [[entities/CognitumSeed]]（c-000119）, [[entities/RuVector]]（c-000120）, [[concepts/WiFiDensePose]]（c-000121）, [[concepts/CSI感知]]（c-000122）, [[concepts/WiFi生命体征监测]]（c-000123）, [[concepts/WASM边缘模块]]（c-000124）, [[concepts/自监督WiFi学习]]（c-000125）
- Pages updated: [[entities/_index]], [[people/_index]], [[concepts/_index]], [[sources/_index]], [[index]], [[hot]], [[log]]
- Key insight: RuView 用 $9 ESP32-S3 传感器 + Channel State Information 实现无摄像头穿墙感知，65 个 no_std Rust WASM 边缘模块覆盖从医疗到工业的完整场景；对比自监督学习让 ~55KB 模型在 ESP32 上 30 秒适应新房间，是边缘 AI 与 WiFi 感知结合的完整工程实践。

## 2026-05-17 ingest | Scientific Agent Skills — GitHub README

- Source: `.raw/articles/scientific-agent-skills-2026-05-17.md`（GitHub README，K-Dense-AI/scientific-agent-skills，23,247 ⭐）
- Summary: [[sources/scientific-agent-skills-2026-05-17]]
- Pages created: [[sources/scientific-agent-skills-2026-05-17]]（c-000111）, [[entities/KDenseAI]]（c-000112）, [[entities/ScientificAgentSkills]]（c-000113）, [[concepts/AgentSkillsStandard]]（c-000114）, [[skills/scientific-agent-skills-collection]]（c-000115）
- Pages updated: [[skills/_index]], [[entities/_index]], [[sources/_index]], [[concepts/_index]], [[index]], [[hot]], [[log]]
- Key insight: Scientific Agent Skills 是目前最大的开放科学研究 Agent Skill 集合（135 skills，100+ 数据库），遵循跨平台 Agent Skills 标准；标志着 agent skill 生态从单一平台（Claude Code）向开放标准迁移；BGPT Paper Search、Open Notebook、GeoMaster、Consciousness Council 是值得关注的差异化 skill。

## 2026-05-16 ingest | OpenHuman — GitHub README

- Source: `.raw/articles/openhuman-2026-05-16.md`（GitHub README，tinyhumansai/openhuman，10,137 ⭐）
- Summary: [[sources/openhuman-2026-05-16]]
- Pages created: [[sources/openhuman-2026-05-16]]（c-000104）, [[entities/OpenHuman]]（c-000105）, [[entities/TinyHumansAI]]（c-000106）, [[people/Senamakel]]（c-000107）, [[concepts/TokenJuice]]（c-000108）, [[concepts/记忆自动拉取]]（c-000109）, [[concepts/MemoryTree]]（c-000110）
- Pages updated: [[entities/_index]], [[sources/_index]], [[concepts/_index]], [[people/_index]], [[index]], [[hot]], [[log]]
- Key insight: OpenHuman 将 Karpathy 的 obsidian-wiki workflow 自动化——Auto-fetch 每 20 分钟拉取 118+ OAuth 连接数据，经 TokenJuice 压缩后存入本地 SQLite + Obsidian vault；解决 agent harness 冷启动问题，同时可选接入 AgentMemory 与 Claude Code/Cursor 共享记忆。

## 2026-05-16 ingest | The Founder's Playbook — Anthropic

- Source: `.raw/articles/founders-playbook-2026-05-16.md`（PDF，35 页，465 KB，pdf2txt.py 提取）
- Summary: [[sources/founders-playbook-2026-05-16]]
- Pages created: [[sources/founders-playbook-2026-05-16]]（c-000097）, [[entities/ClaudeCowork]]（c-000098）, [[concepts/AI原生创业生命周期]]（c-000099）, [[concepts/智能体技术债]]（c-000100）, [[concepts/创始人编排者角色]]（c-000101）, [[concepts/数据飞轮复利]]（c-000102）, [[concepts/工作流锁定]]（c-000103）
- Pages updated: [[entities/_index]], [[sources/_index]], [[concepts/_index]], [[index]], [[hot]], [[log]]
- Key insight: AI 原生创业四阶段框架（Idea→MVP→Launch→Scale），每阶段有明确退出条件；Claude Cowork 是 Anthropic 新产品（运营自动化层）；智能体技术债是 MVP 阶段核心风险（CLAUDE.md 是防线）；Scale 阶段护城河双支柱：数据飞轮（不可复制）+ 工作流锁定（不可离开）；"瓶颈不再是能构建什么，而是选择构建什么"。
- Addresses: c-000097 ~ c-000103

## 2026-05-15 ingest | Software Fundamentals Matter More Than Ever — Matt Pocock（AI Engineer）

- Source: `.raw/articles/mattpocock-software-fundamentals-2026-05-15.md`（YouTube，yt-dlp auto-captions，18:26）
- Summary: [[sources/mattpocock-software-fundamentals-2026-05-15]]
- Pages created: [[sources/mattpocock-software-fundamentals-2026-05-15]], [[concepts/设计概念]], [[concepts/深模块架构]]
- Pages updated: [[people/MattPocock]], [[concepts/_index]], [[index]], [[hot]], [[log]]
- Key insight: "代码不便宜，坏代码是有史以来最贵的"；AI 在好代码库里表现极好，所以软件基本功比以前更重要；设计概念（Brooks）解释 AI 对齐失败的根本原因；深模块架构（Ousterhout）是 AI 友好代码库的结构特征；与瓶颈转移论/AmdahlsLawInAI 三方独立收敛。

## 2026-05-15 skills | 建立跨来源 Skills 分类体系

- Summary: [[skills/_index]]
- Pages created: [[skills/_index]], [[skills/mattpocock-collection]], [[skills/claude-obsidian-collection]]
- Pages updated: [[index]], [[hot]], [[log]]
- Key insight: 首次建立统一 skills 分类体系（7 类），整合 mattpocock/skills（18 skills + deprecated）和 claude-obsidian（11 skills）；发现 Matt 也用 Obsidian（个人扁平 vault）；deprecated `ubiquitous-language` 的"示例对话"格式值得借鉴；三项跨来源收敛——对齐/上下文显式化/异步维护。

## 2026-05-15 ingest | Skills For Real Engineers — mattpocock/skills

- Source: `.raw/articles/mattpocock-skills-2026-05-15.md`（GitHub repo，mattpocock/skills，⭐ 82,759）
- Summary: [[sources/mattpocock-skills-2026-05-15]]
- Pages created: [[sources/mattpocock-skills-2026-05-15]], [[people/MattPocock]], [[concepts/共享领域语言]], [[concepts/Grilling模式]]
- Pages updated: [[people/_index]], [[concepts/_index]], [[index]], [[hot]], [[log]]
- Key insight: Matt Pocock 提出 AI 辅助开发四大失败模式（对齐失败/术语鸿沟/缺反馈/软件熵），对应修复：Grilling 模式（任务前审讯对齐）、共享领域语言 CONTEXT.md、TDD 红绿重构、架构意识；三者与 JIT 规划、瓶颈转移论、代码仓库即记录系统独立收敛：AI 时代的瓶颈在于人机对齐，不在代码生成速度。

## 2026-05-14 ingest | VibeVoice — 开源前沿语音 AI 模型族（Microsoft）

- Source: `.raw/articles/vibevoice-2026-05-14.md`（GitHub repo，microsoft/VibeVoice，⭐ 47,087）
- Summary: [[sources/vibevoice-2026-05-14]]
- Pages created: [[sources/vibevoice-2026-05-14]], [[entities/VibeVoice]], [[entities/Microsoft]], [[concepts/下一令牌扩散]], [[concepts/长音频单遍处理]]
- Pages updated: [[entities/_index]], [[concepts/_index]], [[index]], [[hot]], [[log]]
- Key insight: VibeVoice 是 Microsoft Research 的开源语音 AI 家族；核心创新是 7.5 Hz 超低帧率连续语音令牌化 + Next-Token Diffusion（LLM+扩散头混合架构），支持 60-90 分钟长音频单遍处理；TTS 代码因深度伪造滥用主动下架，是高质量开源语音合成伦理困境的典型案例；ASR 已集成 HuggingFace Transformers。

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
