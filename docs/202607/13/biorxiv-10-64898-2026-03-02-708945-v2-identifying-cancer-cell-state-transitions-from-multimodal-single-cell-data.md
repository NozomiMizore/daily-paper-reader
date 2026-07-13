---
title: Identifying cancer cell-state transitions from multimodal single-cell data
title_zh: 从多模态单细胞数据识别癌细胞状态转变
authors: "Baselli, G. A., Alekseenko, A., Liano-Pons, J., Sinanis, L., Rrapaj, E., Arsenian-Henriksson, M., Pelechano, V."
date: 2026-07-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.02.708945v2.full.pdf"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 利用mRNA与蛋白延迟捕捉单细胞状态转变
tldr: 癌细胞表型可塑性导致治疗抗性，但状态转变的瞬时性使分子驱动因素难以定义。本研究利用单细胞多模态数据中mRNA与蛋白积累的时间延迟，直接捕获转变中的细胞。在K562白血病模型中鉴定出转变细胞，发现细胞周期进程和线粒体重塑与可塑性相关，CRISPR筛选验证关键调控因子。构建的转变相关评分可预测慢性髓系白血病治疗反应，并在31种肿瘤中具有预后价值，空间转录组学揭示实体瘤可塑性热点。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-02-708945-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1714, \"height\": 1982, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-02-708945-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1775, \"height\": 2509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-02-708945-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1744, \"height\": 2380, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-02-708945-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1743, \"height\": 2207, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-02-708945-v2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1639, \"height\": 1932, \"label\": \"Figure\"}]"
motivation: 癌细胞表型可塑性驱动治疗抗性，但转变的瞬时特征使分子机制难以定义。
method: 利用单细胞多模态数据中mRNA和蛋白积累的时间延迟，识别正在表型转变的细胞。
result: 在K562模型中鉴定转变细胞，发现细胞周期和线粒体稳态基因调控可塑性，CRISPR验证关键调控因子。
conclusion: 框架揭示癌症可塑性的分子基础，并能在多种肿瘤中定量评估可塑性，具有预后和治疗预测价值。
---

## 摘要
表型可塑性使癌细胞能够逃逸治疗，然而状态转变的瞬时性使得其分子驱动因素难以界定。我们在此提出一个单细胞框架，利用mRNA与蛋白质积累之间的时间延迟来直接捕获经历表型转换的细胞。我们展示，在多模态单细胞数据中，转录本与蛋白质积累之间的分化相关延迟可通过不一致的mRNA和表面蛋白水平检测到。将该策略应用于K562白血病模型（该模型在分化的CD24-和祖细胞样CD24+状态之间交替），我们识别出转变中的细胞，并推导出一个连接细胞周期进程和线粒体重塑与可塑性的转录特征。全基因组CRISPR筛选证实了可塑性的关键调控因子，包括BCR-ABL1和线粒体稳态基因。我们将转变相关程序总结为一个评分，该评分可预测慢性粒细胞白血病中的伊马替尼响应，在急性髓系白血病中进行生存分层，并在31种TCGA肿瘤类型中保持预后价值。空间转录组学揭示了实体瘤中局部的可塑性热点。总之，该框架揭示了癌症可塑性的分子基础，并实现了其在肿瘤中的量化。

## Abstract
Phenotypic plasticity allows cancer cells to evade therapy, yet the transient nature of state transitions has made their molecular drivers difficult to define. Here, we present a single-cell framework that leverages the temporal delays between mRNA and protein accumulation to directly capture cells undergoing phenotypic switching. We show that differentiation-associated delays between transcript and protein accumulation are detectable in multimodal single-cell data as discordant mRNA and surface-protein levels. Applying this strategy to the K562 leukemia model, which alternates between differentiated CD24- and progenitor-like CD24+ states, we identify transitioning cells and derive a transcriptional signature linking cell-cycle progression and mitochondrial remodeling to plasticity. Genome-wide CRISPR screening confirms key regulators of plasticity, including BCR-ABL1 and mitochondrial homeostasis genes. We summarize the transition-associated program into a score that predicts imatinib response in chronic myeloid leukemia, stratifies survival in acute myeloid leukemia, and retains prognostic value across 31 TCGA tumor types. Spatial transcriptomics reveals localized plasticity hotspots in solid tumors. Together, this framework exposes the molecular basis of cancer plasticity and enables its quantification across tumors.

---

## 论文详细总结（自动生成）

好的，作为资深学术论文分析助手，我将根据您提供的论文内容，对其进行结构化、深入、客观的总结。

## 论文内容分析总结

### 1. 论文的核心问题与整体含义（研究动机和背景）

