---
title: Artificial intelligence virtual cell immune recovery model for screening traditional Chinese medicine ingredients
title_zh: 人工智能虚拟细胞免疫恢复模型用于筛选中药成分
authors: "Hu, C., Xiao, B., Chen, C. Y.-C."
date: 2026-07-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.16.732528v2.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 用于免疫恢复和扰动筛选的AI虚拟细胞模型
tldr: 免疫疾病治疗后恢复路径复杂，传统基于疾病特征逆转的筛选方法不够精准。为此提出ImmuneNavi模型，利用AI虚拟细胞将异质性PBMC数据映射到统一健康免疫坐标系，构建患者谱系特异性的疾病与恢复状态，并建立中药成分扰动库。模型整合基因、通路和转录因子多视图特征，在独立PBMC队列中稳定地按恢复方向排序候选成分。该模型为中药天然产物的实验筛选提供了高效的计算工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 传统方法依赖疾病特征逆转，忽略了免疫恢复的患者和谱系特异性轨迹。
method: 利用AI虚拟细胞构建免疫恢复模型，通过多视图特征整合和成分扰动库匹配进行排序。
result: 在独立PBMC队列中无需重定义即可保持恢复对齐的成分排序。
conclusion: ImmuneNavi提供了一种基于免疫状态测量的中药成分筛选新范式。
---

## 摘要
从单细胞转录组中筛选治疗候选物需要更接近治疗反应而非疾病特征逆转的目标。在免疫疾病中，治疗后的恢复可能遵循患者和谱系特异性的轨迹，而不是简单地沿着治疗前的疾病轴返回。我们开发了ImmuneNavi，一个人工智能虚拟细胞（AIVC）免疫恢复模型，用于从配对的外周血单核细胞（PBMC）数据中对中药成分进行排序。该模型将异质性PBMC队列映射到一个共同的健康免疫坐标系统，构建患者-谱系疾病和恢复状态，并将ITCM治疗-对照谱处理成固定的成分扰动库。患者和成分状态在匹配的基因、通路和转录因子视图中表示，使模型能够将局部转录方向与更稳定的程序级特征相结合。在一个配对治疗队列上训练的匹配器在独立的PBMC队列中保持了与恢复对齐的成分排序，而无需重新定义特征空间、候选集或预处理程序。ImmuneNavi提供了一个AIVC模型，该模型利用配对免疫状态测量来筛选天然产物候选物，用于后续实验验证。

## Abstract
Screening therapeutic candidates from single-cell transcriptomes requires a target that is closer to treatment response than disease-signature reversal. In immune diseases, post-treatment recovery may follow patient- and lineage-specific trajectories rather than a simple return along the pretreatment disease axis. We developed ImmuneNavi, an artificial intelligence virtual cell (AIVC) immune recovery model for ranking traditional Chinese medicine ingredients from paired PBMC data. The model maps heterogeneous PBMC cohorts to a common healthy immune coordinate system, constructs patient-lineage disease and recovery states, and processes ITCM treated-control profiles into a fixed ingredient perturbation bank. Patient and ingredient states are represented in matched gene, pathway and transcription-factor views, allowing the model to combine local transcriptional direction with more stable program-level features. A matcher trained on one paired treatment cohort preserved recovery-aligned ingredient rankings in independent PBMC cohorts without redefining the feature space, candidate set or preprocessing procedure. ImmuneNavi provides an AIVC model that uses paired immune-state measurements to screen natural-product candidates for experimental follow-up.