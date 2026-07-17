---
title: "Mapping Tumor-Microenvironment dependencies with TMEformer: A spatial foundation framework enabling in silico perturbation"
title_zh: 利用TMEformer绘制肿瘤-微环境依赖关系：一个支持计算扰动的空间基础框架
authors: "Chen, S., Zhu, G., Yang, L., Wei, X., Li, S., Liu, P., Chen, Q., Zhang, Z., Liu, D., Tang, Y., Xu, G., Zhou, M., Luo, J., Huang, L., Chen, B., Ou, S., Jiang, J."
date: 2026-07-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.17.725770v2.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 利用空间转录组实现肿瘤微环境中的计算机模拟扰动
tldr: 肿瘤进展高度依赖空间微环境，但现有虚拟扰动模型多忽略空间背景。本文提出TMEformer框架，利用高分辨率空间转录组数据，显式整合空间架构，联合建模肿瘤内在程序与局部微环境信号。在多种肿瘤数据上验证，TMEformer的虚拟扰动准确捕获细胞功能依赖，优于大规模预训练模型。系统扰动分析优先发现肿瘤内转录因子和微环境衍生配体，且空间嵌入改善肿瘤细胞分层，建立了空间耦合、可扰动的肿瘤生态系统通用框架。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-05-17-725770-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1528, \"height\": 1535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-05-17-725770-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1538, \"height\": 2212, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-05-17-725770-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1532, \"height\": 1813, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-05-17-725770-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1498, \"height\": 2059, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-05-17-725770-v2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1518, \"height\": 1991, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-05-17-725770-v2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1529, \"height\": 2126, \"label\": \"Figure\"}]"
motivation: 现有虚拟扰动模型忽略空间上下文，无法准确捕捉肿瘤-微环境的功能依赖关系。
method: 提出TMEformer，显式整合空间架构，联合建模肿瘤细胞程序与微环境信号，实现空间感知的虚拟扰动。
result: 在空间转录组数据上，TMEformer优于预训练基线，虚拟扰动揭示关键转录因子和配体，空间嵌入改善肿瘤细胞分层。
conclusion: TMEformer建立了空间耦合、可扰动的肿瘤生态系统通用框架。
---

## 摘要
尽管空间背景在驱动肿瘤进展中起着根本性作用，但目前大多数用于虚拟扰动的计算模型在很大程度上忽视了其重要性。在此，我们介绍TMEformer，一种肿瘤微环境感知的深度学习框架，它利用高分辨率空间转录组学，通过明确纳入空间架构，联合建模内在肿瘤细胞程序与局部微环境信号。经过跨不同肿瘤空间转录组队列验证，TMEformer能够实现捕获局部细胞生态系统内功能依赖关系的虚拟扰动。尽管仅在癌症特异性空间数据集上训练，TMEformer在捕捉关键肿瘤转变（包括谱系可塑性和治疗耐药性的出现）方面优于在大型语料库上预训练的基线模型。系统性扰动分析优先考虑驱动疾病进展的肿瘤内在转录因子和TME来源配体，恢复了已知调控因子并揭示了新候选因子。此外，TME衍生的嵌入改善了肿瘤细胞的空间分层，并与病理结构更紧密对齐。总之，TMEformer建立了一个将肿瘤建模为空间耦合、可扰动生态系统的一般框架。

