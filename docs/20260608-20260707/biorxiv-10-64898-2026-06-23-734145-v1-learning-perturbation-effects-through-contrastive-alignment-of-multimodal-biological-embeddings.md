---
title: Learning Perturbation Effects Through Contrastive Alignment of Multimodal Biological Embeddings
title_zh: 通过多模态生物嵌入的对比对齐学习扰动效应
authors: "Long, W., Liu, T., Szalata, A., Theis, F. J., Xue, L., Zhao, H."
date: 2026-06-26
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.23.734145v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 多模态对比对齐学习单细胞屏幕中的扰动效应
tldr: 多模态单细胞扰动数据缺乏通用表示学习方法。PertOmni采用CLIP式对比学习对齐转录组、文本和图像嵌入，通过掩膜对比目标增强细胞类型特异性。在双向检索、药物-基因交互和扰动预测任务上优于基线。该框架可跨数据集和扰动类型泛化。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法针对单一模态，未能利用外部语义知识，跨数据集和扰动类型的泛化能力有限。
method: 提出PertOmni，联合训练共享转录组编码器和数据集特定文本编码器，使用掩膜对比目标强调细胞类型内区分。
result: 在双向检索、药物-基因交互推断和扰动预测任务上持续优于强基线方法。
conclusion: PertOmni通过多模态对齐实现跨数据集和扰动类型的有效表示学习，提升泛化能力。
---

## 摘要
多模态单细胞扰动筛选为表征遗传和化学干预对细胞状态的影响提供了一种可扩展的方法。然而，大多数现有的表示学习方法针对单一扰动模态，未能明确整合外部语义知识，这限制了它们跨数据集和扰动类型的泛化能力。在此，我们提出PertOmni，一种CLIP风格的多模态表示学习框架，该框架将转录组扰动签名与经过筛选的基因和化合物描述的文本嵌入，以及来自细胞绘画的图像嵌入进行对齐。PertOmni联合训练一个共享的转录组编码器和数据集特定的文本编码器，使用一种掩码对比目标，强调细胞类型内的区分，同时减轻细胞类型异质性引起的混杂效应。我们在小分子和CRISPRi扰动数据集上评估了生成的联合嵌入空间，应用于双向检索、药物-基因相互作用推断和扰动预测，并展示出相对于强基线方法的一致改进。

## Abstract
Multimodal single-cell perturbation screens offer a scalable approach for characterizing the effects of genetic and chemical interventions on cellular state. However, most existing representation-learning methods are tailored to a single perturbation modality and fail to explicitly incorporate external semantic knowledge, which limits their ability to generalize across datasets and perturbation types. Here, we introduce PertOmni, a CLIP-style multimodal representation-learning framework that aligns transcriptomic perturbation signatures with text-derived embeddings of curated genes and compound descriptions, as well as image-derived embeddings from cell paintings. PertOmni jointly trains a shared transcriptomic encoder and dataset-specific text encoders using a masked contrastive objective that emphasizes within-cell-type discrimination while mitigating confounding effects arising from cell-type heterogeneity. We evaluate the produced joint embedding space on bi-directional retrieval, drug-gene interaction inference, and perturbation prediction across both small-molecule and CRISPRi perturbation datasets, and demonstrate consistent improvements over strong baseline methods.