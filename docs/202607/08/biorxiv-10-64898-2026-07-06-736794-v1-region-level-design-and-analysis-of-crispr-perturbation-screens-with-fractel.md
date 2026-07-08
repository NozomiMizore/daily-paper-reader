---
title: Region-Level Design and Analysis of CRISPR Perturbation Screens with FRACTEL
title_zh: 基于FRACTEL的CRISPR扰动筛选区域级设计与分析
authors: "Doty, R. W., ter Weele, M. A., Barrera, A., Bounds, L. R., Gersbach, C. A., Allen, A. S."
date: 2026-07-07
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.06.736794v1.full.pdf"
tags: ["query:virtual-cell"]
score: 7.0
evidence: CRISPR扰动筛选分析框架
tldr: CRISPR扰动筛选的区域级分析缺乏统计方法。FRACTEL采用有界最小顺序统计量聚合gRNA p值，通过模拟估计区域级零分布。模拟和真实数据表明其比gRNA级分析具有更高功效和重复率，并能揭示gRNA冗余与功效间的权衡。该框架集成现有流程，提升区域级CRISPR筛选分析的准确性与可解释性。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有CRISPR筛选分析主要针对gRNA级别，缺乏区域级统计方法，无法有效检测稀疏或弥散效应。
method: FRACTEL利用有界最小顺序统计量聚合gRNA p值，并通过模拟估计区域级零分布以控制I类错误。
result: 在模拟和真实CRISPRi/a数据中，FRACTEL相比gRNA级分析显著提升功效和重复率，并指导实验设计权衡。
conclusion: FRACTEL为区域级CRISPR筛选提供鲁棒统计框架，集成现有流程，拓展了在单细胞抑制等场景的应用。
---

## 摘要
我们提出了FRACTEL，一个用于CRISPR扰动筛选区域级分析的统计框架。FRACTEL通过顺序统计量的有界最小值聚合gRNA p值，保持尺度并实现对稀疏或扩散效应的自适应敏感性。通过模拟估计区域级零分布，确保精确的I类错误控制。模拟和真实的CRISPRi/a数据集表明，与gRNA级分析相比，具有更高的功效和复制率。FRACTEL还为实验设计提供信息，揭示了gRNA冗余与功效之间的权衡，并识别了低表达基因单细胞抑制筛选中的固有极限。该方法与现有流程集成，并支持多种CRISPR筛选应用。

## Abstract
We present FRACTEL, a statistical framework for region-level analysis of CRISPR perturbation screens. FRACTEL aggregates gRNA p-values using a bounded minimum across order statistics, preserving scale and enabling adaptive sensitivity to sparse or diffuse effects. Region-level null distributions are estimated via simulation, ensuring precise type I error control. Simulations and real CRISPRi/a datasets demonstrate improved power and replication rate over gRNA-level analyses. FRACTEL also informs experimental design, revealing trade-offs between gRNA redundancy and efficacy and identifying inherent limits in single-cell repression screens of lowly expressed genes. The method integrates with existing pipelines and supports diverse CRISPR screening applications.