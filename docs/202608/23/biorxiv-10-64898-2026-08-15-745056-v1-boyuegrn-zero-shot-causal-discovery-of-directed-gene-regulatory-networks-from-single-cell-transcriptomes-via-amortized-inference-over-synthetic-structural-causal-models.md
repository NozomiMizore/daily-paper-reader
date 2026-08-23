---
title: "BoYueGRN: Zero-shot causal discovery of directed gene regulatory networks from single-cell transcriptomes via amortized inference over synthetic structural causal models"
title_zh: BoYueGRN：通过合成结构因果模型的摊销推断，从单细胞转录组中零样本因果发现有向基因调控网络
authors: "Wu, J., Shen, Y.-Q."
date: 2026-08-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.15.745056v1.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 从单细胞转录组中零样本推断因果调控网络，为预测遗传扰动效应提供基础
tldr: 传统GRN推断需逐数据集优化且难以确定因果方向。BoYueGRN在10000个合成结构因果模型上预训练，对任意新数据只需一次前向传播即可输出边概率与调控方向，并通过TF中心滑窗和非对称融合实现全转录组扩展。在BEELINE基准和两个CRISPRi Perturb-seq筛选中，方向准确率分别达到0.86和0.95，可重建五种疾病27万细胞的类型与阶段特异调控动态。该研究确立了训练一次、跨数据集复用的零样本GRN推断范式，有助于疾病调控图谱的大规模构建。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有GRN推断需逐数据集拟合，且多数无法推断因果方向，缺乏可迁移的定向推断工具。
method: 使用1万合成结构因果模型训练，TF中心滑窗与非对称融合实现全转录组零样本推断。
result: BEELINE基准与两个CRISPRi筛选中方向准确率达0.86和0.95，重建五种疾病27万细胞的动态GRN。
conclusion: 将GRN推断变为训练一次、跨数据集复用的零样本范式，支持图谱级疾病调控动态分析。
---

## 摘要
基于单细胞RNA-seq的基因调控网络（GRN）推断通常依赖逐个数据集进行优化。现有工具必须针对每个新数据集重新拟合，而且大多数工具无法推断因果调控方向。在此，我们提出了BoYueGRN，这是一个仅在10,000个合成结构因果模型上训练的摊销因果发现框架。对于任何未见过的数据集，单次前向传播即可返回边概率和调控方向，同时，通过具有不对称融合的TF中心滑动窗口，可将这一固定尺寸模型扩展到全转录组覆盖。BoYueGRN在BEELINE基准测试中展现出强大的零样本性能。在两个独立的全基因组CRISPRi Perturb-seq筛选中，保留边上的方向准确率分别达到0.86和0.95。在跨越超过270,000个细胞的五种疾病中重建的细胞类型和阶段特异性GRN动态，产生了可实验检验的生物学假设。BoYueGRN将定向GRN推断重新定义为一种一次训练、跨数据集复用的范式。通过将网络重建与逐数据集优化解耦，该范式为系统性、图谱规模地映射人类疾病中的调控动态打开了大门。

## Abstract
Gene regulatory network (GRN) inference from single-cell RNA-seq conventionally relies on per-dataset optimization. Existing tools must be refit for every new dataset, and the majority fail to infer causal regulatory directions. Here we present BoYueGRN, an amortized causal discovery framework trained exclusively on 10,000 synthetic structural causal models. For any unseen dataset, a single forward pass returns edge probabilities and regulatory directions, while TF-centric sliding windows with asymmetric fusion extend this fixed-size model to full-transcriptome coverage. BoYueGRN demonstrates strong zero-shot performance across BEELINE benchmarks. On two independent genome-wide CRISPRi Perturb-seq screens, directional accuracy on retained edges reaches 0.86 and 0.95. Reconstructed cell-type- and stage-specific GRN dynamics across five diseases spanning more than 270,000 cells yield experimentally testable biological hypotheses. BoYueGRN reframes directed GRN inference as a train-once, reuse-across-datasets paradigm. By decoupling network reconstruction from per-dataset optimization, this paradigm opens the door to systematic, atlas-scale mapping of regulatory dynamics across human diseases.