---
title: "PertDiffBench: Benchmarking Diffusion Models for Single-Cell Perturbation Response Prediction"
title_zh: PertDiffBench：用于单细胞扰动响应预测的扩散模型基准测试
authors: "Song, Z., Xiang, Y., Jin, W., Li, J., Sun, C., Xie, L."
date: 2026-06-13
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.13.732013v1.full.pdf"
tags: ["query:virtual-cell"]
score: 10.0
evidence: 基于扩散模型的单细胞扰动响应预测标准化基准
tldr: 扩散模型被广泛用于预测单细胞扰动响应，但其相对于简单基线模型的实际优势尚不明确。该研究提出了PertDiffBench标准化基准，在多种场景下评估扩散模型，包括标准预测、跨细胞类型/物种/药物的泛化测试以及特征维度等压力测试。结果表明扩散模型并无一致优势，scGen在常见任务中表现强劲，而scDiffusion在部分泛化设置中较优。该基准为评估扩散模型在扰动响应预测中的表现提供了实用框架。
source: biorxiv
selection_source: fresh_fetch
motivation: 扩散模型在扰动响应预测中的有效性缺乏系统评估，现有研究混淆了架构、表示、生物背景和指标选择的影响。
method: 构建PertDiffBench基准，包含标准预测、泛化到未知条件及压力测试三组设置，系统比较多个扩散模型与基线。
result: 扩散模型无一致优势；scGen在标准预测中表现强，scDiffusion在跨细胞类型泛化中较好；性能对表示选择和任务设计敏感。
conclusion: 扩散模型的性能高度依赖于任务设计和表示选择，PertDiffBench为生物变异和压力条件下的模型评估提供了实用框架。
---

## 摘要
扩散模型越来越多地被用于预测对扰动的转录响应，但它们是否比简单的生成模型和基于表示的基线模型有所改进仍不清楚。现有的评估通常没有区分模型架构、输入表示、生物学背景和度量选择的影响，因此难以确定扩散方法在何处有用。在此，我们介绍PertDiffBench，这是一个基于扩散的转录组扰动预测的标准化基准，涵盖单细胞和批量RNA-seq数据集。PertDiffBench在三个互补的评估设置下评估基于扩散的模型：已知单细胞背景和批量扰动条件下的标准预测、对未见细胞类型、物种、药物和中间时间点的泛化能力，以及针对特征维度、输入表示、噪声类型和基因排序的压力测试。在这些设置中，扩散模型并未表现出一致的优势。在常见预测任务中，scGen仍然是一个强大的基线，而scDiffusion在多个泛化设置中是最具竞争力的基于扩散的方法。时间插值显示出不同的模式，一个直接在表达空间操作的简单DDPM表现优于更专门的模型。压力测试表明，性能依赖于模型，并对特征维度、编码器选择、噪声类型和基因排序敏感。预训练编码器并未持续提升性能，经典的scVI表示在已知条件和未见细胞类型设置中略优于STATE。这些结果表明，扩散模型在扰动响应预测中的性能强烈依赖于任务设计和表示选择。PertDiffBench提供了一个实用框架，用于在生物学变异和压力测试条件下评估这些模型。

## Abstract
Diffusion models are increasingly used to predict transcriptional responses to perturbations, but whether they improve on simpler generative and representation-based baselines remains unclear. Existing evaluations often do not separate the effects of model architecture, input representation, biological context and metric choice, making it difficult to determine where diffusion-based methods are useful. Here we introduce PertDiffBench, a standardized benchmark for diffusion-based transcriptomic perturbation prediction across single-cell and bulk RNA-seq datasets. PertDiffBench evaluates diffusion-based models across three complementary evaluation settings: standard prediction in known single-cell contexts and bulk perturbation conditions, generalization to unseen cell types, species, drugs and intermediate time points, and stress tests of feature dimensionality, input representation, noise type and gene ordering. Across these settings, diffusion models did not show a consistent advantage. scGen remained a strong baseline in common prediction tasks, whereas scDiffusion was the most competitive diffusion-based method in several generalization settings. Temporal imputation showed a different pattern, with a simple DDPM operating directly in expression space outperforming more specialized models. Stress tests showed that performance was model dependent and sensitive to feature dimensionality, encoder choice, noise type and gene ordering. Pretrained encoders did not consistently improve performance, with the classical scVI representation slightly exceeding STATE in seen-condition and unseen-cell-type settings. These results indicate that diffusion-model performance in perturbation response prediction depends strongly on task design and representation choice. PertDiffBench provides a practical framework for evaluating these models under biologically varied and stress-tested conditions.