---
title: Tabular Foundation Models Are Competitive Cellular Perturbation Predictors Across Biological Scales
title_zh: 表格基础模型是跨生物尺度的竞争性细胞扰动预测器
authors: "Palla, G., Hillsley, A., Kim, Y.-J., Royer, L. A."
date: 2026-07-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.28.735106v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 评估表格基础模型作为跨生物尺度的竞争性细胞扰动预测器
tldr: 细胞扰动预测是药物发现的核心问题。现有领域特定模型是否优于通用表格基础模型尚不明确。本研究在跨细胞类型预测、伪批量扰动预测、全基因组CRISPR筛选和胚胎发育预测四个场景中，比较了TabICL、TabPFN与scGPT等专门模型。结果显示通用模型性能相当或更优，表明表格上下文学习是可扩展的强替代方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 评估通用表格基础模型在细胞扰动预测中是否优于领域特定架构。
method: 在跨细胞类型、伪批量、CRISPR筛选和胚胎发育四个设置中，比较TabICL、TabPFN与PRESAGE等模型。
result: 通用模型在多数任务上性能相当或超越专门模型，尤其在伪批量预测中一致领先。
conclusion: 通用表格基础模型提供了可扩展的替代方案，无需领域定制即可有效预测细胞扰动。
---

## 摘要
预测细胞如何响应遗传和化学扰动是药物发现和功能基因组学中的一个核心挑战。为此，已经开发了一个不断增长的专业单细胞基础模型生态系统，但它们相对于领域无关方法的实际优势仍不清楚。在这里，我们评估了TabICL和TabPFN等表格基础模型（通用的预训练回归模型）与包括PRESAGE、scGPT、scLAMBDA、STACK和Prophet在内的领域特定架构在四个互补评估设置中的表现：细胞层面上下文内跨细胞类型预测、基于五个细胞系Perturb-seq数据集的伪批量扰动预测、原代人CD4+ T细胞的全基因组CRISPR筛选，以及斑马鱼发育扰动图谱中的胚胎水平细胞类型组成预测。在细胞级别跨细胞类型扰动预测中，表格基础模型的表现与专业模型相当或更好。在伪批量扰动预测中，表格基础模型在多个评估指标和数据集上 consistently 优于专业基线。在整体胚胎细胞类型组成预测中，表格基础模型与专业基线具有竞争力。这些结果表明，通用的表格上下文学习为跨细胞系统和尺度的扰动响应建模提供了一种强大且可扩展的替代方案，取代了定制的生物架构。

## Abstract
Predicting how cells respond to genetic and chemical perturbations is a central challenge in drug discovery and functional genomics. A growing ecosystem of specialized single-cell foundation models has been developed to address this problem, yet their practical advantage over domain-agnostic approaches remains unclear. Here we evaluate the power of Tabular Foundation Models such as TabICL and TabPFN, general-purpose pre-trained regression models, against domain-specific architectures including PRESAGE, scGPT, scLAMBDA, STACK and Prophet across four complementary evaluation settings: cell-level in-context cross-cell-type prediction, pseudobulk perturbation prediction on five Perturb-seq datasets of cell-lines, a genome-wide CRISPR screen in primary human CD4+ T cells, and embryo-level cell-type composition prediction in a zebrafish developmental perturbation atlas. In the cell-level cross-cell type perturbation prediction, Tabular Foundation Models perform on par or better than specialized models. On pseudobulk perturbation prediction, Tabular Foundation Models consistently outperform specialized baselines across multiple evaluation metrics and datasets. On whole-emrbryo cell-type composition prediction, Tabular Foundation Models are competitive with specialized baselines. These results demonstrate that general-purpose tabular in-context learning provides a strong and scalable alternative to bespoke biological architectures for perturbation response modeling across cell systems and scales.