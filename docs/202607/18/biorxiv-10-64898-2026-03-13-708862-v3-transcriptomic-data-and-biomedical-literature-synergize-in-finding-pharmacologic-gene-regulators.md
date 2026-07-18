---
title: Transcriptomic data and biomedical literature synergize in finding pharmacologic gene regulators
title_zh: 转录组数据与生物医学文献协同作用寻找药理基因调控因子
authors: "Deisseroth, C. A., Brazelton, B., Shaik, Z., Sandberg, B. S., Liu, Z., Zoghbi, H. Y."
date: 2026-07-15
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.13.708862v3.full.pdf"
tags: ["query:virtual-cell"]
score: 7.0
evidence: 利用转录组数据和文献自动挖掘基因敲除/敲降等扰动实验的药物调控因子
tldr: 多数由单一基因产物缺乏或过量导致的疾病缺乏靶向治疗，而基因敲除/敲低模型可用于药物筛选。本文引入SNACKKSS，它自动从GEO中筛选基因干扰和药物处理研究，结合均匀计算的RNA-Seq数据直接进行调控关系预测。交叉验证表明其变体SA4在寻找蛋白抑制化合物方面具有独特贡献，且与现有预测工具集成效果更优。该工作支持将自动筛选的RNA-Seq特征与文献及共表达预测整合，用于药物重定位优先级评估。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-13-708862-v3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1963, \"height\": 990, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-13-708862-v3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1405, \"height\": 1384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-13-708862-v3/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1971, \"height\": 1983, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-13-708862-v3/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1949, \"height\": 991, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-03-13-708862-v3/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1704, \"height\": 400, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-03-13-708862-v3/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1709, \"height\": 669, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-03-13-708862-v3/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1973, \"height\": 563, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-03-13-708862-v3/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1897, \"height\": 887, \"label\": \"Table\"}]"
motivation: 利用自动筛选的转录组数据与生物医学文献协同，为缺乏靶向治疗的基因相关疾病发现潜在药物。
method: 提出SNACKKSS，自动从GEO中筛选基因敲除、敲低及小分子处理研究，结合均匀计算的RNA-Seq数据直接预测基因调控关系。
result: SA4变体在交叉验证中展现独特贡献，且集成多个预测工具能显著提高药物重定位优先级性能。
conclusion: 自动筛选的RNA-Seq特征与文献及共表达预测工具整合，对药物重定位优先级具有重要价值。
---

## 摘要
大部分由一种基因产物的缺乏或过量引起的疾病缺乏靶向治疗。由于这些疾病可以通过基因过表达、敲除或敲低来建模，因此能够对抗此类扰动转录组效应的药物可能是有希望的治疗候选药物。RNA测序研究可以推动这种药物优先排序，但其用通俗语言编写的标签必须手动注释。因此，我们引入了基于自动筛选敲除、敲低和小分子研究的特征网络（SNACKKSS），它从基因表达综合数据库自动筛选基因干扰和药物治疗研究，并与统一计算的读数计数数据集合作，直接将标签和RNA测序数据输入调控关系预测。通过交叉验证，我们表明SNACKKSS的预测（特别是来自称为“SA4”的变体的预测）在寻找蛋白质抑制化合物方面做出了独特贡献，即使与现有预测因子一起使用时也是如此。我们展示了聚合多个预测工具的好处，并提供了这个强大的集成工具以及SNACKKSS。重要的是，我们建议研究人员在多个设备上测试复杂的机器学习模型，因为硬件架构可能会影响其输出。尽管如此，下游预测能力非常显著，我们的研究结果支持将自动筛选的RNA测序特征与基于文献和共表达的预测因子整合起来，用于药物重新定位的优先排序。

## Abstract
Most disorders caused by a deficiency or excess of one gene product lack targeted therapies. Since these disorders can be modeled with a gene overexpression, knockout, or knockdown, drugs that oppose the transcriptomic effects of such perturbations may be promising therapeutic candidates. RNA-Sequencing (RNA-Seq) studies can fuel this drug-prioritization, but their labels, written in plain language, must be annotated manually. Hence, we introduce Signature-based Networks from Automatically Curated Knockout, Knockdown, and Small-molecule Studies (SNACKKSS), which automatically curates gene-disruption and drug-treatment studies from the Gene Expression Omnibus and, in partnership with uniformly computed read count datasets, feeds the labels and RNA-Seq data directly into regulatory relationship predictions. Through cross-validation, we show that SNACKKSS' predictions (specifically, from a variation called "SA4") make a unique contribution to finding protein-inhibiting compounds, even alongside existing predictors. We demonstrate the benefit of aggregating multiple predictive tools, and provide this powerful ensemble alongside SNACKKSS. Importantly, we advise researchers to test complex machine learning models on multiple devices, since the hardware architecture can affect their output. Nonetheless, the downstream predictive ability was striking, and our findings support the value of integrating automatically curated RNA-Seq signatures with literature- and co-expression-based predictors for drug-repurposing prioritization.