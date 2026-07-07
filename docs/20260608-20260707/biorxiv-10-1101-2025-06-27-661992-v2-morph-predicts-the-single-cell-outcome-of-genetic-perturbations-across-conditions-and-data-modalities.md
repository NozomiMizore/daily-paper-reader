---
title: MORPH Predicts the Single-Cell Outcome of Genetic Perturbations Across Conditions and Data Modalities
title_zh: MORPH预测跨条件和数据模态的遗传扰动的单细胞结果
authors: "He, C., Zhang, J., Dahleh, M. A., Uhler, C."
date: 2026-07-01
pdf: "https://www.biorxiv.org/content/10.1101/2025.06.27.661992v2.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 使用模块化VAE和注意力机制预测单细胞遗传扰动响应
tldr: 预测遗传扰动对单细胞的影响是计算生物学难题。本文提出MORPH框架，结合差异变分自编码器和注意力机制，可预测未见过的扰动、组合扰动及新细胞环境下的结果，适用于转录组学和成像数据。注意力机制还能推断基因相互作用网络，学习到的基因嵌入可指导实验设计。MORPH有助于高效探索扰动空间，推动基础研究和治疗应用。
source: biorxiv
selection_source: fresh_fetch
motivation: 实验测量所有基因扰动及其组合在多种细胞类型和条件下的反应成本高昂，亟需能跨数据模态泛化的预测模型。
method: MORPH采用基于差异的变分自编码器与注意力机制相结合，预测对未知扰动的细胞响应。
result: 支持单细胞转录组和成像输出，能泛化到未见扰动、组合扰动及新细胞环境，并推断基因调控网络。
conclusion: MORPH是灵活的扰动实验优化工具，可高效探索扰动空间，助力理解细胞程序并促进治疗应用。
---

## 摘要
建模细胞对遗传扰动的响应是计算生物学中的一个重大挑战。测量所有基因扰动及其在细胞类型和条件上的组合在实验上具有挑战性，这突出了需要能够跨数据类型泛化的预测模型来支持这一任务。这里我们提出MORPH，一个用于预测扰动变化的模块化框架。MORPH结合了基于差异的变分自编码器和注意力机制，以预测细胞对未见扰动的响应。它支持单细胞转录组学和成像输出，并能泛化到未见扰动、扰动组合以及新细胞环境中的扰动。基于注意力的框架能够推断基因相互作用和调控网络，而学习的基因嵌入可以指导信息性扰动的设计，如在两个应用中所展示的。总体而言，MORPH是一个用于优化扰动实验的灵活工具，能够高效探索扰动空间，从而推进对细胞程序的理解，用于基础研究和治疗应用。

## Abstract
Modeling cellular responses to genetic perturbations is a significant challenge in computational biology. Measuring all gene perturbations and their combinations across cell types and conditions is experimentally challenging, highlighting the need for predictive models that generalize across data types to support this task. Here we present MORPH, a MOdular framework for predicting Responses to Perturbational cHanges. MORPH combines a discrepancy-based variational autoencoder with an attention mechanism to predict cellular responses to unseen perturbations. It supports both single-cell transcriptomics and imaging outputs and can generalize to unseen perturbations, combinations of perturbations, and perturbations in new cellular contexts. The attention-based framework enables inference of gene interactions and regulatory networks, while the learned gene embeddings can guide the design of informative perturbations, as demonstrated in two applications. Overall, MORPH is a flexible tool for optimizing perturbation experiments, enabling efficient exploration of the perturbation space to advance understanding of cellular programs for fundamental research and therapeutic applications.