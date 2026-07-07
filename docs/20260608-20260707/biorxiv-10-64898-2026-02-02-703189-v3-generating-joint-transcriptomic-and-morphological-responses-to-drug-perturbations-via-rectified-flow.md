---
title: Generating Joint Transcriptomic and Morphological Responses to Drug Perturbations via Rectified Flow
title_zh: 通过整流流生成药物扰动的联合转录组和形态反应
authors: "Verma, S., Wang, M., Wang, L., Kadadi, S. D., Sola, M., Kazemian, M., Grama, A., Lanman, N. A."
date: 2026-06-12
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.02.703189v3.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 药物扰动的转录组和形态联合预测
tldr: 现有方法孤立预测药物扰动下的转录组或形态变化，缺乏联合建模。本文提出PertFlow框架，基于整流流同时预测基因表达和生成细胞形态，以对照状态和药物元数据为条件。在3个细胞系40种化合物上，转录组预测皮尔逊相关系数0.780，形态生成FID 24.06，病理学家评分中位数7-8/10，并能恢复已知药物机制。该工作首次实现药物扰动的转录组-形态联合预测，为药物机制解析和筛选提供新工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法孤立建模转录组和形态变化，缺失药物扰动下分子-表型的联合预测关系。
method: 提出PertFlow框架，基于整流流以对照细胞状态和药物元数据为条件，联合预测基因表达和生成细胞形态。
result: 在3细胞系40化合物上，转录组预测Pearson相关系数0.780，形态生成FID 24.06，病理医师评分中位数7.11-7.89/10。
conclusion: PertFlow实现药物扰动下转录组与形态的同步预测，有效恢复微管破坏、DNA损伤等药物机制。
---

## 摘要
动机
预测细胞对药物扰动的反应需要捕捉转录组和形态变化之间的复杂依赖关系。现有方法孤立地建模这些模态，忽略了药物治疗过程中同时发生的关键分子-表型关系。目前没有方法能够从化学扰动中联合预测基因表达谱和细胞形态。

结果
我们提出了PertFlow，一个统一的计算框架，能够同时预测处理后的基因表达（批量RNA-seq）并根据药物元数据从对照细胞状态生成细胞形态（Cell Painting图像）。在来自3个细胞系和40种化合物（17,242个样本）的配对RNA-seq和成像数据上评估，PertFlow在转录组预测上达到了0.780±0.264的皮尔逊相关系数，在形态生成上达到了24.06的FID。经委员会认证的病理学家对生成的图像进行了评分，中位数相似度得分为7.11-7.89/10。该模型成功恢复了已知的药物机制，包括微管破坏、DNA损伤和MAPK通路抑制，基因富集分析证实了预期的生物学通路（EMT、p53、凋亡）的激活。

可用性
代码和预训练模型将在https://github.com/wangmengbo/PertFlow上提供。

## Abstract
MotivationPredicting cellular responses to drug perturbations requires capturing complex dependencies between transcriptomic and morphological changes. Existing approaches model these modalities in isolation, missing critical molecular-phenotypic relationships that occur simultaneously during drug treatment. No current method jointly predicts gene expression profiles and cellular morphology from chemical perturbations.

ResultsWe introduce PertFlow, a unified computational frame-work that simultaneously predicts treatment gene expression (bulk RNA-seq) and generates cellular morphology (Cell Painting images) from control cellular states, conditioned on drug metadata. Evaluated on paired RNA-seq and imaging data from 3 cell lines and 40 compounds (17,242 samples), PertFlow achieves Pearson correlation of 0.780{+/-}0.264 for transcriptomic prediction and FID of 24.06 for morphological generation. Board-certified pathologists rated generated images with median similarity scores of 7.11-7.89/10. The model successfully recovers known drug mechanisms including microtubule disruption, DNA damage, and MAPK pathway inhibition, with gene enrichment analysis confirming activation of expected biological pathways (EMT, p53, apoptosis).

AvailabilityCode and pretrained models will be available at https://github.com/wangmengbo/PertFlow.