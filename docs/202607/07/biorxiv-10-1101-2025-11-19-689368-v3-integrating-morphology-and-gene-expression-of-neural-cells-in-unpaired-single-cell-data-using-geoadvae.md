---
title: Integrating morphology and gene expression of neural cells in unpaired single-cell data using GeoAdvAE
title_zh: 利用GeoAdvAE整合非配对单细胞数据中神经细胞的形态与基因表达
authors: "Du, J. T., Chartrand, T., Jayadev, S., Prater, K. E., Lin, K. Z."
date: 2026-06-30
pdf: "https://www.biorxiv.org/content/10.1101/2025.11.19.689368v3.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 整合单细胞形态与转录组，支持将形态变化与基因表达扰动关联的分析
tldr: 单细胞形态与转录组数据通常来自不同细胞且缺乏对应特征，难以直接整合。本文提出GeoAdvAE，一种几何感知的对抗自编码器，通过Gromov-Wasserstein正则化和对抗判别器将非配对形态与转录组嵌入共享空间。在patch-seq神经元数据上，该方法跨模态匹配准确率最优，并在阿尔茨海默病模型中恢复了形态-转录组轴，鉴定了疾病相关基因标志物。GeoAdvAE提供了无需联合测量的可扩展整合方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 单细胞形态和转录组数据来自不同细胞且缺乏特征对应，难以直接关联分析。
method: GeoAdvAE结合模态特定变分自编码器与Gromov-Wasserstein正则化和对抗判别器，学习非配对数据的共享潜在空间。
result: 在patch-seq神经元数据上跨模态匹配准确率最优，并在5xFAD模型中恢复形态-转录组轴并发现疾病相关基因与形态解耦。
conclusion: GeoAdvAE提供可扩展、可解释的桥梁连接细胞形式与功能，适用于无法同时测量的场景。
---

## 摘要
背景：在许多疾病中观察到细胞形态转变，但由于少有技术能在同一细胞中同时测量形态和功能，其功能作用仍不清楚。将单细胞形态与转录组学联系起来很困难：这两种模态没有特征对应关系，且通常在不同细胞中测量。
方法：我们提出GeoAdvAE，一种用于单细胞形态和单细胞RNA测序的对角（非配对）整合的几何感知对抗自编码器。GeoAdvAE将模态特异性变分自编码器与Gromov-Wasserstein正则化器和对抗判别器相结合，将非配对的形态和转录组嵌入到一个共享的潜在空间中，该空间同时保留重建保真度和跨模态几何结构。
结果：使用具有联合形态-RNA测量的patch-seq神经元作为真实值，GeoAdvAE在对角整合方法中实现了最佳的跨模态细胞类型匹配准确度，优于最优传输、潜在对齐和对抗基线方法。应用于来自5xFAD阿尔茨海默病模型的98个CAJAL定量小胶质细胞形态和31,948个单细胞转录组，GeoAdvAE恢复了一个对齐两种模态的一维轴。集成梯度归因突出了转录组变化（分枝状小胶质细胞中的DNA修复；阿米巴状小胶质细胞中的细胞杀伤），提名了基因标志物（Ms4a6b；Ftl1 /Fth1），并揭示了与形态解耦的疾病相关小胶质细胞特征。
结论：当形态和转录组的联合分析不切实际时，GeoAdvAE提供了一种可扩展且可解释的方法来连接细胞的“形态”和“功能”。我们的方法公开在https://github.com/turbodu222/GeoAdVAE。

## Abstract
BackgroundCellular morphological transitions are observed across many diseases, yet their functional role remains unclear because few technologies profile form and function in the same cell. Linking single-cell morphology to transcriptomics is difficult: the two modalities share no feature correspondence and are typically measured in different cells.

MethodsWe present GeoAdvAE, a geometry-aware adversarial autoencoder for diagonal (unpaired) integration of single-cell morphology and single-cell RNA sequencing. GeoAdvAE couples modality-specific variational autoencoders with a Gromov-Wasserstein regularizer and an adversarial discriminator to embed unpaired morphologies and transcriptomes into a shared latent space that preserves both reconstruction fidelity and cross-modal geometry.

ResultsUsing patch-seq neurons with joint morphology-RNA measurements as ground truth, GeoAdvAE attains the best cross-modal cell-type matching accuracy among diagonal integration methods, outperforming optimal-transport, latent-alignment, and adversarial baselines. Applied to 98 CAJAL-quantified microglial morphologies and 31,948 single-cell transcriptomes from the 5xFAD Alzheimers disease model, GeoAdvAE recovers a one-dimensional axis that aligns the two modalities. Integrated-gradient attribution highlights transcriptomic shifts (DNA repair in ramified microglia; cell killing in amoeboid microglia), nominates gene markers (Ms4a6b; Ftl1 /Fth1), and reveals disease-associated microglia signatures that are decoupled from morphology.

ConclusionsGeoAd-vAE provides a scalable and interpretable approach to connecting cellular "form" and "function" when joint profiling of morphology and transcriptomics is impractical. Our method is publicly available at https://github.com/turbodu222/GeoAdVAE.