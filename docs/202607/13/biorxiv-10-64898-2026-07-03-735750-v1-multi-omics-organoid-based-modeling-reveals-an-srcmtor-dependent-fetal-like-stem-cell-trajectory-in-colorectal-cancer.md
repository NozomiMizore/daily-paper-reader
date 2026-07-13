---
title: "Multi-omics, organoid-based modeling reveals an SRC/mTOR-dependent fetal-like stem cell trajectory in colorectal cancer"
title_zh: 基于多组学和类器官的建模揭示结直肠癌中SRC/mTOR依赖的胎儿样干细胞轨迹
authors: "Mulholland, T., Aybey, B., Li, Z., Schwarzmüller, L., Rindtorff, N., Tondo, L., Sui, P., Karabati, E., Albrecht, P., Riedesser, J. E., Petersen, Y., Miersch, T., Valentini, E., Burgermeister, E., Zhan, T., Dreikhausen, L., Schulte, N., Belle, S., Wiemann, S., Boutros, M., Ebert, M. P., Betge, J."
date: 2026-07-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.03.735750v1.full.pdf"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 基于类器官的多组学建模预测药物敏感性，涉及细胞状态和扰动响应
tldr: 结直肠癌干细胞存在连续景观，从成体干细胞向胎儿样再生状态转变。本研究利用64个患者来源类器官进行多组学分析和62-140种药物筛选，结合公开转录组数据，鉴定出PI3K/mTOR依赖的胎儿样干细胞轨迹。该状态与mRNA翻译抑制和SRC信号上调相关，预后不良。工作通过功能扰动建模揭示了干细胞状态调控机制，为治疗靶向提供新方向。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-735750-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1552, \"height\": 2152, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-735750-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1710, \"height\": 1108, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-735750-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1709, \"height\": 1584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-735750-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1468, \"height\": 2151, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-735750-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1665, \"height\": 2123, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-735750-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1716, \"height\": 1609, \"label\": \"Figure\"}]"
motivation: 单细胞图谱描述了结直肠癌中多种干细胞状态，但其发育轨迹及功能机制，尤其是与药物敏感性的关系尚不清楚。
method: 建立64个微卫星稳定结直肠癌患者类器官，整合转录组、基因组、药物筛选数据，并结合公开数据集及单细胞转录组进行多组学建模。
result: 发现连续干细胞景观中胎儿样再生状态依赖于PI3K/mTOR，且与mRNA翻译抑制和SRC信号上调相关，该状态预后差。
conclusion: 通过类器官功能扰动分析建立了干细胞状态调控机制模型，鉴定了SRC/mTOR依赖的再生状态，为未来治疗靶向提供基础。
---

## 摘要
背景：单细胞图谱已描述了结直肠癌（CRC）中多种干细胞状态，然而，这些状态的总体轨迹及其潜在功能机制，包括它们与药物敏感性的相关性，仍需进一步理解。

方法：我们从微卫星稳定的结直肠癌中建立了64个患者来源的类器官，对其转录组和基因组进行了表征，并使用62-140种临床批准药物进行了药物筛选。我们还分析了来自患者来源类器官（来自三个独立数据集的72名患者）、TCGA-CRC数据（466名患者）以及肿瘤活检单细胞转录组（来自六个独立队列的123,000个细胞）的额外已发表转录组数据，以建立CRC干细胞的功能和分子图谱。我们通过基于质谱的蛋白质组学、大规模激酶抑制试验和免疫荧光分析进行了机制性后续分析。

结果：我们发现CRC干细胞呈现一个连续图谱，其特征是不同的发育程序：从成体干细胞到胎儿样再生状态以及分化程序之间的转换。通过大规模药物扰动和多组学建模，我们识别出一个以PI3K/mTOR依赖性为特征的再生/胎儿样干细胞轨迹。我们发现这种识别的发育轴在类器官、临床以及单细胞数据中保守，且胎儿样PI3K/mTOR依赖状态与不良临床预后相关。机制上，PI3K/mTOR脆弱性由于mRNA翻译受抑制而与适应性能力缺乏相关，并与上调的SRC信号网络相关。

结论：我们的工作通过结合类器官中的功能性扰动分析，超越了分子CRC图谱的范畴。这使得干细胞状态调控的机制建模成为可能，并识别出CRC中一个SRC/mTOR依赖的再生状态，这可能为未来改进治疗靶向提供思路。

## Abstract
BackgroundSingle-cell atlases have described diverse stem cell states in colorectal cancer (CRC), however, the overarching trajectories of those states and the underlying functional mechanisms, including their relevance for drug sensitivity, need better understanding.

MethodsWe established 64 patient-derived organoids from microsatellite-stable colorectal cancers, characterized their transcriptomes and genomes, and performed drug screening with 62-140 clinically approved substances. We analyzed additional published transcriptome data from patient-derived organoids (72 patients from three independent datasets), TCGA-CRC data (466 patients), and single-cell transcriptomes of tumor biopsies (123,000 cells from six independent cohorts) to establish a functional and molecular landscape of CRC stem cells. We performed mechanistic follow-up analyses by mass-spectrometry-based proteomics, large-scale kinase inhibition assays and immunofluorescence analyses.

