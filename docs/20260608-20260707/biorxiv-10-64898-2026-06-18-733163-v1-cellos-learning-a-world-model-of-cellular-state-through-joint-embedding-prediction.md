---
title: "CellOS: Learning a World Model of Cellular State through Joint Embedding Prediction"
title_zh: CellOS：通过联合嵌入预测学习细胞状态的世界模型
authors: "Zhou, Q., Le, Y., Qi, X., Chang, S., Lu, H., Wu, Y., Wang, H., Ran, R., li, x."
date: 2026-06-23
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.18.733163v1.full.pdf"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 细胞状态世界模型，用于AI虚拟细胞
tldr: 当前单细胞转录组基础模型仅从单一表达视图学习，难以捕捉细胞状态的互补信息。CellOS提出多视图框架，通过因果语言建模、MoE扩展和LLM-JEPA对齐三阶段策略，在3.9亿细胞上训练120亿参数模型。在细胞注释、批次整合和扰动响应预测上超越现有方法，实现了可迁移的AI虚拟细胞。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有单细胞模型仅从单一基因表达视图学习，无法整合互补的细胞状态信息。
method: 三阶段训练：因果细胞-句子语言建模、功能保持的稠密到MoE扩展、基于LLM-JEPA的潜在空间对齐。
result: 在390.5M单细胞转录组上训练12B参数模型，在细胞状态注释、批次整合和扰动预测上全面超越SOTA。
conclusion: 多视图预测对齐为构建表征中心的细胞世界模型和可迁移AI虚拟细胞提供可扩展路径。
---

## 摘要
从单细胞转录组学习得到的基础模型对于实现能够表示、查询和预测细胞状态的AI虚拟细胞至关重要。然而，目前大多数单细胞基础模型从单一基因表达视角学习，并主要通过重建或下一个标记预测进行优化。因此，它们捕获了表达丰度，但无法明确协调细胞状态的互补视图。这里我们介绍CellOS，一个多视图基础模型，它从配对的表达和感知视图中学习细胞表示。CellOS通过可扩展的三阶段训练策略整合互补视图，该策略结合了因果细胞句子语言建模、功能保持的密集到混合专家扩展以及通过LLM-JEPA目标的潜在空间对齐。利用这一框架，我们在3.905亿个单细胞转录组上训练了一个120亿参数的模型。在涵盖细胞状态注释、批次整合和扰动响应预测的多种基准测试中，CellOS始终优于最先进的单细胞基础模型。综上所述，这些结果表明互补细胞视图之间的预测对齐为以表示为中心的细胞世界模型和可迁移的AI虚拟细胞提供了一条可扩展的路径。

## Abstract
Foundation models learned from single-cell transcriptomes are central to the prospect of AI virtual cell that can represent, query and predict cellular state. However, most current single-cell foundation models learn from a single view of gene expression and are optimized primarily through reconstruction or next-token prediction. As a result, they capture expression abundance but cannot explicitly reconcile complementary views of cellular state. Here we present CellOS, a multi-view foundation model that learns cellular representations from paired expression and perception views. CellOS integrates complementary views through a scalable three-stage training strategy that combines causal cell-sentence language modelling, function-preserving dense-to-mixture-of-experts expansion and latent-space alignment via an LLM-JEPA objective. Using this framework, we trained a 12-billion-parameter model on 390.5 million single-cell transcriptomes. Across diverse benchmarks spanning cell-state annotation, batch integration and perturbation-response prediction, CellOS consistently outperformed state-of-the-art single-cell foundation models. Together, these results suggest that predictive alignment between complementary cellular views provides a scalable path toward representation-centric cellular world models and transferable AI virtual cells.