## Abstract
Despite the fundamental role of spatial context in driving tumor progression, most current computational models for virtual perturbation have largely overlooked its importance. Here, we introduce TMEformer, a tumor microenvironment-aware deep learning framework that leverages high-resolution spatial transcriptomics to jointly model intrinsic tumor cell programs and local microenvironmental signals by explicitly incorporating spatial architecture. Validated across diverse tumor spatial transcriptomic cohorts, TMEformer enables virtual perturbations that capture functional dependencies within local cellular ecosystems. Despite being trained on cancer-specific spatial datasets, TMEformer outperforms baseline models pretrained on large-scale corpora in capturing key tumor transitions, including lineage plasticity and the emergence of therapy resistance. Systematic perturbation analyses prioritize tumor-intrinsic transcription factors and TME-derived ligands that drive disease progression, recovering established regulators and revealing novel candidates. Furthermore, TME-derived embeddings improve the spatial stratification of tumor cells and align more closely with pathological architecture. Together, TMEformer establishes a general framework for modeling tumors as spatially coupled, perturbable ecosystems.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：肿瘤进展高度依赖于空间组织化的肿瘤微环境（TME），但现有大多数计算模型（如单细胞基础模型）进行虚拟扰动时，将细胞视为孤立实体，忽略了空间上下文。这导致无法准确模拟肿瘤细胞与微环境之间的功能依赖关系，如谱系可塑性和治疗耐药性。
- **整体含义**：需要一种能够显式整合空间架构的深度学习框架，将肿瘤建模为空间耦合、可扰动的生态系统，从而实现对肿瘤-微环境相互作用的系统性因果推断。

## 2. 方法论
- **核心思想**：提出TMEformer，一个TME感知的空间转换器框架。通过集成空间转录组学数据，联合学习肿瘤内在转录程序与局部微环境信号。
- **关键技术细节**：
  - **TME-CEM（TME上下文编码模块）**：对每个肿瘤细胞，选择其空间最近邻的k个TME细胞，将每个TME细胞的转录组嵌入（来自预训练单细胞模型）与可学习细胞类型嵌入求和；通过两层注意力机制（自注意力 + 基于可学习查询向量的注意力池化）聚合为单个上下文token；然后以固定权重（α=0.2）与肿瘤细胞嵌入融合，作为Transformer编码器的输入。
  - **训练**：在自产Xenium-5K前列腺癌数据上，以掩码基因预测为目标，对GF_CL模型（Geneformer继续训练版）进行持续训练，同时融入TME上下文。基准模型GF_PCa为相同训练但不含TME信息。
  - **三种ISP策略**：
    1. **目标排名扰动**：修改肿瘤细胞内目标基因的表达排名（Overexpression/KD）。
    2. **TME组成扰动**：通过重采样改变邻居细胞中特定TME细胞类型的比例。
    3. **TME排名扰动**：在特定TME细胞类型中上调或下调目标基因（两步：增加表达细胞比例 + 置顶表达排名）。
  - **两种评分方法**：
    - **端点分数**：取极端扰动（排名第一或最后）下的嵌入变化。
    - **面积分数**：沿排名逐步扰动，计算轨迹曲线下的面积，更稳健地评估累积效应。
- **预测任务**：
  - **状态嵌入相似度分析**（零样本）：计算扰动后细胞嵌入与目标状态（如CRPC）参考嵌入的余弦相似度变化。
  - **标记基因表达预测**（需微调）：添加回归头预测掩码标记基因的表达值，比较扰动前后变化。

## 3. 实验设计
- **数据集**：
  - **自产数据集**：8个前列腺癌标本（4个初治、3个ADT后、1个CRPC），使用Xenium-5K平台 + 自定义51个PCa基因探针，共5,051个基因，约150万细胞。
  - **公共数据集**：10x Genomics Xenium平台的前列腺癌、乳腺癌、卵巢癌样本；Vizgen MERFISH平台的前列腺癌样本；小鼠scRNA-seq（Gao数据集）；TCGA-PRAD和MSKCC队列的bulk RNA-seq。
- **基准方法**：
  - **基线模型**：Geneformer预训练版（GF_PR）、癌症scRNA-seq继续训练版（GF_CL）、仅在PCa空间数据上训练但无TME信息的版本（GF_PCa）。
  - **聚类与分类对比**：scVI、PCA、Nicheformer、CellPLM、STACK、随机嵌入。
- **实验场景与任务**：
  - NEPC标记基因预测：SOX2 OE、ASCL1 OE、PTEN+RB1+TP53 KD、LIF+LIFR OE，以及15个L-R对；计算整体delta-exp分数。
  - CRPC状态转变：模拟AR信号、IL-12B/IL-23A OE、SPP1 OE等，评估嵌入相似度变化。
  - TF筛选：495个TFs，三种过程（神经内分泌分化、去势抵抗、Gleason升级），使用面积分数。
  - TME组成和配体筛选：系统扰动TME细胞类型比例和特定配体。
  - TME嵌入聚类：与EXP-emb对比，计算TME聚类指数和Gleason一致性指数。
  - Gleason分类：跨样本验证，多个对比方法（P205, P018, P020三个样本）。
  - 跨平台/癌种泛化：Xenium、MERFISH、乳腺癌、卵巢癌的CD44表达预测。

