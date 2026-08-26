---
title: "bulk2scDiff: A Pseudobulk-Conditioned Diffusion Model for Bulk-to-Single-Cell RNASeq Generation"
title_zh: bulk2scDiff：一种用于批量到单细胞RNA测序生成的伪批量条件扩散模型
authors: "Xiao, J., Raue, A."
date: 2026-08-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.20.745960v1.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 提出伪批量条件扩散模型生成单细胞RNA-seq，支持从批量数据推断虚拟细胞状态。
tldr: Bulk RNA测序只能获得群体平均水平，掩盖了细胞异质性。现有反卷积方法多估计细胞类型比例或平均表达，无法解析单细胞水平。本文提出bulk2scDiff，一种基于条件扩散的框架，将bulk转录组生成单细胞表达谱。在乳腺癌和急性髓系白血病数据上，模型能重建训练样本群体，并对留出样本生成生物学上一致的单细胞群体，验证了可行性。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有bulk转录组分析难以揭示细胞异质性，而反卷积方法仅提供细胞类型比例或平均表达，无法达到单细胞分辨率。
method: 构建基于伪bulk条件输入的扩散模型，将单细胞生成视为条件生成问题，用单细胞数据派生伪bulk作为条件。
result: 在两种癌症数据上，模型重建训练样本群体，对留出样本生成一致的免疫特征，伪bulk交换对照验证了样本特异性。
conclusion: 该工作首次证明条件扩散可从bulk转录组生成单细胞群体，为临床bulk数据应用奠定基础。
---

## 摘要
批量RNA测序仍是大型临床队列的主要分析策略，但它汇总了细胞群体中的转录信号，从而掩盖了潜在的细胞异质性。从现有的批量转录组数据中推断这种异质性，可以扩展已经完成分析的大型队列研究，但这构成一个欠定逆问题，因为一个批量谱可能与多个潜在的细胞群兼容。现有的计算反卷积方法主要通过估计细胞类型比例或细胞类型平均表达谱来解决这个问题，而不是在单个细胞水平上解析表达。在这里，我们提出了bulk2scDiff，一个概念验证的条件扩散框架，它将批量到单细胞的推断重新表述为从伪批量转录组输入条件生成单细胞表达谱。我们在两个癌症单细胞RNA测序数据集上评估了bulk2scDiff，即乳腺癌和急性髓系白血病，其中伪批量谱来自单细胞数据并用作条件输入，匹配的单细胞群体为受控评估提供了真实标签。在这两种情况下，bulk2scDiff都能从训练样本中紧密重建群体，并为留出样本生成生物学上一致的单细胞群体，最一致地泛化到复发性免疫特征。伪批量交换对照进一步证实了样本特异性条件，在几乎所有情况下，每个样本对应的伪批量与其观察到的群体的一致性最高。总体而言，我们的工作确立了从伪批量转录组谱生成单细胞群体的条件扩散的可行性，为未来使用临床批量RNA测序数据进行评估奠定了基础。

## Abstract
Bulk RNA sequencing remains the predominant profiling strategy for large clinical cohorts, but it aggregates transcriptional signals across cell populations, thereby masking the underlying cellular heterogeneity. Inferring this heterogeneity from existing bulk transcriptomic data could extend large cohort-based studies that have already been profiled, but constitutes an underdetermined inverse problem, as one bulk profile can be compatible with multiple underlying cellular populations. Existing computational deconvolution methods address this problem primarily by estimating cell-type proportions or cell-type-averaged expression profiles rather than resolving expression at the level of individual cells. Here, we present bulk2scDiff, a proof-of-concept conditional diffusion framework that reformulates bulk-to-single-cell inference as conditional generation of single-cell expression profiles from pseudobulk transcriptomic input. We evaluated bulk2scDiff on two cancer single-cell RNA sequencing datasets, breast cancer and acute myeloid leukemia, where pseudobulk profiles were derived from the single-cell data and used as conditioning inputs, with the matched single-cell populations providing ground truth for controlled evaluation. Across both cases, bulk2scDiff closely reconstructed populations from training samples and generated biologically coherent single-cell populations for held-out samples, generalizing most consistently to recurrent immune features. A pseudobulk-swap control further confirmed sample-specific conditioning, with each sample corresponding pseudobulk yielding the closest agreement with its observed population in nearly all cases. Overall, our work establishes the feasibility of conditional diffusion for generating single-cell populations from pseudobulk transcriptomic profiles, providing a foundation for future evaluation with clinical bulk RNA sequencing data.