ResultsWe find a continuous landscape of CRC stem cells that is characterized by distinct developmental programs: adult stem cell-to fetal-like regenerative states and transition between differentiation programs. By large-scale drug perturbations and multi-omics modeling, we identify a regenerative/fetal-like stem cell trajectory characterized by PI3K/mTOR dependency. We find the identified developmental axes conserved in organoid, clinical, as well as single-cell data, and the fetal-like PI3K/mTOR-dependent state to be associated with poor clinical prognosis. Mechanistically, PI3K/mTOR vulnerability is linked to a lack of adaptive capability due to suppressed mRNA translation and associated with an upregulated SRC signaling network.

ConclusionsOur work moves beyond a molecular CRC landscape by combined functional perturbation analyses in organoids. This enables mechanistic modeling of stem cell state regulation and identifies an SRC/mTOR-dependent regenerative state in CRC, which might allow improved therapeutic targeting in the future.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：结直肠癌（CRC）中存在多种干细胞状态（成体干细胞、胎儿样/再生干细胞等），但这些状态的**连续发育轨迹**、**潜在功能机制**以及它们与**药物敏感性**的关系尚不清楚。现有CRC分子分型（如CMS、CRIS、iCMS）多为离散分类，难以捕捉动态的细胞状态转化，且缺乏治疗指导价值。
- **整体含义**：本研究旨在通过大规模患者来源类器官（PDO）的多组学与功能扰动分析，系统描绘CRC干细胞的**连续景观**，识别特定状态相关的**可靶向依赖性**，从而为精确治疗提供新策略。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用PDO作为模型系统，整合转录组、基因组、药物响应等多模态数据，通过**多组学因子分析（MOFA）** 构建低维潜在因子，关联基因表达与药物敏感性，进而鉴定出特定干细胞状态下的分子依赖性。
- **关键技术细节**：
  - **PDO建立与培养**：从64位微卫星稳定（MSS）CRC患者获取活检组织，培养132个PDO样本，覆盖临床多样性。
  - **转录组分析**：采用Affymetrix微阵列和RNA-seq获得表达谱，使用**RMA标准化**，针对性别进行批次校正。
  - **基因组分析**：通过全外显子测序或靶向扩增子测序鉴定突变（APC、TP53、KRAS等）。
  - **药物筛选**：两个子队列分别使用62种和140种临床批准药物，在384孔板中进行5点浓度梯度筛选，以CellTiter-Glo测定活力，计算DMSO归一化AUC值。
  - **扩散图（Diffusion Map）**：基于PCA负载基因集构建，推断伪时间，展示连续轨迹。
  - **MOFA2**：整合基因表达（top 10%高变异基因）、药物响应（AUC）和突变状态（频率>3个样本的基因），设置7个潜在因子，使用高斯/伯努利似然，最终收敛为6个因子。
  - **蛋白质组学与磷酸化蛋白质组学**：采用DIA质谱，数据经VSN标准化；通过磷酸化位点推断激酶活性（decoupleR+OmniPath）。
  - **激酶抑制剂筛选**：277种化合物在8个代表性PDO中进行，以Cohen's d评估选择性。

## 3. 实验设计：数据集、场景、基准与对比方法

- **使用的数据集**：
  1. **自建PDO数据集**：64个患者（132样本）的MSS CRC PDO。分为发现队列（CRC1: 42 PDOs, 52药物）和验证队列（CRC2: 22 PDOs, 140药物）。
  2. **外部PDO数据集**：GSE64392、GSE74843、GSE128213（共78个样本），整合后批次校正。
  3. **TCGA CRC数据**：COAD/READ共466例MSS患者，获取RNA-seq（log2(TPM+1)）和临床生存数据。
  4. **单细胞数据集**：6个独立队列（123,000个恶性上皮细胞），来自Chu等人整合的CRC图谱。
- **基准与对比**：没有直接对比其他预测模型，主要通过以下方式验证：
  - 将扩散图与随机基因集对比（排列检验）证明轨迹非随机。
  - 在外部PDO、TCGA、单细胞数据中**重现**景观和FMD签名分布。
  - 与已有胎儿/再生长签名（如Mustata, Gregorieff, Yui, Ayyaz等）比较重叠。
  - 与CMS/CRIS/iCMS分类对比相关性。

## 4. 资源与算力

- **文中未明确说明**：未提及GPU型号、数量或训练时长。分析主要基于R语言（如affy, limma, destiny, MOFA2, clusterProfiler等）在本地或服务器上完成。蛋白质组学和RNA-seq的原始数据处理依赖DKFZ核心设施（NGS、蛋白质组学、微阵列中心）。**无算力细节披露**。

## 5. 实验数量与充分性

