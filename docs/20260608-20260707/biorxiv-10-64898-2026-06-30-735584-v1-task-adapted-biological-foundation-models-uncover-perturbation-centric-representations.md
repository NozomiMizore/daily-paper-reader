---
title: Task-adapted biological foundation models uncover perturbation-centric representations
title_zh: 任务适应的生物基础模型揭示以扰动为中心的表征
authors: "Pareja-Lorente, E., Aloy, P."
date: 2026-07-05
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.30.735584v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 微调基础模型学习扰动中心表示
tldr: "现有生物基础模型主要捕捉细胞状态而非扰动效应。本文通过监督微调scGPT预测扰动身份，将其潜在空间转化为扰动中心表示，在超过300万LINCS L1000扰动图谱上训练。微调嵌入在最近邻恢复（top100内85-100%）和分类准确率（从10-19%提升至25-49%）上大幅提升，并自发捕获化学相似性（AUROC达0.81）、作用机制（Hit@10达100%）等未训练关系。该表示可用于注释近12000种未表征化合物、优先化靶标关联及情境化未知扰动，证明目标驱动适应是重编程生物基础模型的有效策略。"
source: biorxiv
selection_source: fresh_fetch
motivation: 使生物基础模型学习扰动中心表示，以更有效捕获化学和遗传扰动效应而非细胞状态。
method: 在超过300万LINCS L1000扰动图谱上，用监督目标微调预训练scGPT，预测扰动身份。
result: 微调嵌入显著提升扰动分类和近邻恢复，并自发捕获化学相似性、作用机制等未训练关系。
conclusion: 目标驱动适应是重编程生物基础模型学习复杂生物现象可复用表示的有效策略。
---

## 摘要
基础模型已成为学习生物系统可迁移表征的强大工具，但其潜在空间通常被优化以捕捉细胞状态而非扰动的效果。在此，我们证明通过改变学习目标，可以重新利用生物基础模型学习根本不同的表征。我们使用监督目标对scGPT（一个在超过3000万个单细胞转录组上预训练的Transformer）在超过300万个LINCS L1000扰动谱上进行微调，以预测扰动身份。这将潜在空间转变为以扰动为中心的表征，使由相同化学或遗传扰动在异质实验条件下诱导的转录响应对齐。微调后的嵌入显著优于基因表达谱和原始预训练模型，在前100个最近邻中恢复了[85%, 100%]的扰动，并将扰动分类准确率从[10%, 19%]提高到[25%, 49%]。值得注意的是，尽管该模型仅专门训练以识别扰动身份，但学习到的表征自发捕捉了训练中从未提供过的正交生物关系，包括化学相似性（AUROC高达0.81）、作用机制（Hit@10高达100%）、化合物靶标关系（AUROC高达0.74）以及遗传扰动之间的功能关系。由此产生的嵌入空间能够对近12,000种先前未表征的化合物进行作用机制注释，优先考虑靶标相关的化学遗传关联，并对未见过的扰动和外部转录组数据集进行情境化。总之，我们的结果确立了目标驱动适应作为重新利用生物基础模型来学习复杂生物现象可重用表征的通用策略。

## Abstract
Foundation models have emerged as powerful tools for learning transferable representations of biological systems, yet their latent spaces are typically optimized to capture cellular state rather than the effects of perturbations. Here, we demonstrate that a biological foundation model can be repurposed to learn a fundamentally different representation by changing its learning objective. We finetuned scGPT, a transformer pre-trained on over 30 million single cell transcriptomes, on more than three million LINCS L1000 perturbation profiles using a supervised objective that predicts perturbation identity. This transformed the latent space into a perturbation centric representation that aligned transcriptional responses induced by the same chemical or genetic perturbation across heterogeneous experimental conditions. Finetuned embeddings substantially outperformed both gene expression profiles and the original pretrained model, recovering [85, 100%] of perturbations within the top 100 nearest neighbors and increasing perturbation classification accuracy from [10, 19%] to [25, 49%]. Remarkably, although the model was trained exclusively to recognize perturbation identity, the learned representation spontaneously captured orthogonal biological relationships never provided during training, including chemical similarity (AUROC up to 0.81), mechanisms of action (Hit@10 up to 100%), compound target relationships (AUROC up to 0.74), and functional relationships between genetic perturbations. The resulting embedding space enabled mechanism-of-action annotation of nearly 12,000 previously uncharacterized compounds, prioritization of target related chemical genetic associations, and contextualization of unseen perturbations and external transcriptomic datasets. Together, our results establish objective-driven adaptation as a general strategy for repurposing biological foundation models to learn reusable representations of complex biological phenomena.