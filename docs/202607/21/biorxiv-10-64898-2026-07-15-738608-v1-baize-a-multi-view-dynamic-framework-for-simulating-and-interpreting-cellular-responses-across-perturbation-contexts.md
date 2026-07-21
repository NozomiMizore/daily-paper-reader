---
title: "BaiZe: A Multi-View Dynamic Framework for Simulating and Interpreting Cellular Responses Across Perturbation Contexts"
title_zh: BaiZe：一个用于模拟和解释跨扰动情境细胞响应的多视角动态框架
authors: "Zeng, Q., Cai, W., Tian, R., Wang, Q., Zhou, D., Pan, M., Yang, H., Liu, Z., Lin, G. N., Wang, Z."
date: 2026-07-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.15.738608v1.full.pdf"
tags: ["query:virtual-cell"]
score: 10.0
evidence: 预测不同遗传、化学、时间扰动下的转录组变化
tldr: 现有模型多针对特定扰动类型或情境。本文提出BaiZe，基于多视图条件状态转换的框架，从对照转录组结合遗传、化学、时间及染色质可及性信息预测扰动后转录组。支持对未见过的细胞状态、遗传扰动、多基因组合、化学结构、剂量、时间阶段及物种上下文的预测。在多种扰动设定中有效恢复主要转录程序，整合ATAC-seq可提升预测并归因关键染色质区域。BaiZe还支持人鼠跨物种迁移并连接表型投影，为细胞响应理解提供通用可解释框架。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-15-738608-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1514, \"height\": 1870, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-15-738608-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1458, \"height\": 1864, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-15-738608-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1514, \"height\": 1994, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-15-738608-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1460, \"height\": 1026, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-15-738608-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1469, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-15-738608-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1522, \"height\": 1912, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-15-738608-v1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1451, \"height\": 1859, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-15-738608-v1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1496, \"height\": 1189, \"label\": \"Figure\"}]"
motivation: 现有模型无法跨扰动类型和生物学情境预测细胞响应，缺乏统一框架。
method: 构建多视图条件状态转换模型，整合对照转录组及遗传、化学、时间、ATAC-seq信息预测扰动后转录组。
result: 在多种扰动条件下有效恢复主要转录程序，整合ATAC-seq提升预测并归因染色质区域，支持跨物种迁移。
conclusion: BaiZe提供了广泛适用的细胞响应预测与解释框架，可优先排序扰动假设。
---

## 摘要
准确预测细胞如何响应扰动对于理解细胞调控和优先选择实验干预措施至关重要，然而现有模型通常针对特定扰动类型或生物学情境而设计。本文提出BaiZe，一个多视角条件状态转移框架，它根据对照状态转录组以及遗传、化学、时间和可选的染色质可及性信息来预测扰动后的转录组。BaiZe将扰动响应建模为细胞状态之间的情境依赖转换。BaiZe支持对未见的细胞状态和遗传扰动、未见的多基因组合、化学结构和剂量、时间阶段以及物种情境的预测。跨不同扰动设置的基准测试表明，BaiZe能有效恢复在先前未见条件下的主要转录响应程序。整合匹配的ATAC-seq情境进一步改善了选定的状态转移预测，并能够基于模型将染色质区域归因于响应相关基因和通路。BaiZe还支持从人类到小鼠细胞系统的扰动响应少样本迁移，并将预测的转录组连接到候选形态学投影。为便于解释和使用，BaiZe-Agent将响应基因、通路、染色质证据、跨物种预测和投影表型组织成可追溯、可查询的扰动记录。总之，BaiZe提供了一个广泛适用的框架，用于预测和解释情境依赖的细胞响应，并在不同扰动设置中优先选择假设。

