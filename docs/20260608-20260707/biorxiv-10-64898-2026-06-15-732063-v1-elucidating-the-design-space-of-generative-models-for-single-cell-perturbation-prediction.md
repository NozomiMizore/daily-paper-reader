---
title: Elucidating the Design Space of Generative Models for Single-Cell Perturbation Prediction
title_zh: 阐明单细胞扰动预测生成模型的设计空间
authors: "Bhattacharya, S., Gensbigler, C., Karim, S., Lees, J."
date: 2026-06-18
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.15.732063v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 单细胞扰动预测的生成模型
tldr: 单细胞RNA-seq数据缺乏天然基因顺序，直接应用序列预测方法存在左到右偏置。本文提出ExpressionVAE，利用有限标量量化（FSQ）将细胞编码为离散编码序列，并训练扰动条件离散先验。在Replogle和Parse 1M数据集上，eVAE在所有分布指标上达到SOTA，FID和MMD2比连续潜变量基线低3-20倍。消融研究表明离散潜变量本身是关键，解码器预测分布的丰富性将指标分为方差敏感和均值敏感两组。在CRISPRi逆转基准上，eVAE编码器优于UMAP和差异表达，与scGPT相当但数据量更少。
source: biorxiv
selection_source: fresh_fetch
motivation: 单细胞RNA-seq计数缺乏天然基因顺序，直接序列预测存在误导性左到右偏置，需要学习潜在结构提供序信息。
method: 提出ExpressionVAE，使用有限标量量化（FSQ）将细胞压缩为离散编码序列，并训练扰动条件离散先验。
result: 在Replogle和Parse 1M上，分布指标SOTA，Frechet距离和MMD2比连续基线低3-20倍；CRISPRi基准上编码器优于UMAP和差异表达。
conclusion: 离散潜在变量本身是性能提升关键，解码器预测分布丰富性将指标分为方差敏感和均值敏感两组。
---

## 摘要
下一词元预测已在语言领域产生可预测的扩展，但该方案假定序列中的词元具有有意义的顺序。单细胞RNA-seq计数没有自然的基因顺序，因此将方案直接应用于原始表达，会在不合适的从左到右偏向下失效。相反，我们探讨学习到的潜在表示是否能提供该方案所需的结构。我们提出ExpressionVAE（eVAE），一种离散潜在扰动模型，通过有限标量量化（FSQ）瓶颈将每个细胞压缩成短序列的离散编码，并在这些编码上训练一个扰动条件的离散先验。在Replogle和Parse 1M数据集上，eVAE在每项分布指标上均创下新纪录，并在大多数细胞评估扰动指标上领先，弗雷歇距离和MMD2比最强连续潜在基线大约低3至20倍。将先验在自回归与掩蔽离散扩散之间切换，性能几乎相同，表明增益来自离散潜在本身而非先验族。随后，解码器头消融实验揭示了一个单一的设计轴——推理时预测分布的丰富性——它将标准指标分为两组：方差敏感型和均值敏感型，沿该轴方向相反移动。最后，在炎症细胞因子应激下的1,732种扰动的保留CRISPRi逆转基准上，冻结的eVAE编码器优于UMAP和差异表达，并在扰动排序上与scGPT相当，而所用数据却少得多。我们已发布代码。

## Abstract
Next-token prediction has produced predictable scaling in language, but the recipe presumes a sequence of tokens with a meaningful order. Single-cell RNA-seq counts have no natural gene ordering, so applying the recipe directly to raw expression fails under an ill-suited left-to-right bias. We instead ask whether a learned latent can supply the structure the recipe needs. We introduce ExpressionVAE (eVAE), a discrete-latent perturbation model that compresses each cell into a short sequence of discrete codes through a finite-scalar-quantization (FSQ) bottleneck and trains a perturbation-conditioned discrete prior over those codes. On Replogle and Parse 1M, eVAE sets a new state of the art on every distributional metric and leads on most cell-eval perturbation metrics, with Frechet distance and MMD2 roughly 3 to 20x lower than the strongest continuous-latent baseline. Swapping the prior between autoregressive and masked discrete diffusion leaves performance near-identical, isolating the gain to the discrete latent itself rather than the prior family. A decoder-head ablation then exposes a single design axis, the richness of the predictive distribution at inference, that splits the standard metrics into two groups, variance-sensitive and mean-sensitive, which move in opposite directions along the axis. Finally, on a held-out CRISPRi reversion benchmark of 1,732 perturbations under inflammatory cytokine stress, the frozen eVAE encoder outperforms UMAP and differential expression and matches scGPT on perturbation ranking at a fraction of the data.1 We release our code.2