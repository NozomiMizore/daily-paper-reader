---
title: Textural features for pathway-level representation of omics data in biological networks
title_zh: 生物网络中组学数据通路水平表征的纹理特征
authors: "Alexeyenko, A."
date: 2026-07-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.12.737672v1.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 提出通路级纹理特征用于预测抗癌药物响应（一种扰动）
tldr: Haralick纹理特征在图像分析中广泛应用，但生物网络是稀疏不规则图，直接应用受限。本文提出网络适配的Haralick纹理分析，将基因表达数据转化为通路水平特征。与网络富集分析相比，该方法灵敏度相当，且在体外药物筛选和临床生存分析中保持一致性。该特征可用于稳健的通路-药物反应关联优先排序。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-12-737672-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 746, \"height\": 741, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-12-737672-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 873, \"height\": 935, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-12-737672-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 683, \"height\": 744, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-12-737672-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1734, \"height\": 821, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-12-737672-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1668, \"height\": 702, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-12-737672-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 815, \"height\": 780, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-12-737672-v1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 840, \"height\": 779, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-12-737672-v1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1805, \"height\": 857, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-12-737672-v1/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1673, \"height\": 1122, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-12-737672-v1/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1695, \"height\": 858, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-12-737672-v1/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1767, \"height\": 1627, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-12-737672-v1/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1751, \"height\": 1041, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-12-737672-v1/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1702, \"height\": 1041, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-12-737672-v1/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1625, \"height\": 979, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-12-737672-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1713, \"height\": 865, \"label\": \"Table\"}]"
motivation: 图像纹理特征无法直接用于稀疏、不规则的生物网络，需开发网络适配版本以生成通路级组学特征。
method: 提出网络适配的Haralick纹理分析，从基因级组学数据中提取通路级特征，并用于预测抗癌药物响应。
result: Haralick特征与网络富集分析灵敏度相当，且在体外和临床数据中保持一致的药物响应关联。
conclusion: 该方法可优先排序稳健的通路水平药物响应标志物，支持临床转化应用。
---

## 摘要
五十多年前，Haralick及其合作者提出了一族称为纹理特征的灰度共现统计量。这些特征在图像分析中被广泛使用，但由于细胞网络是稀疏的不规则图而非规则像素网格，因此它们在生物网络中的应用仍然有限。

本文提出了一种网络适配的Haralick纹理分析方法，用于从基因水平组学数据中生成通路水平特征。所得特征集降低了维度，并可用作抗癌药物反应的候选预测因子。将这些特征的性能与原始基因表达变量以及网络富集分析（NEA）的通路特征进行比较，后者已被证明具有稳健性。尽管技术上比NEA简单，但Haralick特征显示出相当的敏感性。更重要的是，在体外药物筛选和临床治疗相关的生存分析中，选定的Haralick特征得以保留，支持了它们在优先筛选稳健的通路水平药物反应相关因素方面的潜在用途。

## Abstract
More than 50 years ago, Haralick and co-authors proposed a family of gray-level co-occurrence statistics that became known as textural features. These features are widely used in image analysis, but their application to biological networks has remained limited because cellular networks are sparse, irregular graphs rather than regular pixel grids.

This work presents a network-adapted version of Haralick texture analysis for generating pathway-level features from gene-level omics profiles. The resulting profiles reduce dimensionality and can be used as candidate predictors of anti-cancer drug response. Performance of these features is compared with original gene expression variables and with pathway features from network enrichment analysis (NEA), whose robustness has been demonstrated previously. Although technically simpler than NEA, Haralick features showed comparable sensitivity. More importantly, selected Haralick features were preserved between in vitro drug screens and clinical treatment-associated survival analyses, supporting their potential use for prioritizing robust pathway-level drug-response correlates.