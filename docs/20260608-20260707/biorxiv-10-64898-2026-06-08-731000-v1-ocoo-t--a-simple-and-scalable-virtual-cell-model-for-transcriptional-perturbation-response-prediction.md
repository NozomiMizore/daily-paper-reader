---
title: "OCOO-T : A SIMPLE AND SCALABLE VIRTUAL CELL MODEL FOR TRANSCRIPTIONAL PERTURBATION RESPONSE PREDICTION"
title_zh: OCOO-T：一种用于转录扰动响应预测的简单且可扩展的虚拟细胞模型
authors: "Zhao, Y., Lai, L., Jiang, D., An, Z."
date: 2026-06-11
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.08.731000v1.full.pdf"
tags: ["query:virtual-cell"]
score: 10.0
evidence: 用于转录扰动响应预测的虚拟细胞模型
tldr: 预测细胞对遗传、化学和细胞因子扰动的转录响应是计算生物学和AI虚拟细胞模型的核心挑战。现有模型依赖复杂架构，限制扩展性与泛化性。OCOO-T提出基于流匹配的简约框架，采用普通Transformer直接处理连续基因表达谱，通过自适应层归一化和上下文令牌整合扰动与细胞信息。在Tahoe100M、Replogle和PBMC基准上取得最先进性能，并利用分片与合并技术有效扩展至长转录谱。该工作为可扩展的虚拟细胞模拟提供了简单有效方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有转录扰动预测模型架构复杂，难以扩展和泛化，亟需简单且可扩展的虚拟细胞模型。
method: 基于流匹配的Transformer，直接处理连续表达谱，通过自适应层归一化和上下文令牌整合扰动、剂量及细胞类型信息。
result: 在Tahoe100M、Replogle和PBMC基准上达到最先进性能，并有效扩展至长转录谱。
conclusion: OCOO-T以简约设计实现高精度和可扩展性，为虚拟细胞模拟提供有效框架。
---

## 摘要
预测单细胞对遗传、化学和细胞因子扰动的转录反应是计算生物学和AI虚拟细胞（AIVC）建模中的一个基本挑战，对药物发现和基因调控网络的阐明具有直接意义。现有方法通常依赖辅助细胞状态编码器、分层变分自编码器、专用Transformer编码器-解码器模块或基因相互作用先验，将高维表达谱压缩为潜在表示。虽然有效，但这些设计增加了架构复杂度，可能限制可扩展性和泛化能力。本文介绍了OCOO-T，一种基于简约流匹配的AIVC模型，用于转录扰动响应预测。OCOO-T使用一个直接在连续基因表达谱上操作的普通Transformer栈，并将扰动响应预测表述为连续时间去噪过程。通过自适应层归一化和上下文令牌整合扰动嵌入、剂量信息以及细胞系/细胞类型特异性。在Tahoe100M、Replogle和PBMC基准上的全面评估表明，OCOO-T在多种扰动和细胞类型上实现了最先进的性能，同时通过细胞上下文的拼接和分解有效扩展到长转录谱。通过利用基于Transformer的去噪的简单性进行单细胞组学分析，OCOO-T为计算机细胞模拟提供了一个有效且可扩展的框架。

## Abstract
Predicting single-cell transcriptional responses to genetic, chemical and cytokine perturbations is a fundamental challenge in computational biology and AI Virtual Cell (AIVC) modeling, with direct implications for drug discovery and the elucidation of gene regulatory networks. Existing approaches often rely on auxiliary cell-state encoders, hierarchical variational autoencoders, dedicated Transformer encoder-decoder modules, or gene-interaction priors to compress high-dimensional expression profiles into latent representations. While effective, these designs increase architectural complexity and may limit scalability and generalizability. This paper introduces OCOO-T 1, a minimalist flow-matching-based AIVC model for transcriptional perturbation response prediction. OCOO-T utilizes a vanilla Transformer stack that operates directly on continuous gene expression profiles and formulates perturbation response prediction as a continuous-time denoising process. Perturbation embeddings, dosage information, and cell-line/cell-type specificity are integrated through adaptive layer normalization and in-context tokens. Comprehensive evaluations on Tahoe100M, Replogle, and PBMC benchmarks demonstrate that OCOO-T achieves state-of-the-art performance across diverse perturbations and cell types while effectively scaling to long transcriptional profiles through patching and depatching of cellular contexts. By leveraging the simplicity of Transformer-based denoising for single-cell omics, OCOO-T provides an effective and scalable framework for in-silico cellular simulation.