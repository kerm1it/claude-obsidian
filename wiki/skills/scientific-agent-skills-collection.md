---
id: c-000115
address: c-000115
type: skills-collection
title: "Scientific Agent Skills — 科学研究技能集"
source: https://github.com/K-Dense-AI/scientific-agent-skills
author: "[[entities/KDenseAI]]"
stars: 23247
created: 2026-05-17
tags:
  - skills
  - science
  - research
  - open-source
related:
  - "[[skills/_index]]"
  - "[[entities/ScientificAgentSkills]]"
  - "[[entities/KDenseAI]]"
  - "[[concepts/AgentSkillsStandard]]"
  - "[[sources/scientific-agent-skills-2026-05-17]]"
---

# Scientific Agent Skills — 科学研究技能集

[[entities/KDenseAI]] 出品，⭐ 23,247。**135 个科学研究 skills**，遵循开放的 [[concepts/AgentSkillsStandard|Agent Skills 标准]]。  
安装：`npx skills add K-Dense-AI/scientific-agent-skills`

---

## 🧬 生物信息学 & 基因组学（21+ skills）

| Skill | 核心功能 |
|-------|----------|
| **BioPython** | DNA/RNA/蛋白质序列分析，NCBI Entrez（38 个子数据库），BLAST |
| **pysam** | SAM/BAM/VCF 文件处理，序列对比读取 |
| **scikit-bio** | 微生物组分析，多样性指数，系统发育 |
| **BioServices** | 统一访问 ~40 个生物信息学服务（REST API）|
| **Scanpy** | 单细胞 RNA-seq 分析，QC/归一化/降维/聚类 |
| **AnnData** | 单细胞数据结构，高效存储 |
| **scvi-tools** | 单细胞深度学习变分模型 |
| **scVelo** | RNA 速度（RNA Velocity）—— 细胞分化方向预测 |
| **Arboreto** | 基因调控网络（GRN）推断 |
| **Cellxgene Census** | CZI 单细胞公共数据库整合 |
| **gget** | 快速基因组数据库查询（20+ 来源）|
| **geniml, gtars** | 基因组区间机器学习工具 |
| **deepTools** | 深度测序数据分析与可视化 |
| **TileDB-VCF** | 大规模 VCF 数据库（增量添加样本，高效群体查询）|
| **PyDESeq2** | RNA-seq 差异表达分析 |
| **ETE Toolkit** | 系统发育树操作与可视化 |
| **Phylogenetics** | MAFFT / IQ-TREE 2 / FastTree 工作流 |

---

## 🧪 化学信息学 & 药物发现（10+ skills）

| Skill | 核心功能 |
|-------|----------|
| **RDKit** | 分子指纹、SAR 分析、属性预测、合成可达性 |
| **Datamol** | RDKit 之上的简化分子操作，分子生成 |
| **Molfeat** | 分子特征化与嵌入 |
| **DeepChem** | ADMET 预测，分子属性深度学习 |
| **TorchDrug** | 分子图神经网络，药物-靶标结合预测 |
| **DiffDock** | 扩散模型分子对接，虚拟筛选 |
| **OpenMM + MDAnalysis** | 分子动力学模拟 + 轨迹分析 |
| **Rowan** | 云端量子化学：pKa、对接、共折叠 |
| **MedChem** | 药物相似性过滤，铅化合物优化 |
| **PyTDC** | 药物发现基准测试套件 |

---

## 🔬 蛋白质组学 & 质谱（2 skills）

| Skill | 核心功能 |
|-------|----------|
| **matchms** | 质谱谱图匹配，光谱相似性搜索 |
| **pyOpenMS** | LC-MS/MS 处理，肽段鉴定，蛋白质定量 |

---

## 🏥 临床研究 & 精准医学（8+ skills）

| Skill | 核心功能 |
|-------|----------|
| **Database Lookup** | ClinicalTrials.gov、ClinVar、ClinPGx、COSMIC、FDA、cBioPortal 等 |
| **DepMap** | 癌症细胞系依赖性评分，药物敏感性，基因效应谱 |
| **Imaging Data Commons** | NCI 放射学 & 病理学数据集（idc-index）|
| **PyHealth** | 电子病历分析，临床预测模型 |
| **NeuroKit2** | ECG/PPG/EDA 生理信号处理 |
| **Clinical Decision Support** | 临床决策辅助工作流 |
| **Clinical Reports** | 结构化临床报告生成 |
| **Treatment Plans** | 治疗方案制定，靶向治疗匹配 |

