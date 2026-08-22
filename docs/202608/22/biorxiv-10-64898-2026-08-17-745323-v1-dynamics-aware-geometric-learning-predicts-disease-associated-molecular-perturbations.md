---
title: Dynamics-aware geometric learning predicts disease-associated molecular perturbations
title_zh: 动力学感知的几何学习预测疾病相关的分子扰动
authors: "Ning, Y., Cai, M., Luo, D., Li, Y., Verkhivker, G., Hu, G., Liang, Z."
date: 2026-08-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.17.745323v1.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 深度学习预测分子扰动效应的相关方法
tldr: 错义突变和磷酸化修饰是重要蛋白分子扰动，但常被独立研究且忽略动力学信息。本文提出DynGeo-Pheno框架，融合蛋白质语言模型与各向异性网络模型，统一预测致病突变与磷酸化位点。结果显示两者均富集于配体结合口袋和蛋白互作界面，但动态特征不同：磷酸化位点倾向灵活调节区域，而致病突变位于有序结构元件，且共同具有增强的长程耦联和机械稳定性。该工作揭示了内在动力学是致病性的重要补充决定因素。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法依赖序列保守性或静态结构，缺乏对蛋白质内在动力学及扰动联合效应的统一理解。
method: 提出DynGeo-Pheno，集成蛋白质语言模型与各向异性网络模型，联合捕获进化、结构和动力学特征。
result: 在独立测试集上高精度预测疾病相关磷酸化位点和致病错义突变，并揭示两者富集于功能关键结构区域。
conclusion: 证明蛋白质内在动力学是致病性判定的重要互补因素，为可解释AI预测疾病机制提供统一框架。
---

## 摘要
错义突变和翻译后修饰（PTMs）是重塑蛋白质功能的主要分子扰动，但传统上它们是分开研究的。当前的计算方法主要依赖于序列保守性或静态结构特征，限制了我们对扰动如何改变蛋白质内在动力学的理解。我们提出了DynGeo-Pheno，一个统一的几何深度学习框架，将蛋白质语言模型表示与各向异性网络模型导出的动力学相结合，共同捕捉进化、结构和生物物理信息。DynGeo-Pheno在独立测试数据集上高精度地预测了疾病相关的磷酸化位点和致病性错义突变。消融分析表明，蛋白质动力学在序列进化和结构拓扑之外提供了互补的致病性预测信息。除了预测性能，DynGeo-Pheno还揭示了疾病相关扰动优先定位于功能性结构区域，包括配体结合口袋和蛋白质-蛋白质相互作用界面。从机制上讲，磷酸化位点和错义突变表现出不同但趋同的动力学特征。磷酸化位点优先出现在柔性调节区域，而致病突变富集于有序结构元件中。尽管存在这些差异，两种扰动类型都表现出增强的长程耦合、增加的扰动响应性和升高的机械稳定性，表明致病残基优先占据机械约束和变构调节位点。本研究提供了有力证据，表明内在蛋白质动力学是致病性的重要补充决定因素，并建立了一个统一的框架，用于可解释的人工智能预测和对遗传及调节扰动如何塑造蛋白质功能的机制理解。

## Abstract
Missense mutations and post-translational modifications (PTMs) are major molecular perturbations that reshape protein function but are traditionally studied independently. Current computational approaches largely rely on sequence conservation or static structural features, limiting our understanding of how perturbations alter intrinsic protein dynamics. We present DynGeo-Pheno, a unified geometric deep learning framework that integrates protein language model representations with anisotropic network model-derived dynamics to jointly capture evolutionary, structural, and biophysical information. DynGeo-Pheno predicts disease-associated phosphosites and pathogenic missense mutations with high accuracy on independent test datasets. Ablation analyses indicate that protein dynamics provide complementary information beyond sequence evolution and structural topology for pathogenicity prediction. Beyond predictive performance, DynGeo-Pheno reveals that disease-associated perturbations preferentially localize to functional structural regions, including ligand-binding pockets and PPI interfaces. Mechanistically, phosphosites and missense mutations appear to exhibit distinct yet convergent dynamic signatures. Phosphosites preferentially occur in flexible regulatory regions, whereas pathogenic mutations are enriched in ordered structural elements. Despite these differences, both perturbation types display enhanced long-range coupling, increased perturbation responsiveness, and elevated mechanical stability, indicating that pathogenic residues preferentially occupy mechanically constrained and allosteric regulatory sites. This study provides compelling evidence that intrinsic protein dynamics is an important complementary determinant of pathogenicity and establishes a unified framework for interpretable AI predictions and mechanistic understanding of how genetic and regulatory perturbations may shape protein function.