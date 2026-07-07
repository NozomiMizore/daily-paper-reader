---
title: "Back to basics: Observed statistics are sufficient to predict drug responses"
title_zh: 回归基础：观测统计量足以预测药物反应
authors: "Svensson, V., Khan, U., Heydari, H., Ubas, A. A., Thomas, N., Merico, D., Goodarzi, H., Yu, J., Alidoust, N., Gandhi, S."
date: 2026-06-12
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.09.731197v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 直接提出扰动响应预测器Rhaister
tldr: 预测细胞对药物、细胞因子等扰动的响应是生物和临床推理的核心。现有虚拟细胞模型成本高，而Rhaister直接利用屏幕级汇总统计量，通过学习参考情境间响应模式的变化，仅需少量新情境的扰动测量即可预测未测扰动。在转录组和表型数据上，Rhaister训练仅数秒、预测毫秒级，性能匹配甚至超越昂贵模型，在评估指标上常达最优。研究还引入基于基线表达的零样本预测模型Rhaister-O，为药物响应预测提供快速、可解释的新框架。
source: biorxiv
selection_source: fresh_fetch
motivation: 传统虚拟细胞模型昂贵且慢，需简化方法，利用统计量直接预测扰动响应。
method: Rhaister通过学习参考情境中响应模式变化，从新情境少量已知扰动预测所有未测扰动，支持分子和表型终点。
result: 在Tahoe-100M和Emerald Bay数据集上，Rhaister训练数秒、预测毫秒，性能超越或持平虚拟细胞模型，常达最优指标。
conclusion: 总结统计量扰动建模是快速、可解释的预测生物响应的有效框架，并首次实现零样本预测。
---

## 摘要
预测细胞、组织及患者对药物、细胞因子或遗传扰动的反应，是生物学与临床推理的核心。实际目标在于估计可用于支持这一推理的分析就绪型读数：哪些细胞反应依赖于环境，哪些扰动揭示了共享或分化的机制，以及哪些观察结果应成为下一实验的基础。

我们在此介绍Rhaister，一种直接基于筛选级别汇总统计量进行扰动-反应预测的模型。通过在新生物学背景下仅测量少数扰动，Rhaister通过学习反应模式在不同参考背景间的变化来预测未测量的扰动。这一公式既适用于细粒度的分子读数（如来自Tahoe-100M或其他大规模扰动筛选的转录反应），也适用于表型终点。为了在表型终点上训练和应用Rhaister，我们创建了Emerald Bay，一个专门构建的Tahoe数据集，它统一了多日癌症药物扰动、混合Mosaic肿瘤背景及配对的转录组反应测量数据。

在这些设置中，Rhaister匹配或超越了成本显著更高的虚拟细胞模型，通常在评估指标上达到可能的最佳值，同时训练仅需数秒，预测运行仅需毫秒。在Emerald Bay上，Rhaister仅凭敏感性测量即可预测环境特异性药物表型，并在加入转录组信息后进一步提升。我们还引入了Rhaister-O，它仅凭基线表达即可预测新背景下的药物反应，据我们所知，这是该任务的第一个零样本模型。Rhaister将汇总统计量扰动建模确立为一种快速、可解释的框架，用于预测跨新背景的生物学反应。

## Abstract
Predicting how cells, tissues, and patients will respond to a drug, cytokine, or genetic perturbation is central to biological and clinical reasoning. The practical goal is to estimate the analysis-ready readouts that support this reasoning: which cellular responses are context-dependent, which perturbations reveal shared or divergent mechanisms, and which observations should become the basis for the next experiment.

Here we introduce Rhaister, a perturbation-response predictor that operates directly on screen-level summary statistics. By measuring just a few perturbations in a new biological context, Rhaister predicts the unmeasured perturbations by learning how response patterns vary across reference contexts. This formulation applies to both fine-grained molecular readouts, such as transcriptional responses from Tahoe-100M or other large perturbation screen, or on phenotypic endpoints. To train and apply Rhaister on pheno-typic endpoints we created Emerald Bay, a purpose-built Tahoe dataset that unifies multi-day cancer drug perturbation, pooled Mosaic tumor contexts, and paired transcriptomic response measurements*.

Across these settings, Rhaister matches or exceeds substantially more expensive virtual-cell models, often achieving the highest values possible in evaluation metrics, while training in seconds and running predictions in milliseconds. On Emerald Bay, Rhaister predicts context-specific drug phenotypes from sensitivity measurements alone and improves further when including transcriptomic information. We also introduce Rhaister-O, predicting drug responses in new contexts from baseline expression alone and, to our knowledge, provides the first zero-shot model for this task. Rhaister establishes summary-statistic perturbation modeling as a fast, interpretable framework for predicting biological response across new contexts.