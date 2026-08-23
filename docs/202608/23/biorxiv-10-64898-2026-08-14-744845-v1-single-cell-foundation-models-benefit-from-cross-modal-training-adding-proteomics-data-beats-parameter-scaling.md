---
title: "Single-cell foundation models benefit from cross-modal training: adding proteomics data beats parameter scaling"
title_zh: 单细胞基础模型受益于跨模态训练：加入蛋白质组学数据胜过参数扩展
authors: "Burq, M., Stepec, D., Kim, C., Cimermancic, P."
date: 2026-08-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.14.744845v1.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: "单细胞基础模型跨模态蛋白质组训练,增强虚拟细胞的细胞表示"
tldr: 单细胞基础模型通常只在 RNA 转录组数据上预训练，提升性能依赖扩大模型规模。本文提出跨模态继续预训练方法，将 Tahoe-x1 模型在来自 440 项质谱研究的 48843 个蛋白质组样本上微调一个周期。所得 70M 参数模型在大部分 Tahoe-x1 原始基准上匹配或超过 1B 和 3B 参数的 RNA-only 模型，且在蛋白质扰动迁移任务上表现更好。这表明，有针对性地策展蛋白质组数据比单纯增加参数量更能提升模型质量，多模态预训练有望成为构建更强生物基础模型的关键路径。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有单细胞基础模型主要依靠扩大 RNA 数据规模和参数规模提升性能，缺乏对跨模态数据价值的探索。
method: 提出跨模态继续预训练：将已发布的 Tahoe-x1 模型在来自大量质谱研究的蛋白质组样本上微调一个周期。
result: 七千万参数模型在多数基准上匹配甚至超过十亿和三十亿参数的 RNA-only 模型，并改善蛋白质扰动预测。
conclusion: 结果表明，针对性蛋白质组数据比扩大模型规模更有效，多模态预训练是提升生物基础模型的有力路径。
---

## 摘要
领先的细胞基础模型已在数亿个单细胞转录组上训练，进展日益由更大的数据集和模型扩展驱动。在此，我们探究了在仅扩展RNA模型之外，加入蛋白质组学模态能否改善基因级和细胞级表示。我们引入了跨模态持续预训练，在一个大型蛋白质组学谱语料库上微调已发表的单细胞模型（Tahoe-x1）。在来自440项多样化质谱研究的48843个蛋白质组学样本上，对70M参数的Tahoe-x1模型进行单轮训练，在大多数Tahoe-x1原始评估基准上达到或超过了1B和3B参数的仅RNA模型。这表明，采用正确的训练方案，异质性蛋白质组学数据能够改善单细胞RNA测序样本的学习表示，展现出强大的分布外泛化能力。跨模态预训练还改善了对一个留出的蛋白质扰动基准的迁移，而在该基准上仅扩展RNA模型无法提供相当的收益。这些结果表明，对蛋白质组学数据进行仔细的定向整理能比单独增大模型规模带来更大的收益，并提示多模态预训练是构建更具信息量的生物基础模型的一条有前景的路径。

## Abstract
Leading cellular foundation models have been trained on hundreds of millions of single-cell transcriptomes, with progress increasingly driven by larger datasets and model scaling. Here, we asked whether adding a proteomics modality can improve gene-level and cell-level representations beyond scaling RNA-only models. We introduce cross-modal continued pretraining, fine-tuning a published single-cell model (Tahoe-x1) on a large corpus of proteomic profiles. Training a 70M-parameter Tahoe-x1 model for a single epoch on 48843 proteomic samples from 440 diverse mass-spectrometry studies matched or exceeded 1B- and 3B-parameter RNA-only models across most of the original Tahoe-x1 evaluation benchmarks. This shows that with the right training recipe, heterogeneous proteomics data can improve the learned representations of single-cell RNAseq samples, demonstrating strong out-of-distribution generalization. Cross-modal pretraining also improves transfer to a held-out protein perturbation benchmark, where scaling the RNA-only model does not provide comparable benefits. These results demonstrate that careful targeted curation of proteomics data can provide larger benefits than increasing the model size alone and suggest that multimodal pretraining is a promising path toward more informative biological foundation models.