*   **核心问题**：癌细胞通过**表型可塑性**（phenotypic plasticity）在不同状态间动态转换，这种瞬时性的状态转变是导致**治疗抵抗**和**疾病进展**的关键因素，但其分子驱动机制和特征极难被捕捉和界定。
*   **动机**：传统的单细胞分析（如scRNA-seq）仅提供静态快照，难以直接研究动态的状态转换。依赖RNA速率等推断性方法存在假设限制和准确性挑战。因此，迫切需要一种能直接鉴定并解析正在发生状态转换的细胞的方法。
*   **整体含义**：本论文构建了一个基于单细胞多模态数据（同时测量mRNA和蛋白）的分析框架，成功捕获了处于状态转变中的细胞，并识别出与细胞周期、线粒体重塑相关的可塑性转录程序。该程序具有广泛的预后价值，揭示了癌症可塑性的保守分子基础。

### 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

*   **核心思想**：利用**mRNA与蛋白质在积累动力学上的时间延迟**。当细胞转变时，关键标记物的mRNA水平会先于其相应的表面蛋白水平发生变化。因此，在单细胞多模态数据（如CITE-seq）中，若某个细胞的标记物mRNA与蛋白表达水平不一致（如高mRNA但低蛋白，或低mRNA但高蛋白），则表明该细胞正处于**活跃转变中**。
*   **关键技术细节**：
    1.  **模型与分类**：通过线性回归模型，根据每个细胞的标记物（如CD24）mRNA表达量预测其期望蛋白水平。将实际蛋白水平和预测蛋白水平分别与阈值比较，得到两个二分类状态。二者一致则判定为稳定状态（CD24+或CD24-），不一致则判定为转变状态（-/+ 或 +/-）。
    2.  **去除干扰**：为排除不同分化轨迹（lineage）的干扰，分析前会去除属于其他分支（如CD44+）的细胞。
    3.  **可塑性评分的构建**：将转变相关基因（transition-associated genes）的表达进行排名偏差（rank-deviation）计算，形成一个单一的、无监督的“可塑性评分”（plasticity score），用于在大量患者样本中量化该转录程序。
    4.  **功能验证**：采用**全基因组CRISPR敲除筛选**，结合两步分选策略，富集状态转变动力学发生改变的细胞，从而鉴定出调控可塑性的关键基因。
*   **算法流程（文字描述）**：
    1.  **输入**：多模态单细胞数据（CITE-seq），包含同一细胞的mRNA（如CD24）和表面蛋白（如CD24）表达。
    2.  **标记物选择**：选择一个在两种细胞状态间表达差异显著的关键表面蛋白标记物（如K562模型中的CD24）。
    3.  **转变细胞鉴定**：
        *   基于mRNA水平预测蛋白水平。
        *   比较实际蛋白水平和预测蛋白水平（或mRNA水平）的一致性。
        *   将不一致的细胞初步标记为转变候选细胞。
    4.  **特征分析**：对鉴定出的转变细胞进行差异表达分析、通路富集分析和轨迹推断。
    5.  **核心程序提取**：提取转变细胞共同上调/下调的基因集作为“**转变相关转录程序**”。
    6.  **评分量化**：将该基因集转换为一个**可塑性评分**，用于分析大型临床队列和空间转录组学数据。
    7.  **功能筛选**：将CRISPR筛选与转变分选策略结合，以识别驱动可塑性的遗传因素。

### 3. 实验设计：使用的数据集、基准测试与对比方法

*   **使用的数据集/场景**：
    1.  **模型建立**：**K562慢性粒细胞白血病（CML）细胞系**，其可在分化CD24-状态和祖细胞样CD24+状态间切换。
    2.  **方法通用性验证**：**公共骨髓CITE-seq数据**，用于追踪单核细胞分化轨迹。
    3.  **功能验证**：**全基因组CRISPR-KO筛选**，在K562系统上进行。
    4.  **临床应用**：
        *   **CML患者队列** (N=96, GSE130404): 用于评估可塑性评分预测伊马替尼治疗效果的能力。
        *   **三个独立的AML患者队列** (Beat AML, TCGA-LAML, TARGET-AML): 用于评估评分对生存预后的预测能力。
        *   **泛癌分析**：31个非血液肿瘤的TCGA数据集 (N=8,873): 用于评估评分的普适性。
        *   **空间转录组学**：**肝细胞癌（HCC）** 和**肾透明细胞癌（ccRCC）** 的肿瘤切片数据，用于观察可塑性的空间分布。
*   **基准测试（Benchmark）**：论文**没有**直接对比其他识别状态转变的方法（如RNA velocity），而是通过**多维度实验验证**（如体外分化实验、CRISPR功能筛选、大规模临床队列预后分析）来证明其框架的有效性和临床相关性。
*   **对比方法**：论文未涉及与其他方法的系统性对比。其方法新颖性在于直接利用mRNA-蛋白动力学的差异。

### 4. 资源与算力（GPU、模型、时长）

*   论文的文本内容**未明确说明**使用的GPU型号、数量以及模型训练的具体时长。仅提及使用的计算和存储资源（如UPPMAX计算基础设施）。
*   **可推断的资源**：单细胞测序数据的处理与分析（CellRanger, Seurat），差异表达分析（DESeq2）以及大规模临床队列的评分计算通常对GPU要求不高，但对内存和CPU有较高要求。全基因组CRISPR筛选数据的分析同样如此。论文主要依赖**高性能计算集群**而非特定的深度学习模型。

