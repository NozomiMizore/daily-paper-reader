---
title: A Counterfactual Framework for Directional Cell-Cell Interaction Analysis in Spatial Transcriptomics
title_zh: 空间转录组中定向细胞间相互作用分析的反事实框架
authors: "Anzum, H., Kochat, V., Satpati, S., Mahmud, M. I., Dwarampudi, J. M. R., Shukla, P., Javle, M., Kwong, L., Rai, K., Banerjee, T."
date: 2026-07-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.05.716510v4.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 反事实框架预测细胞状态变化，适用于虚拟细胞模型中的扰动模拟
tldr: 现有空间转录组细胞互作研究依赖相关性或已知配体-受体对，缺乏方向性测试。本文提出反事实干预框架，通过邻域条件图模型预测接收细胞状态，并反事实替换发送者邻居量化方向影响，定义反事实方向性分数（CDS）。应用于胆管癌组织微阵列，发现肿瘤-EMT→巨噬细胞等非对称互作，经置换检验显著且与LR分数高度相关。该框架为空间转录组提供了统计严谨、可扩展的方向性分析方法。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-05-716510-v4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1263, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-05-716510-v4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 766, \"height\": 351, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-05-716510-v4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 881, \"height\": 579, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-05-716510-v4/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1037, \"height\": 820, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-05-716510-v4/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1255, \"height\": 505, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-05-716510-v4/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1256, \"height\": 474, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-04-05-716510-v4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1418, \"height\": 886, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-04-05-716510-v4/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1379, \"height\": 885, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-04-05-716510-v4/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 906, \"height\": 559, \"label\": \"Table\"}]"
motivation: 现有方法依赖相关性或先验LR对，无法明确测试细胞间互作的方向性。
method: 构建邻域条件图模型预测受体状态，通过反事实替换候选发送者细胞计算CDS分数，实现LR无关的方向性量化。
result: 在Xenium胆管癌微阵列上识别出Tumor-EMT→Macrophage等不对称互作，置换检验FDR<0.001，与LR分数相关系数0.758。
conclusion: 反事实方向性测试为空间转录组细胞通讯分析提供了统计严谨且可扩展的新范式。
---

## 摘要
理解邻近细胞如何影响细胞状态是空间转录组学的核心，然而现有方法大多依赖于相关性或预定义的配体-受体对，并未明确测试方向性。我们提出了一种基于反事实干预的框架，用于推断与配体-受体无关且可测试发送者特异性的定向细胞间影响。

一个邻域条件图模型根据局部空间上下文预测接收者细胞状态。定向影响通过反事实替换候选发送者类型的邻居并测量预测接收者状态的位移来量化。我们定义了一个反事实方向性分数（CDS）来量化定向影响，并通过在接收者细胞间聚合以及针对每个有序发送者-接收者对测试核心计算配对级CDS。

将该框架应用于Xenium胆管癌组织微阵列（38个核心），识别出肿瘤、免疫和基质区室之间可重复的非对称相互作用，其中最显著的是肿瘤-EMT [→] 巨噬细胞（CDS = 0.0828）和成纤维细胞 [→] 巨噬细胞（CDS = 0.0582）。这些效应超过了标签置换和空间混洗零模型（p < 0.001，FDR控制），并在核心级自举重采样下保持稳定。推断的定向强度与匹配的配体-受体评分高度相关（r = 0.758，p = 0.0027），支持生物学一致性。

这些结果表明，反事实测试是空间转录组学中一种统计上严格且可扩展的定向细胞间通讯分析方法。

## Abstract
Understanding how neighboring cells influence cellular states is central to spatial transcriptomics, yet most existing methods rely on correlation or predefined ligand-receptor (LR) pairs and do not explicitly test directionality. We introduce a counterfactual, intervention-based framework for inferring directional cell-cell influence that is LR-agnostic and tests sender specificity.

A neighborhood-conditioned graph model predicts receiver cell state from local spatial context. Directional influence is quantified by counterfactually replacing neighbors of a candidate sender type and measuring the resulting displacement in predicted receiver state. We define a Counterfactual Directionality Score (CDS) that quantifies directional influence, and compute pair-level CDS by aggregating across receiver cells and test cores for each ordered sender-receiver pair.

Applied to Xenium cholangiocarcinoma tissue microarrays (38 cores), the framework identified reproducible, asymmetric interactions between tumor, immune, and stromal compartments, most prominently Tumor-EMT [-&gt;] Macrophage (CDS = 0.0828) and Fibroblast [-&gt;] Macrophage (CDS = 0.0582). Effects exceeded label-permutation and spatial-shuffle null models (p < 0.001, FDR-controlled) and remained stable under core-level bootstrap resampling. Inferred directional strengths correlated strongly with matched LR scores (r = 0.758, p = 0.0027), supporting biological concordance.

These results demonstrate counterfactual testing as a statistically rigorous and scalable approach for directional cell-cell communication analysis in spatial transcriptomics.