---

## 🖼️ 医学影像 & 数字病理（3 skills）

| Skill | 核心功能 |
|-------|----------|
| **pydicom** | DICOM 文件处理，医学影像元数据 |
| **histolab** | 全切片图像（WSI）分析，计算病理 |
| **PathML** | 病理机器学习工作流 |

---

## 🧠 神经科学 & 电生理（1 skill）

**Neuropixels-Analysis**：胞外棘波记录，硅探针数据处理，棘波排序

---

## 🤖 机器学习 & AI（16+ skills）

| Skill | 核心功能 |
|-------|----------|
| **PyTorch Lightning** | 深度学习训练框架（科学任务优化）|
| **Transformers** | HuggingFace 预训练模型，科学 NLP |
| **Stable Baselines3** | 强化学习算法库 |
| **PufferLib** | 强化学习环境封装 |
| **scikit-learn** | 经典 ML：分类/回归/聚类/降维 |
| **scikit-survival** | 生存分析，风险预测 |
| **SHAP** | 模型可解释性，特征重要性 |
| **aeon** | 时间序列分类与预测 |
| **TimesFM** | Google 零样本时间序列基础模型 |
| **PyMC** | 贝叶斯统计建模，MCMC 采样 |
| **PyMOO** | 多目标优化（遗传算法等）|
| **Torch Geometric** | 图神经网络，分子 / 知识图谱 |
| **UMAP-learn** | 降维与可视化 |
| **statsmodels** | 统计建模，假设检验，回归分析 |

---

## 🔮 材料科学 & 物理（7 skills）

| Skill | 核心功能 |
|-------|----------|
| **Pymatgen** | 晶体结构分析，相图，计算化学 |
| **COBRApy** | 代谢建模，通量平衡分析 |
| **Astropy** | 天文数据分析，坐标变换，宇宙学计算 |
| **Cirq** | Google 量子电路模拟 |
| **PennyLane** | 量子机器学习 |
| **Qiskit** | IBM 量子计算 |
| **QuTiP** | 量子系统数值模拟 |

---

## ⚙️ 工程 & 仿真（4 skills）

| Skill | 核心功能 |
|-------|----------|
| **MATLAB/Octave** | 数值计算，工程仿真 |
| **FluidSim** | 计算流体动力学（CFD）|
| **SimPy** | 离散事件仿真，资源竞争建模 |
| **SymPy** | 符号数学，微积分，方程求解 |

---

## 📊 数据分析 & 可视化（16+ skills）

| Skill | 核心功能 |
|-------|----------|
| **Matplotlib** | 发表级可视化，全定制 |
| **Seaborn** | 统计数据可视化 |
| **Scientific Visualization** | 科学图表最佳实践 |
| **GeoPandas** | GIS 分析，空间数据处理 |
| **GeoMaster** | 遥感、卫星图像、地球观测（500+ 示例，空间 ML）|
| **Dask** | 大规模并行数据处理 |
| **Polars** | 高性能 DataFrame（Rust 实现）|
| **Vaex** | 超大规模懒惰求值数据分析 |
| **NetworkX** | 网络/图分析与可视化 |
| **Document Skills** | PDF/DOCX/PPTX/XLSX 解析与生成 |
| **Infographics** | 10 种类型，8 种风格，色觉无障碍调色板 |
| **Markdown & Mermaid** | 文本图表（作为文档默认标准）|
| **EDA** | 探索性数据分析工作流 |
| **Statistical Analysis** | 假设检验，功效分析，实验设计 |

---

## 🧪 实验室自动化（4 skills）

| Skill | 核心功能 |
|-------|----------|
| **PyLabRobot** | Opentrons 液体处理协议 |
| **Ginkgo Cloud Lab** | 无细胞蛋白表达，自主 RAC 基础设施 |
| **Protocols.io** | 实验方案管理，社区分享 |
| **Benchling / LabArchives** | LIMS 集成，实验室数据管理 |

---

## 🔬 多组学 & 系统生物学（4+ skills）

| Skill | 核心功能 |
|-------|----------|
| **PrimeKG** | 精准医学知识图谱（基因-药物-疾病-表型）|
| **HypoGeniC** | 多组学数据整合 |
| **LaminDB** | 生物数据管理，版本控制 |
| **Database Lookup** | KEGG、Reactome、STRING 通路分析 |

---

