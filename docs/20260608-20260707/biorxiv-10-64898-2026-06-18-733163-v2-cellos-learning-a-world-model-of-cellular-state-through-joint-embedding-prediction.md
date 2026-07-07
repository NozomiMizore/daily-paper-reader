---
title: "CellOS: Learning a World Model of Cellular State through Joint Embedding Prediction"
title_zh: CellOS：通过联合嵌入预测学习细胞状态的世界模型
authors: "Zhou, Q., Le, Y., Qi, X., Chang, S., Lu, H., Wu, Y., Wang, H., Ran, R., li, x."
date: 2026-06-25
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.18.733163v2.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 用于AI虚拟细胞表示的多视图基础模型
tldr: 现有单细胞基础模型大多从单一基因表达视图学习，无法整合互补的细胞状态视图。CellOS提出多视图模型，通过因果细胞句子语言建模、稠密到混合专家扩展和LLM-JEPA目标的三阶段训练，在3.9亿单细胞转录组上训练120亿参数，在细胞注释、批次整合和扰动响应预测中超越现有模型。预测对齐互补细胞视图为表示中心的细胞世界模型和可迁移AI虚拟细胞提供了可扩展路径。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有单细胞基础模型仅学习单一基因表达视图，无法整合互补的细胞状态视图。
method: 提出CellOS多视图模型，采用三阶段训练：因果语言建模、稠密到MoE扩展、LLM-JEPA潜空间对齐。
result: 在3.9亿细胞上训练120亿参数模型，细胞注释、批次整合和扰动预测均优于现有模型。
conclusion: 互补细胞视图的预测对齐为构建可扩展的细胞世界模型和可迁移AI虚拟细胞提供了新路径。
---

## 摘要
基于单细胞转录组学的基础模型对于能够表示、查询和预测细胞状态的AI虚拟细胞至关重要。然而，当前大多数单细胞基础模型仅从基因表达的单视角学习，并且主要通过重构或下一个token预测进行优化。因此，它们捕捉表达丰度，但无法明确调和细胞状态的互补视角。本文提出CellOS，一个多视角基础模型，从配对的表达和感知视角学习细胞表示。CellOS通过可扩展的三阶段训练策略整合互补视角，该策略结合了因果细胞句子语言建模、保持功能从密集到混合专家的扩展，以及通过LLM-JEPA目标进行潜在空间对齐。利用这一框架，我们在3.905亿个单细胞转录组上训练了一个120亿参数的模型。在涵盖细胞状态注释、批次整合和扰动响应预测的多种基准测试中，CellOS始终优于最先进的单细胞基础模型。综合这些结果表明，互补细胞视角之间的预测对齐为以表示为中心的细胞世界模型和可迁移的AI虚拟细胞提供了一条可扩展的路径。

## Abstract
Foundation models learned from single-cell transcriptomes are central to the prospect of AI virtual cell that can represent, query and predict cellular state. However, most current single-cell foundation models learn from a single view of gene expression and are optimized primarily through reconstruction or next-token prediction. As a result, they capture expression abundance but cannot explicitly reconcile complementary views of cellular state. Here we present CellOS, a multi-view foundation model that learns cellular representations from paired expression and perception views. CellOS integrates complementary views through a scalable three-stage training strategy that combines causal cell-sentence language modelling, function-preserving dense-to-mixture-of-experts expansion and latent-space alignment via an LLM-JEPA objective. Using this framework, we trained a 12-billion-parameter model on 390.5 million single-cell transcriptomes. Across diverse benchmarks spanning cell-state annotation, batch integration and perturbation-response prediction, CellOS consistently outperformed state-of-the-art single-cell foundation models. Together, these results suggest that predictive alignment between complementary cellular views provides a scalable path toward representation-centric cellular world models and transferable AI virtual cells.