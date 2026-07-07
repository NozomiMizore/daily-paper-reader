---
title: Reference-guided immune recovery matching prioritizes traditional Chinese medicine ingredients
title_zh: 参考引导的免疫恢复匹配优先考虑中药成分
authors: "Hu, C., Xiao, B., Chen, C. Y.-C."
date: 2026-06-22
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.16.732528v1.full.pdf"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 提出人工智能虚拟细胞（AIVC）模型用于免疫恢复
tldr: 针对免疫疾病治疗候选物筛选，现有疾病特征逆转方法因忽略恢复轨迹特异性而受限。本文提出ImmuneNavi模型，通过将配对PBMC数据映射到健康免疫坐标系，构建患者谱系特异性疾病与恢复状态，并整合中药成分扰动谱。匹配器经单队列训练后，在独立队列中无需调整即可保持恢复对齐的排序。该方法为天然产物筛选提供了基于免疫恢复方向的优先级排序框架，具有跨队列泛化能力。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法基于疾病特征逆转，但免疫恢复沿谱系特异性轨迹，需更接近治疗反应的靶点匹配。
method: 构建ImmuneNavi人工智能虚拟细胞模型，通过健康免疫坐标映射、疾病与恢复状态构建及中药成分扰动库匹配实现排序。
result: 匹配器在独立PBMC队列中保持恢复对齐的中药成分排名，无需重新定义特征空间或候选集。
conclusion: ImmuneNavi为基于配对免疫状态测量的天然产物筛选提供虚拟细胞模型，可优先推荐实验验证候选物。
---

## 摘要
从单细胞转录组中筛选治疗候选物需要比疾病特征逆转更接近治疗反应的靶点。在免疫疾病中，治疗后恢复可能遵循患者和谱系特异性的轨迹，而不是简单地沿着治疗前疾病轴返回。我们开发了ImmuneNavi，一种人工智能虚拟细胞（AIVC）免疫恢复模型，用于从配对PBMC数据中对中药成分进行排序。该模型将异质性PBMC队列映射到一个共同的健康免疫坐标系，构建患者-谱系疾病和恢复状态，并将ITCM处理-对照概况处理成固定的成分扰动库。患者和成分状态在匹配的基因、通路和转录因子视图中表示，使模型能够将局部转录方向与更稳定的程序级特征相结合。在一个配对治疗队列上训练的匹配器在独立的PBMC队列中保持了与恢复对齐的成分排序，无需重新定义特征空间、候选集或预处理流程。ImmuneNavi提供了一种AIVC模型，利用配对免疫状态测量来筛选天然产物候选物以进行实验跟进。

## Abstract
Screening therapeutic candidates from single-cell transcriptomes requires a target that is closer to treatment response than disease-signature reversal. In immune diseases, post-treatment recovery may follow patient- and lineage-specific trajectories rather than a simple return along the pretreatment disease axis. We developed ImmuneNavi, an artificial intelligence virtual cell (AIVC) immune recovery model for ranking traditional Chinese medicine ingredients from paired PBMC data. The model maps heterogeneous PBMC cohorts to a common healthy immune coordinate system, constructs patient-lineage disease and recovery states, and processes ITCM treated-control profiles into a fixed ingredient perturbation bank. Patient and ingredient states are represented in matched gene, pathway and transcription-factor views, allowing the model to combine local transcriptional direction with more stable program-level features. A matcher trained on one paired treatment cohort preserved recovery-aligned ingredient rankings in independent PBMC cohorts without redefining the feature space, candidate set or preprocessing procedure. ImmuneNavi provides an AIVC model that uses paired immune-state measurements to screen natural-product candidates for experimental follow-up.