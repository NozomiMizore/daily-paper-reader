---
title: Inferring Protein Variant Impacts Across Contexts
title_zh: 跨情境推断蛋白质变异影响
authors: "Rasoulzadeh Hosseini, A., Senguttuvan, V., van Loggerenberg, W., Border, R., Roth, F. P."
date: 2026-08-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.18.745369v1.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: MAVE变异效应插补与预测遗传扰动结果相关
tldr: 多路复用变异效应检测可测量不同遗传和环境背景下的蛋白质变异影响，但背景空间近乎无限，实验预算有限。研究比较了线性混合效应模型、随机森林和自编码器等多背景插补方法，发现最优方法取决于插补任务和测量密度。灵活模型在数据充足时表现更好，简单模型在稀疏时更可靠，但简单回归无法插补未测量的变异，存在局限。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有预测器未充分利用多背景数据，需高效插补策略扩展上下文变异效应的覆盖范围。
method: 分类多种插补挑战，系统比较线性混合模型、随机森林和自编码器在亚饱和多背景数据上的表现。
result: 插补性能随任务与数据密度变化；简单源到目标回归模型无法处理双方未测变异，灵活模型需充足数据支持。
conclusion: 提出多背景插补的概念框架，为优化实验设计和算法选择提供初始评估，推动大规模上下文相关变异研究。
---

## 摘要
多重变异效应分析（MAVEs）可并行测量大量蛋白质序列变异的功能影响，可能覆盖所有可能的单氨基酸替换。与当前的计算变异效应预测器不同，MAVEs能够揭示不同遗传和环境背景下变异的影响。然而，虽然可能的情境空间实际上是无限的，情境MAVE研究却受到有限实验预算的限制。为了最大化跨情境的覆盖，一种策略是进行亚饱和情境MAVE，然后通过插补填补空白。在此，我们对不同的插补挑战进行分类和比较，探索一系列多情境插补解决方案，包括线性混合效应模型、随机森林和自编码器，并为给定的插补任务应如何最佳推进提供见解。我们发现，最优方法取决于插补任务以及情境测量的密度。当测量丰富时，更灵活的模型表现优异，而当测量稀疏时，最简单的模型被证明最为可靠。然而，简单的源到目标回归模型虽然非常适合插补在源情境中测量的变异得分，但无法插补在任一情境中都未测量的变异得分。当两个图谱都稀疏测量时，这是一个重大局限。我们提供了一个概念框架和对多情境插补方法的初步评估，这些方法可以扩展大规模情境依赖性变异效应研究的范围。

## Abstract
Multiplexed assays of variant effects (MAVEs) measure the functional impact of many protein sequence variants in parallel, potentially covering all possible single amino acid substitutions. Unlike current computational variant effect predictors, MAVEs can reveal the effects of variants under different genetic and environmental contexts. However, whereas the space of possible contexts is effectively infinite, contextual MAVE studies are limited by finite experimental budgets. To maximize coverage across contexts, one strategy is to carry out sub-saturation contextual MAVEs and then fill in the gaps via imputation. Here, we categorize and compare different imputation challenges, explore a collection of multi-context imputation solutions, including linear mixed-effects models, random forests, and autoencoders, and provide insight into how best to proceed for a given imputation task. We find that the optimal method depends on the imputation task and how densely the contexts have been measured. More flexible models excel when measurements are plentiful, whereas the simplest models prove most reliable when measurements are sparse. However, the simple source-to-target regression models, although well suited to imputing scores for variants measured in the source context, cannot impute scores for variants that were not measured in either context. This is a major limitation when both maps are sparsely measured. We provide a conceptual framework and an initial evaluation of multi-context imputation methods that can extend the scope of large-scale studies of context-dependent variant effects.