## 🧬 蛋白质工程 & 设计（3 skills）

| Skill | 核心功能 |
|-------|----------|
| **ESM** | Meta 蛋白质语言模型，结构预测，序列设计 |
| **Glycoengineering** | N/O-糖基化预测，治疗性抗体优化 |
| **Adaptyv** | 云端自动化蛋白测试与验证 |

---

## 📚 科学传播（20+ skills）

| Skill | 核心功能 |
|-------|----------|
| **Paper Lookup** | 统一检索 10 个数据库（PubMed、PMC、bioRxiv、medRxiv、arXiv、OpenAlex、Crossref、Semantic Scholar、CORE、Unpaywall）|
| **BGPT Paper Search** | 从论文全文提取 25+ 结构化字段（方法/结果/样本量/质量评分），非摘要 |
| **Literature Review** | 文献综述自动化 |
| **Scientific Writing** | 科学论文写作辅助 |
| **Peer Review** | 同行评审 |
| **Open Notebook** | 自托管 NotebookLM 替代品（16+ AI 提供商，多说话人播客生成）|
| **Parallel Web** | 带引用的合成网络搜索摘要 |
| **Scientific Slides** | 幻灯片生成 |
| **LaTeX Posters / PPTX Posters** | 学术海报 |
| **Scientific Schematics** | 科学示意图 |
| **Infographics** | 信息图表 |
| **Citation Management** | 文献管理，pyzotero |
| **Generate Image** | AI 图像生成（FLUX.2 Pro + Gemini 3 Pro）|
| **Venue Templates** | 期刊/会议格式模板 |

---

## 🔬 科学数据库（6 skills → 100+ 数据库）

| Skill | 覆盖 |
|-------|------|
| **Database Lookup** | 78 个公共数据库（化学/基因组/临床/通路/专利/经济/天文）|
| **DepMap** | 癌症细胞系依赖性与药物敏感性 |
| **Imaging Data Commons** | NCI 放射学 & 病理数据集 |
| **PrimeKG** | 精准医学知识图谱 |
| **U.S. Treasury Fiscal Data** | 国债、财政报告、国债拍卖、汇率 |
| **Hugging Science** | HuggingFace 上 17 个科学领域的数据集/模型/Space 精选目录 |

---

## 🔧 基础设施 & 平台（7+ skills）

| Skill | 核心功能 |
|-------|----------|
| **Modal** | 云计算，无服务器 GPU 工作负载 |
| **GPU Optimization** | CuPy、Numba CUDA、cuDF、cuML、cuGraph、KvikIO、cuCIM 等 RAPIDS 生态 |
| **DNAnexus** | 基因组云平台 |
| **LatchBio** | 生物信息学工作流云平台 |
| **OMERO** | 显微镜图像管理 |
| **Opentrons** | 液体处理机器人协议 |
| **Get Available Resources** | 检测当前环境可用资源 |

---

## 🎓 研究方法论（12+ skills）

| Skill | 核心功能 |
|-------|----------|
| **Scientific Brainstorming** | 头脑风暴，创意发散 |
| **Hypothesis Generation** | 假设生成与评估 |
| **Scientific Critical Thinking** | 批判性分析 |
| **Scholar Evaluation** | 学者评价与文献质量评估 |
| **What-If Oracle** | 多分支可能性探索，风险分析，战略选项 |
| **Consciousness Council** | 多元专家视角，魔鬼代言人分析 |
| **DHDNA Profiler** | 从任意文本提取思维模式和认知特征 |
| **Research Grants** | 科研基金申请写作 |
| **Research Lookup** | 研究资源发现 |
| **Market Research Reports** | 市场分析报告 |
| **ISO 13485** | 医疗器械认证合规 |

---

## 与现有 Skills 体系的对比

| 维度 | mattpocock/skills | claude-obsidian | **Scientific Agent Skills** |
|------|-------------------|-----------------|------------------------------|
| 定位 | 工程实践，反 vibe coding | 知识管理，wiki 体系 | 科学研究，AI 科学家 |
| 数量 | 18（+4 deprecated）| 11 | **135** |
| 语言 | TypeScript/JS 生态 | Markdown/Python | Python 科学生态 |
| 数据库 | — | — | **100+** |
| 标准 | Agent Skills | Agent Skills | **Agent Skills** |

---

## 来源

- [[entities/ScientificAgentSkills]] — 实体页
- [[sources/scientific-agent-skills-2026-05-17|来源：GitHub README]]