## Abstract
Accurately predicting how cells respond to perturbations is important for understanding cellular regulation and prioritizing experimental interventions, yet existing models are often designed for specific perturbation types or biological contexts. Here we present BaiZe, a multi-view conditional state-transition framework that predicts the post-perturbation transcriptome from a control-state transcriptome together with genetic, chemical, temporal and optional chromatin-accessibility information. BaiZe models perturbation responses as context-dependent transitions between cellular states. BaiZe supports prediction across held-out cell states and genetic perturbations, unseen multi-gene combinations, chemical structures and doses, temporal stages and species contexts. Benchmarking across diverse perturbation settings demonstrates that BaiZe effectively recovers major transcriptional response programs under previously unseen conditions. Incorporating matched ATAC-seq context further improves selected state-transition predictions and enables model-based attribution of chromatin regions to response-associated genes and pathways. BaiZe also supports few-shot transfer of perturbation responses from human to mouse cellular systems and connects predicted transcriptomes to candidate morphology projections. To facilitate interpretation and use, BaiZe-Agent organizes response genes, pathways, chromatin evidence, cross-species predictions and projected phenotypes into traceable, queryable perturbation records. Together, BaiZe provides a broadly applicable framework for predicting and interpreting context-dependent cellular responses and for prioritizing hypotheses across diverse perturbation settings.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有单细胞扰动响应预测模型大多针对特定扰动类型（如基因敲除、药物处理）或特定生物学情境设计，缺乏一个统一的框架来模拟和解释跨多种扰动情境（遗传、化学、时间、跨物种）的细胞响应。实验覆盖的扰动空间远小于理论可能的组合（基因组合、药物剂量、细胞状态、时间点、物种），亟需计算模型填补未测量条件，并优先选择最具信息量的干预实验。
- **整体含义**：将扰动响应建模为上下文依赖的细胞状态转移，有望推动“虚拟细胞”计划，通过预测性、可查询的方式连接分子状态、干预和表型，为功能基因组学、疾病机制、靶点发现和表型筛选提供统一的计算基础。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将扰动响应视为从对照状态转录组到扰动后转录组的情境依赖转移。模型接收对照状态转录组，结合扰动条件（遗传靶点、化学结构/剂量、时间/状态标签、可选ATAC染色质可及性），预测转录组变化残差，加回对照状态得到最终预测。
- **关键技术细节**：
  - **模型架构**：包含细胞背景编码器、条件编码器和条件扩散解码器。
    - 细胞背景编码器：将对照RNA谱映射为细胞起始状态的潜在表示。
    - 条件编码器：将干预信息（如基因嵌入、摩根指纹+剂量、时间/状态嵌入、ATAC嵌入）编码为共享条件表示。
    - 扩散解码器：通过迭代去噪生成扰动特异性的转录组残差。
  - **公式与流程**：定义观察到的表达变化 Δx_obs = x_post - x_ctrl。确定性分支估计主变化 μ_det = h_mean_delta + h_gene_prior；残差 r_res = Δx_obs - μ_det；对残差进行前向加噪，去噪网络预测干净残差；训练目标为残差扩散的MSE损失。推理时，预测变化 Δx_pred = μ_det + λ_res * r_hat，重构转录组 x_pred = x_ctrl + Δx_pred。
  - **统一条件接口**：遗传、化学、时间、ATAC均通过条件编码器映射到同一空间，与细胞背景表示融合。
  - **多视图扩展**：ATAC可及性作为可选调节视图，用于改进预测和归因；跨物种通过直系同源基因对齐实现零样本和少样本迁移；转录组预测可输入特征扩散模型（MorphDiff）生成多通道形态学投影。
  - **BaiZe-Agent**：基于预存扰动结果的自然语言查询系统，将响应基因、通路、染色质证据、跨物种预测和形态学投影组织成可追溯记录。

### 3. 实验设计：数据集/场景、基准、对比方法

- **数据集与场景**（共7类主要任务）：
  - 未见细胞状态预测：人类胚胎10x多组学（GSE218314），留出HYPO/VE状态。
  - 未见遗传扰动：Adamson Perturb-seq（GSE90546），留出部分基因扰动。
  - 多基因组合预测：Norman Perturb-seq（GSE133344），留出双基因组合和ATF6+EIF2AK3+ERN1三基因组合。
  - 药物响应预测：Sci-Plex（GSE139944），包括随机细胞、未见药物、留出细胞系（K562、A549、MCF7）等拆分。
  - ATAC整合预测：MultiPerturb-seq（GSE277747）和人类胚胎多组学，比较RNA-only vs RNA+ATAC。
  - 时间预测：HSPC时间序列多组学（GSE305370），留出供体13176进行跨供体预测。
  - 跨物种预测：人类CD8 T细胞（GSE218988）→小鼠肿瘤浸润T细胞（GSE203593），零样本和5%/10%少样本适应。
  - SNP-informed扰动：使用rs2057482提示HIF1A，在Replogle K562 CRISPRi数据上评估。
- **基准与对比方法**：
  - 各任务分别与任务相关的方法比较：scGPT、Geneformer、scGen、Ridge、GEARS、UCE等。
  - 消融实验：RNA vs RNA+ATAC、ATAC guidance scale消融、组件消融、条件编码策略（表达空间相加 vs 潜在空间条件控制）等。
