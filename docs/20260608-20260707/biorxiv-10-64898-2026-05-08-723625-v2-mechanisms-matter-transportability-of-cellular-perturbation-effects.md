---
title: "Mechanisms Matter: Transportability of Cellular Perturbation Effects"
title_zh: 机制至关重要：细胞扰动效应的可转移性
authors: "Qi, S.-a., Chapfuwa, P."
date: 2026-07-02
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.08.723625v2.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 利用因果可传递性理论直接预测细胞对遗传或化学扰动的响应
tldr: 细胞对扰动的响应预测在跨生物背景时表现不佳，因为泛化依赖于共享因果机制而非分布相似性。本文基于因果可迁移性理论，构建了具有可调机制差异的半合成Perturb-seq数据模拟器，并引入Vendi多样性评分检测模式崩溃。实验表明，跨背景测试中深度模型性能大幅下降，甚至不及简单基线，揭示对因果归纳偏好的迫切需求。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有深度学习模型在跨背景扰动预测中未能超越简单基线，亟需理解泛化失败的根本原因。
method: 利用因果可迁移性理论，开发包含已知因果结构的半合成数据模拟器，并采用Vendi评分诊断模式崩溃。
result: 跨上下文评估中，所有模型（含深度模型）性能骤降至基线水平，即使完全指定因果结构也无法迁移。
conclusion: 跨背景泛化需要以机制为导向的评估、多样性感知指标和因果归纳偏好的设计。
---

## 摘要
预测细胞对遗传或化学扰动的响应在不同生物学背景下的表现，是药物开发和疾病理解的核心。尽管数据和模型规模有所增加，深度学习模型并未始终优于简单基线。利用因果可运输性理论，我们表明跨背景泛化受共享因果机制驱动，而不仅仅是分布相似性。为了进行受控评估，我们开发了一个因果模拟器，生成具有可调节机制分歧的真实半合成Perturb-seq数据集，并提供已知真实因果结构的基准。此外，我们将Vendi多样性分数适应于扰动设置，作为模式崩溃的诊断工具，而模式崩溃是标准按扰动指标无法观察到的失败模式。在半合成和真实Perturb-seq数据集上对四个深度学习模型和六个简单基线进行的广泛实验揭示了跨背景泛化差距：在跨背景分割下，性能显著下降，通常降至简单基线水平。值得注意的是，即使在具有完全指定因果结构的合成数据上，也没有模型能在不同因果机制的背景下泛化。这些结果强调了跨背景评估、多样性感知指标和基于机制的归纳偏置的必要性。

## Abstract
Predicting cellular responses to genetic or chemical perturbations across biological contexts is central to drug development and disease understanding. Despite increases in data and model scale, deep learning models have not consistently outperformed simple baselines. Leveraging causal transportability theory, we show that cross-context generalization is governed by shared causal mechanisms, not merely distributional similarity. To enable controlled evaluation, we develop a causal simulator that generates realistic semi-synthetic Perturb-seq datasets with tunable mechanistic divergence, providing benchmarks with known ground-truth causal structure. Further, we adapt the Vendi diversity score to the perturbation setting as a diagnostic for mode collapse, a failure mode invisible to standard per-perturbation metrics. Extensive experiments across four deep learning models and six simple baselines on semi-synthetic and real Perturb-seq datasets reveal a cross-context generalization gap: performance under cross-context splits drops substantially, often to simple baseline levels. Notably, even on synthetic data with fully specified causal structure, no model generalized across contexts with different causal mechanisms. These results underscore the need for cross-context evaluation, diversity-aware metrics, and mechanistically grounded inductive biases.