### 5. 实验数量与充分性

*   **实验数量**：实验种类丰富且全面：
    *   **方法论验证**：1个核心模型（K562）+ 1个验证模型（单核细胞分化）。
    *   **功能验证**：1个大规模CRISPR筛选实验。
    *   **临床应用**：1个CML + 3个AML + 31个TCGA肿瘤类型 + 2个空间转录组学数据集（HCC, ccRCC）。
*   **充分性与客观性**：
    *   **充分**：论文的论证链条完整，从**体外细胞系模型（发现机制）-> 功能基因组学筛选（验证机制）-> 大规模临床队列（检验普适性）-> 空间转录组学（观察空间特征）**，逻辑严谨，层层递进。
    *   **客观**：
        *   所有分析均采用公开可及的统计和生物信息学方法（如DESeq2, Seurat, Cox回归）。
        *   临床分析均进行了年龄校正，且在某些分析中考虑了TCGA对特定肿瘤类型数据使用的建议和警告。
        *   在泛癌分析中强调了少数肿瘤类型中存在相反的预后关联，显示了结果的复杂性和客观性。
    *   **不足**：论文**没有消融实验**来证明其方法学选择（如线性回归模型、特定的转变细胞分界阈值）的绝对最优性。

### 6. 论文的主要结论与发现

1.  **新方法可行**：利用mRNA-蛋白表达的不一致性，可以直接从多模态单细胞数据中识别正在发生状态转变的细胞。
2.  **可塑性的机制**：在K562模型中，状态转变与**细胞周期进程**（尤其是G1/S期切换）和**线粒体稳态**（线粒体功能重塑）密切相关，且由**BCR-ABL1**信号转导驱动。
3.  **核心调控因子**：全基因组CRISPR筛选证实了**线粒体氧化磷酸化通路**和**BCR-ABL1**信号通路是调节可塑性的关键遗传因子。
4.  **临床价值**：
    *   **CML**：可塑性评分可**预测伊马替尼**治疗早期分子应答失败。
    *   **AML**：高可塑性评分与**更差的总生存期**独立相关。
    *   **泛癌**：该评分在31种实体瘤中广泛与**更差的总生存期、无进展间隔**等预后指标显著相关。
5.  **空间定位**：在实体瘤中，高可塑性区域呈**局部热点分布**，并与增殖、氧化磷酸化和细胞器分裂等功能程序相关，这提示了可塑性在肿瘤微环境中的空间组织。

### 7. 优点：方法或实验设计上的亮点

*   **方法论创新性高**：提出了一种利用了多模态数据内在动力学信息（mRNA-蛋白延迟）的全新视角来鉴定转变细胞，概念简洁而有效。
*   **逻辑链完整**：从机制发现、功能验证到临床转化，形成了一个“**机制-功能-预后**”的完整叙事闭环，极大地增强了研究结论的说服力。
*   **验证范围广泛**：不仅在细胞系中验证机制，还在多个独立的大规模临床队列（CML, AML, 31种泛癌）和空间转录组学数据中验证了其普适性和临床意义，显示了该框架的强大实用价值。
*   **避免了过度拟合**：通过无监督的泛癌分析，展示了结果的一致性与差异性（如某些肿瘤中相反关联），体现了数据分析的客观性和结果报告的诚实性。
*   **将复杂的生物学现象转化为可计算的定量评分**，利于临床推广和应用。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等

*   **方法鲁棒性**：该方法高度依赖于一个关键的、在状态间有显著表达差异的**表面蛋白标记物**。在没有这种理想标记物的复杂系统中，其应用可能会受到限制。
*   **实验验证的潜在偏差**：CRISPR筛选和临床分析均依赖于通过CD24定义的K562模型，CD24在此模型中既是可塑性的标志物，也是状态分类的依据。这可能导致一定程度的循环论证（除非模型能独立于CD24验证）。
*   **临床关联的局限性**：
    *   可塑性评分与临床预后的关联性在多数肿瘤中显著，但作为单变量预测指标，其效应量（Hazard Ratio）在一些肿瘤中可能有限（论文未系统量化其相对于其他已知预后因素的增量价值）。
    *   论文中提到的“TLR和细胞因子信号”等通路在CRISPR筛选中与可塑性相关，但在临床部分讨论较少，机制深度有提升空间。
*   **应用限制**：该方法目前主要适用于**血液系统肿瘤**（如CML, AML）和拥有明确状态标记物的系统。对于实体瘤中更复杂的表现状态和异质性，其通用性和效率尚需更多验证。
*   **计算与实验依赖性**：该方法依赖**高质量的多模态单细胞数据（CITE-seq）**，对于只有单模态数据的旧有数据集，该方法无法直接应用。

（完）
