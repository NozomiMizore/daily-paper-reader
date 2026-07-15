---
title: A Bayesian Network-Based Framework for Causal Cancer Drug Target Discovery Integrating Patient and Cell Line Data
title_zh: 基于贝叶斯网络的因果性癌症药物靶点发现框架整合患者与细胞系数据
authors: "Yoon, S. H., Park, Y. R., Kim, H. U."
date: 2026-07-13
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.13.736676v1.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 通过贝叶斯网络整合患者和细胞系数据发现因果药物靶点
tldr: 现有癌症药物靶点发现受限于细胞系-患者转化困难及缺乏因果解释。BayesTx框架整合患者和细胞系转录组数据，学习域特异性贝叶斯网络并加权聚合，通过do-simulation量化转录因子对癌细胞活性的因果效应。在乳腺癌中鉴定出47个因果转录因子及下游基因靶点，顶级靶点经独立生存分析和药物反应验证。该方法为跨数据域因果靶点发现提供了系统性框架。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-736676-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1579, \"height\": 914, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-736676-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1559, \"height\": 1377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-736676-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 753, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-736676-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1571, \"height\": 995, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-736676-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1632, \"height\": 864, \"label\": \"Figure\"}]"
motivation: 克服细胞系靶点难以转化至患者肿瘤且缺乏因果机制解释的局限。
method: 将患者与细胞系数据映射到共享通路空间，学习因果图并加权聚合，通过bootstrap共识滤波，利用do-simulation评估转录因子因果效应。
result: 在乳腺癌中识别47个转录因子及Regulon传播的基因靶点，顶级靶点获外部生存和药物基因组关联支持。
conclusion: 跨域贝叶斯网络建模可桥接患者和细胞系数据，系统发现癌症因果治疗靶点。
---

## 摘要
当前癌症药物靶点发现方法面临两个关键限制：从细胞系衍生靶点向患者肿瘤的转化不佳，以及靶点优先级排序背后的调控机制缺乏因果解释。在此，我们提出BayesTx（贝叶斯治疗靶点发现），一个贝叶斯网络框架，整合患者转录组学数据与细胞系数据以识别癌症中的因果性治疗靶点。BayesTx将两个数据域投影到通路和转录因子活性的共享生物学空间，学习域特异性因果图，并通过加权边聚合与自助法共识过滤合并它们。对共识网络进行do-模拟量化每个转录因子对癌细胞活性的因果效应。使用TCGA-BRCA（癌症基因组图谱乳腺癌队列）和DepMap（癌症依赖性图谱）数据集应用于乳腺癌，该框架通过预测的因果影响对47个转录因子进行排序，并通过基于调节子的传播进一步得到基因水平靶点。排名靠前的转录因子（TF）靶点得到了外部队列数据中生存分析和药物基因组药物反应关联的独立支持。总体而言，BayesTx证明了跨域贝叶斯网络建模可以桥接患者和细胞系数据，以系统识别癌症中的因果性治疗靶点。

## Abstract
Current approaches to cancer drug target discovery face two key limitations: poor translation of cell line-derived targets to patient tumors, and the lack of causal explanation of the regulatory mechanisms underlying target prioritization. Here we present BayesTx (Bayesian Therapeutics target discovery), a Bayesian network framework that integrates patient transcriptomics data with cell line data to identify causal therapeutic targets in cancer. BayesTx projects both data domains into a shared biological space of pathway and transcription factor activities, learns domain-specific causal graphs, and merges them through weighted edge aggregation with bootstrap consensus filtering. Do-simulation on the consensus network quantifies the causal effect of each transcription factor on cancer cell viability. Applied to breast cancer using TCGA-BRCA (The Cancer Genome Atlas breast cancer cohort) and DepMap (Cancer Dependency Map) datasets, the framework ranked 47 transcription factors by predicted causal impact, with gene-level targets further derived through regulon-based propagation. Top-ranked transcription factor (TF) targets were independently supported by survival analysis in external cohort data and pharmacogenomic drug response associations. Overall, BayesTx demonstrates that cross-domain Bayesian network modeling can bridge patient and cell line data to systematically identify causal therapeutic targets in cancer.