- **实验数量**：
  - 主分析：64个患者PDO的转录组、基因组、药物响应（62-140种药物）的全谱分析。
  - MOFA建模：发现队列42 PDOs×52药物，验证队列22 PDOs×140药物。
  - 机制研究：选取8个PDO（4敏感+4抵抗）进行RNA-seq、蛋白质组、磷酸化蛋白质组、激酶抑制剂筛选（277种化合物）。
  - 免疫荧光：2个代表性PDO对ANXA1/OLFM4染色。
  - 外部验证：在3个PDO队列、TCGA（466）、单细胞（12.3万细胞）中重复景观。
  - 生存分析：TCGA中的PFS/OS。
- **充分性与客观性**：
  - 实验设计严谨：发现-验证策略；使用排列检验证明轨迹有效；多模态（转录、蛋白、磷酸化）一致性校验。
  - **未进行消融实验**（如去除某些基因集的影响），但通过随机基因集比较验证了轨迹特异性。
  - 数据集覆盖广（不同平台、不同来源），但**未涉及体内模型**（如小鼠异种移植）的验证。
  - 统计方法合理（Wilcoxon秩和检验、线性模型、Cox回归、FDR校正）。

## 6. 论文的主要结论与发现

1. **CRC干细胞呈现连续景观**：PC1轴划分成体干细胞（LGR5+）与胎儿/再生（REG4、MUC2、ANXA1）状态；PC2轴划分代谢吸收（ACE2、DPP4）与EMT/可塑性（FN1、CXCR4）状态。二者正交，共同构成二维连续空间。
2. **MOFA因子2鉴定出PI3K/mTOR依赖性基因模块**：称为**FMD（fetal-mTOR-dependency）签名**。该签名与胎儿/再生程序正相关，与成体干细胞程序负相关，且与Vistusertib、Gedatolisib等mTOR通路抑制剂敏感性显著相关。
3. **FMD签名跨数据集保守**：在外部PDO、TCGA和单细胞数据中均能投影到相同的景观，并与不良预后（PFS）相关（HR=0.79, p=0.033）。
4. **机制：mRNA翻译抑制导致缺乏适应性**：敏感PDO在转录水平上调PI3K/mTOR通路，但蛋白水平下调翻译机器（EIF4E、RPS6KA1等），导致“蛋白瓶颈”。进一步抑制mTOR后，敏感PDO无法诱导补偿性翻译和细胞周期（CDK2活性低），而出现复制应激（CHEK1活性高），导致细胞死亡。
5. **SRC信号网络驱动FMD状态**：激酶抑制剂筛选显示敏感PDO对SRC抑制剂（A419259、Saracatinib）和BTK抑制剂（Ibrutinib）也敏感。蛋白/磷酸化数据表明YES1、TEAD1、PIK3AP1（S759磷酸化）上调，提示SRC-BTK-PIK3AP1轴维持PI3K/mTOR信号和胎儿样程序。
6. **转录因子活性**：AP1、STAT3、YAP1活性与FMD评分强相关，是下游效应器。

## 7. 优点：方法或实验设计上的亮点

- **大规模PDO平台**：64个MSS CRC患者的PDO cohort，覆盖临床多样性，且包含多次生物学重复。
- **多组学功能整合**：不仅做转录组聚类，还将药物响应作为另一模态纳入MOFA，直接连接状态与治疗脆弱性。
- **连续景观建模**：放弃离散分类，采用扩散图+伪时间，更符合生物学现实。
- **跨系统验证**：在PDO、TCGA、单细胞三个层次、多个独立队列中重现景观和FMD签名，证明稳健性。
- **机制深度解析**：利用蛋白质组和磷酸化蛋白质组揭示翻译抑制与SRC信号网络，提供从转录到蛋白的“解耦”证据，并辅以大规模激酶抑制剂筛选进行功能验证。
- **临床相关性**：生存分析显示FMD签名与预后关联，提示潜在治疗分层价值。

## 8. 不足与局限

- **缺乏体内验证**：所有实验均在体外类器官中进行，未涉及小鼠移植模型或患者治疗反应数据。微环境（免疫、基质）的影响未纳入。
- **仅限MSS CRC**：微卫星稳定型占CRC大部分，但MSI-H类型可能具有不同行为，结论不能直接推广。
- **药物筛选范围有限**：使用已批准药物，未覆盖所有潜在靶点；部分药物（如SN-38）仅作为对照。
- **单细胞数据的整合局限性**：来自不同研究，技术差异和批次效应可能影响；仅计算了程序评分，未进行更精细的轨迹推断。
- **生存分析受限于TCGA样本量**：PFS关联p值边缘显著（0.046），OS不显著；需更大队列验证。
- **机制验证深度**：翻译抑制的“蛋白瓶颈”机制仅基于相关性和活性推断，缺乏直接证据（如多核糖体分析、代谢标记）。
- **计算资源未披露**：可复现性受限于未公开的软件参数和算力信息。

（完）
