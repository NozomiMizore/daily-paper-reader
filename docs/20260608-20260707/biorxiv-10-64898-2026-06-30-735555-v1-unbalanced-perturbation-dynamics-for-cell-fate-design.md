---
title: Unbalanced Perturbation Dynamics For Cell Fate Design
title_zh: 用于细胞命运设计的不平衡扰动动力学
authors: "Peng, Q., Wang, Y., Li, J., Wang, X., Xiao, Y., Zhou, P."
date: 2026-07-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.30.735555v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 使用不平衡生成框架进行单细胞扰动响应预测
tldr: 单细胞扰动测序中细胞数量因增殖、凋亡等发生非平衡变化，现有模型大多忽略此问题。本文提出U-Pert，一种不平衡生成框架，联合建模转录组状态转移与细胞丰度动态，可在非配对快照上训练，实现未知扰动的准确预测和用户定义目标的逆向干预筛选。在模拟、遗传扰动、药物响应等任务中验证，表明细胞丰度是扰动表型的必要组成部分，为虚拟细胞建模提供质量感知新范式。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有扰动响应模型仅关注转录状态转变，忽略了单细胞测量中因增殖、凋亡导致的细胞数量非平衡变化，限制了模型准确性和生物学意义。
method: 提出U-Pert，一种不平衡生成框架，同时学习转录状态转移和细胞数量动态，支持非配对快照训练，实现可扩展的前向预测与逆向设计。
result: 在模拟、遗传扰动、药物响应和细胞因子扰动中，U-Pert准确预测未知响应，捕获分子与丰度变化，并成功逆向设计目标基因表达和细胞组成。
conclusion: 细胞丰度是扰动表型的关键维度，U-Pert为虚拟细胞建模和细胞命运设计提供了整合质量感知的动态框架。
---

## 摘要
大规模单细胞扰动测序为构建虚拟细胞以在计算机模拟细胞反应和逆设计最优干预提供了前所未有的机会。然而，大多数扰动-响应模型主要将细胞反应视为转录组状态的物质守恒转移，而单细胞扰动测量本质上是不平衡的：恢复的终点群体受技术采样以及生物扰动诱导的增殖、凋亡和选择影响。在这里，我们引入了U-Pert，一个不平衡生成框架，从未配对的单细胞快照中学习条件和上下文依赖的扰动动力学。U-Pert联合建模转录组状态转变和细胞数量动力学，使得对未见过扰动和上下文的可扩展且鲁棒的前向预测成为可能，以及逆设计以筛选实现用户定义转录组或群体水平结果的期望遗传或药理干预。在受控模拟、遗传扰动基准、sciPlex3药物反应和PBMC细胞因子扰动中，U-Pert预测未见过响应，捕获分子和丰度变化，并针对目标基因表达程序和细胞类型组成进行逆设计。这些结果表明细胞丰度是扰动表型的组成部分，为虚拟细胞建模和扰动细胞命运设计提供了一个质量感知框架。

## Abstract
Large-scale single-cell perturbation sequencing provides an unprecedented opportunity to construct virtual cells for the in silico simulation of cellular responses and the inverse design of optimal interventions. However, most perturbation-response models treat cellular responses primarily as mass-preserving shifts in transcriptomic state, whereas single-cell perturbation measurements are inherently unbalanced: the recovered endpoint population is shaped by technical sampling as well as biological perturbation-induced proliferation, apoptosis and selection. Here we introduce U-Pert, an unbalanced generative framework that learns condition- and context-dependent perturbation dynamics from unpaired single-cell snapshots. U-Pert jointly models transcriptomic state transitions and cell-number dynamics, enabling scalable and robust forward prediction of unseen perturbations and contexts, as well as inverse design to screen for desired genetic or pharmacological interventions that achieve user-defined transcriptomic or population-level outcomes. Across controlled simulations, genetic perturbation benchmarks, sciPlex3 drug responses and PBMC cytokine perturbations, U-Pert predicts unseen responses, captures both molecular and abundance changes, and performs inverse design for target gene-expression programs and cell-type compositions. These results show that cell abundance is an integral component of the perturbation phenotype, providing a mass-aware framework for virtual-cell modeling and perturbation cell fate design.