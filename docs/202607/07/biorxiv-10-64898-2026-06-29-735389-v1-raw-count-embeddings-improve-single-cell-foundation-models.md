---
title: Raw-count embeddings improve single-cell foundation models
title_zh: 原始计数嵌入改进单细胞基础模型
authors: "Schlede, S., Muruganandan, T. P., Gojjam Kantharaju, S., Kisis, I., Boecker, M., Kim Alves Carpinteiro, M., Schmitz, A., Buchwald, L. M., Sakthivelu, V., Gülcüler Balta, G. S., Anstötz, M., Rueger, M. A., Thomas, R. K., Beleggia, F."
date: 2026-07-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.29.735389v1.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 改进了单细胞基础模型，可应用于扰动响应分析
tldr: 当前单细胞Transformer基础模型参数庞大，但预处理流程（如基因排序、文库大小归一化）未经系统评估。本文测试七种策略，发现非归一化的log变换计数表现最佳，基因顺序几乎不影响性能，随机顺序甚至优于复杂排序。基于此的Gene Intelligence模型直接使用log1p转换的原始计数，无需归一化、位置编码或读深度token，在基因级任务和双细胞检测中达到最先进，并在细胞分类任务中匹配大型模型，参数量减少10到200倍。
source: biorxiv
selection_source: fresh_fetch
motivation: 针对单细胞Transformer模型预处理选择缺乏系统评估的问题，探究基因排序与归一化的必要性。
method: 测试七种预处理策略，提出直接使用log1p原始计数、无归一化的Gene Intelligence模型。
result: 非归一化log计数表现最佳，基因顺序不重要；Gene Intelligence在多数任务达SOTA，参数量减少10-200倍。
conclusion: 简化预处理可显著提升模型性能，为构建高效单细胞基础模型提供新范式。
---

## 摘要
单细胞Transformer基础模型已发展到拥有数亿参数，但其背后的预处理选择（包括基因排序和文库大小归一化）尚未经过系统性的基准测试。通过测试七种策略，我们发现这些精细化处理大多是不必要的：未归一化的对数转换计数提供了最佳性能，而基因顺序几乎无关紧要，甚至随机排序也优于复杂的基于排序的方案。由此产生的模型——Gene Intelligence，直接将log1p转换的原始计数投射到每个token嵌入上，并联合预测掩码token和计数，不使用归一化、位置编码或读取深度令牌。尽管结构简单，它在测试的基因级任务和双细胞检测中达到了最先进的性能，并在细胞分类任务上与当前大型基础模型相当，同时使用了少10到200倍的参数。

## Abstract
Single-cell transformer foundation models have grown to hundreds of millions of parameters, yet the preprocessing choices that underlie them, including gene ranking and library-size normalisation, have not been systematically benchmarked. Testing seven strategies, we find these elaborations are largely unnecessary: non-normalised, log-transformed counts give the best performance, and gene order barely matters, with even random ordering outperforming sophisticated rank-based schemes. The resulting model, Gene Intelligence, projects log1p-transformed raw counts directly onto each token embedding and jointly predicts masked tokens and counts, using no normalisation, positional encoding, or read-depth tokens. Despite this simplicity, it achieves state-of-the-art performance in the tested gene-level tasks and in doublet detection, and matches large current foundation models on cell-classification tasks while using 10-to 200-fold fewer parameters.