## 4. 资源与算力
- 论文中未明确说明使用的GPU型号、数量及训练时长。训练配置提到：batch size = 6，梯度累积4步，1个epoch，学习率0.0001，AdamW优化器，余弦学习率调度。但未提及具体硬件资源。**需指出此信息缺失**。

## 5. 实验数量与充分性
- **实验数量**：非常丰富。包括：
  - 4种目标扰动任务的NEPC标记预测；15个L-R对的系统分析；与基线模型在所有任务上的对比。
  - TF全量筛选（495个）；CRPC、Gleason升级筛选。
  - TME组成扰动（5种细胞类型）和配体筛选（618个候选，57个显著）。
  - 消融实验（TME-CEM组件、邻居选择策略、注意力聚合层等，见补充表2）。
  - 聚类对比（3个样本；两个指数）；分类对比（5种嵌入方法 + 随机，两个性能指标）。
  - 跨平台（Xenium vs. MERFISH）、跨癌种（前列腺、乳腺、卵巢）的验证。
- **充分性**：实验设计系统，消融和基准对比客观。每个任务均使用统计检验（单侧Wilcoxon、BH校正），并构建随机背景分布。但部分分析仅基于自产8个样本，样本量有限，可能影响泛化性。跨癌种验证仅用单个公共数据集，需更多验证。

## 6. 主要结论与发现
- TMEformer在预测NEPC标记变化和CRPC状态转变方面显著优于所有Geneformer基线模型，尤其在涉及微环境信号的任务中（如L-R对、TME组成扰动）。
- 通过系统TF筛选，恢复了已知驱动因子（如SOX2、ASCL1、AR相关TF），并发现新候选（如TWIST1与Gleason升级相关）。
- TME组成扰动揭示：髓系细胞（尤其是免疫抑制表型）促进NEPC；T细胞和成纤维细胞促进CRPC，而M1样髓系细胞可能具有保护作用。
- TME嵌入（TME-emb）相比纯转录组嵌入（EXP-emb）在空间聚类和Gleason分类上表现更好。
- 模型泛化到不同空间平台和癌种，显示保守的调控机制。

## 7. 优点
- **创新性**：首次将空间架构显式引入Transformer用于虚拟扰动，超越了传统的细胞孤立建模。
- **多样化的扰动策略**：同时支持肿瘤内在基因扰动、TME组成扰动和TME内基因扰动，覆盖多层级因果推断。
- **全面验证**：在多个任务、多个数据集、多个癌种上系统评估，消融实验充分。
- **开放资源**：提供了在线web平台（http://www.pradcellatlas.com）用于扰动预测和可视化，代码在GitHub开源。
- **临床相关性**：识别出TWIST1、BTLA、MRC1等潜在临床相关靶点，并与公开队列（TCGA、MSKCC）生存数据验证。

## 8. 不足与局限
- **空间邻域建模简化**：依赖预定义k个最近邻和固定权重，可能无法捕获长距离或动态相互作；使用固定k=256，未评估不同k的影响。
- **需要实验验证**：所有预测均为in silico，新发现（如TWIST1、BTLA）缺乏湿实验室验证，存在假阳性风险。
- **仅包含转录组**：未整合蛋白组、染色质可及性等其他空间模态，信息维度有限。
- **样本量有限**：自产仅8个样本，且大部分为前列腺癌，跨癌种仅用单个公共数据集，泛化性需更多数据支撑。
- **训练配置不透明**：未报告计算资源（GPU型号、数量、训练时长），影响可复现性。
- **微调依赖标记基因**：在标记表达预测任务中需微调，可能引入过拟合风险；零样本相似度分析虽好，但仅适用于有参考状态的情况。

（完）
