---
title: Perturbation Curve models continuous transcriptional response trajectories and improves prediction of genetic modulations
title_zh: 扰动曲线模型连续转录响应轨迹并改进遗传调控预测
authors: "Zhong, Y., wang, l., Yang, G., Yu, L., Qi, X., Jiang, H."
date: 2026-06-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.16.732192v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 连续扰动强度的转录响应预测模型
tldr: 单细胞CRISPR筛选Perturb-seq中，扰动分配常被视为离散标签，但实际细胞水平扰动强度连续多样，现有框架难以解耦强度变异与响应多样性。本文提出Perturbation Curve (PertCurve)非线性曲线框架，通过按扰动强度排序细胞来建模连续转录响应轨迹。该框架准确重现响应幅度，揭示下游基因行为的比例、敏感和阈值等原型模式，并识别了病毒感染、凋亡等过程中的通用响应及分化中的上下文特异性调控。整合PertCurve至预测模型可提升性能，为功能基因组学提供连续建模新工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有离散标签框架无法有效解耦单细胞CRISPR筛选中连续的扰动强度与多样的下游响应。
method: 提出PertCurve非线性曲线框架，通过按扰动强度排序细胞，建模转录组对连续扰动变化的响应轨迹。
result: 准确重现扰动强度缩放效应，分类出比例、敏感、阈值三种响应原型，并发现通用与上下文特异性调控模式。
conclusion: 揭示了基因响应的异步性，整合至预测模型可提升性能，为理解遗传调控提供连续视角。
---

## 摘要
单细胞CRISPR筛选（Perturb-seq）通过揭示生物学因果关系彻底改变了功能基因组学。然而，尽管扰动分配通常表示为离散标签，但细胞水平上的扰动有效强度通常是连续且多样化的。当前的分析框架难以将扰动强度的变异性与下游反应的多样性分离开来。在此，我们提出扰动曲线（Perturbation Curve, PertCurve），一种基于曲线的非线性计算框架，通过显式纳入不同的扰动幅度和强度来建模转录组响应的轨迹。通过按扰动强度对细胞进行排序，我们证明PertCurve准确再现了响应幅度，并揭示了不同模块性和下游基因行为的异步模式。这些模式被分类为原型，包括比例响应、敏感响应和阈值响应。通过将该框架应用于CRISPRi/a模式，我们识别出病毒感染、凋亡和增殖基因中的通用响应模式，并揭示了细胞分化中先前被忽视的上下文特异性调控特征。最后，将PertCurve纳入扰动预测模型和评估指标可增强预测性能，为改进现有模型提供可操作的见解。

## Abstract
Single-cell CRISPR screens, Perturb-seq, have revolutionized functional genomics by revealing biological causality. However, although perturbation assignments are typically represented as discrete labels, the cell-level effective strength of perturbations is often continuous and diverse. Current analytical frameworks struggle to decouple the variability in perturbation strength from the diversity of downstream responses. Here, we present Perturbation Curve (PertCurve), a nonlinear, curve-based computational framework that models the trajectories of transcriptomic responses by explicitly incorporating diverse perturbation magnitudes and strengths. By ordering cells by perturbation strength, we demonstrate that PertCurve accurately recapitulates the response magnitudes and reveals the distinct modularity and asynchrony patterns of downstream gene behaviors. These patterns are categorized into archetypes, including proportional, sensitive, and threshold responses. By applying this framework across CRISPRi/a modalities, we identify universal response patterns in viral infection, apoptosis, and proliferation genes, and reveal previously overlooked context-specific regulatory features in cell differentiation. Finally, incorporating PertCurve into perturbation prediction models and evaluation metrics enhances predictive performance, delivering actionable insights for refining established models.