- **评估指标**：全局Pearson、Top20 Delta Pearson、Top20 MSE、相反方向率（ODR）。既评估全转录组相似性，也聚焦于响应最显著的基因。

### 4. 资源与算力

- **论文未明确说明**使用的GPU型号、数量、训练时长等计算资源信息。Methods中仅给出模型维度和训练配置（如扩散时间步、采样步数），但未提及硬件细节。因此，无法评估其计算开销或可复现性中的资源需求。

### 5. 实验数量与充分性

- **实验数量**：论文设计了约7大类主要实验，每类下包含多个子任务（如5种药物响应拆分、3种时间点、3种跨物种设置等），总计超过20个不同的评估条件。消融实验包括ATAC指导尺度（5个水平）、组件消融（4种组合）、条件编码策略比较等。
- **充分性与公平性**：实验覆盖了遗传、化学、时间、跨物种、多组学整合等多种扰动情境，对比方法多样，评估指标同时考虑全局和响应焦点。使用了公开标准数据集，测试集拆分符合“留出”原则。但论文为预印本，未经同行评审；部分任务仅报告均值（未给出标准差）。此外，BaiZe在每个基准上分别训练，未展示单一联合预训练模型的表现。总体实验设计较为充分和客观，但仍缺乏不确定性量化和更广泛的扰动类型验证。

### 6. 论文的主要结论与发现

- BaiZe在多种未见条件下有效恢复主要转录响应程序：在未见细胞状态、未见基因扰动、多基因组合、药物结构和剂量、时间阶段、跨物种转移等任务中均优于或持平于现有方法。
- 整合ATAC-seq情境可提升部分时间预测和基因响应预测性能，并通过峰级归因提供候选调控证据（如SMARCA4扰动下NRG1-ERBB4轴的校正）。
- 跨物种预测中，人类→小鼠的零样本迁移可行，少量小鼠扰动数据（5%–10%）即可显著校正系统差异，恢复状态特异响应。
- 预测转录组可投影到形态学空间，产生多通道候选表型图像（尽管缺乏配对实验验证）。
- 通过SNP提示模拟HIF1A扰动，预测的下游缺氧/糖酵解基因响应趋势与实验一致。
- BaiZe-Agent提供自然语言查询，降低了复杂扰动结果探索的技术门槛。

### 7. 优点：方法或实验设计上的亮点

- **统一框架**：将遗传、化学、时间、多组学、跨物种等异构扰动统一表示为条件状态转移，避免为每种扰动类型单独建模。
- **残差扩散机制**：分离确定性主效应和随机残差，既保证预测效率又保留生成式灵活性。
- **多视图条件输入**：自然融合RNA、ATAC、化学指纹等异构数据，支持可选的调控情境和归因分析。
- **响应聚焦评估**：采用Top20 Delta Pearson、ODR等指标，避免全转录组相似性掩盖关键基因错误。
- **可解释性与交互性**：峰级归因、BaiZe-Agent查询界面使模型预测具有可追溯性和可操作性。
- **跨物种能力**：零样本和少样本迁移设计务实，有效利用源物种知识并适配目标物种。
- **应用链完整**：从预测到归因、表型投影、语言查询，形成了一个端到端的假设生成工具。

### 8. 不足与局限

- **训练方式**：BaiZe在每个基准上单独训练，未展示一个跨所有扰动类型的统一预训练模型，限制了其作为基础模型的通用性。
- **计算资源不透明**：缺少GPU型号、数量、训练时长等关键信息，影响可复现性和资源需求评估。
- **预测不确定性**：未提供单细胞水平的不确定性估计（如置信区间），限制了在高风险场景（如临床决策）中的应用。
- **跨物种局限**：仅使用一对一直系同源基因，物种特异性基因和调控元件未被建模，可能遗漏重要响应。
- **形态学投影缺乏验证**：投影图像基于无配对显微图像的模型生成，仅为候选假设，不能作为真实表型的替代。
- **归因为模型相关性**：ATAC峰级归因度量的是模型依赖度，并非因果峰-基因调控关系，需要实验验证。
- **BaiZe-Agent不执行新推理**：仅支持预设结果的查询，无法进行新扰动模拟或统计测试，功能范围有限。
- **实验覆盖**：未测试更大规模的基因组合（如超过3个基因）、更复杂的扰动类型（如环境扰动）、更远的跨物种（如斑马鱼）；部分任务（如MCF7药物响应）性能显著下降，表明对细胞背景泛化仍有限。
- **性能敏感**：对控制匹配、基因空间对齐、预处理流程敏感，且点估计未报告标准差，可能低估同源数据变异性。

（完）
