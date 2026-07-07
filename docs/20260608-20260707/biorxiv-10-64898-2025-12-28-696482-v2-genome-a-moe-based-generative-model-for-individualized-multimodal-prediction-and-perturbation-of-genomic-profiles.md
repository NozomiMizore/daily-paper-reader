---
title: "GenoME: a MoE-based generative model for individualized, multimodal prediction and perturbation of genomic profiles"
title_zh: GenoME：一种基于MoE的生成模型，用于基因组图谱的个体化、多模态预测与扰动
authors: "Wei, J., Xue, Y., Chai, H., Gao, Y. Q."
date: 2026-06-23
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.28.696482v2.full.pdf"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 用于基因组谱扰动预测的生成模型
tldr: 非编码基因组的调控机制复杂且多尺度，现有模型难以整合多模态数据。GenoME提出基于混合专家模型的生成式框架，通过DNA序列和ATAC-seq信号统一预测表观组、转录组和染色质构象。模型支持跨细胞类型泛化与遗传扰动模拟，在增强子-启动子连接预测上超越Activity-by-Contact等专用模型。该工作为调控基因组提供了一站式生成建模与因果机制探究平台。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有模型难以从单一输入整合预测多模态基因组特征，且跨细胞类型泛化能力不足。
method: 采用混合专家模型（MoE）架构，以DNA序列和细胞类型特异性ATAC-seq为输入，联合预测组蛋白修饰、转录因子结合、基因表达及3D构象。
result: 在留出区域和未见细胞类型上实现多模态精准预测，并借助in silico扰动准确推断遗传扰动效应及增强子-启动子功能连接。
conclusion: GenoME为多尺度调控基因组提供了统一的生成式建模与因果分析工具，有望推动非编码区功能解析。
---

## 摘要
非编码基因组通过复杂的多尺度调控系统运作，其中受调控的基因表达与细胞类型特异性的组蛋白修饰、转录因子结合和三维构象密切相关。开发能够整合这些模式以预测和解释调控系统的计算模型仍然具有挑战性。在这里，我们提出了GenoME，一种基于专家混合（MoE）的生成模型，它利用DNA序列和细胞类型特异性的ATAC-seq信号，从碱基对到千碱基分辨率预测涵盖表观基因组学、转录组学和染色质结构的统一基因组图谱。GenoME能够对保留的基因组区域进行多尺度预测，并且至关重要的是，它能够从单个ATAC-seq输入推广到预测未见或个体化细胞类型的完整调控景观。我们为GenoME配备了计算机模拟扰动框架，该框架能够准确预测遗传扰动的多模态后果，并识别功能增强子-启动子连接，优于Activity-by-Contact等专门模型。这些预测还可用于解读细胞类型特异性增强子的转录因子语法。因此，GenoME为多尺度调控基因组的生成建模、跨细胞类型泛化以及因果机制研究提供了一个多功能的一站式平台。

## Abstract
The non-coding genome operates through a complex, multiscale regulatory system where regulated gene expressions are closely associated with cell-type-specific histone modifications, transcription factor binding and 3D conformation. Developing computational models that can integrate these patterns to predict and interpret the regulatory system remains challenging. Here, we present GenoME, a Mixture of Experts (MoE)-based generative model that uses DNA sequence and cell-type-specific ATAC-seq signals to predict a unified genomic profile encompassing epigenomics, transcriptomics, and chromatin architecture at base-pair to kilobase resolutions. GenoME enables multiscale predictions for held-out genomic regions and, critically, generalizes to predict the full regulatory landscape of unseen or individualized cell types from a single ATAC-seq input. We equip GenoME with an in silico perturbation framework that accurately forecasts the multimodal consequences of genetic perturbations and identifies functional enhancer-promoter connections, outperforming specialized models like Activity-by-Contact. These predictions can also be used to decipher the transcription factor grammar of cell-type-specific enhancers. GenoME thus provides a versatile, all-in-one platform for generative modeling, cross-cell-type generalization, and causal mechanistic investigation of the multiscale regulatory genome.