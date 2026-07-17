---
title: CAR T cell foundation model predicts immunotherapy response
title_zh: CAR T细胞基础模型预测免疫治疗反应
authors: "Li, Y., Fang, D., Mao, C., Wu, X., Luo, Y."
date: 2026-07-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.11.737994v2.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 用于免疫治疗反应预测的单细胞T细胞基础模型
tldr: 单细胞转录组学可解析CAR T细胞状态，但难以直接预测患者治疗反应。现有方法缺乏将基因结构与临床结局整合的预测框架。为此，研究者提出gANCHOR，一种基于层级超图注意力的T细胞基础模型，通过学习通路感知的细胞嵌入并聚合细胞信息以预测反应。在161名患者中，gANCHOR取得了0.87的F1分数，优于现有模型，并识别出与疗效和耐药性相关的可解释基因程序，为免疫治疗提供了新的预测工具。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737994-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1463, \"height\": 1455, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737994-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1520, \"height\": 1832, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737994-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1517, \"height\": 1331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737994-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1515, \"height\": 1315, \"label\": \"Figure\"}]"
motivation: 现有单细胞CAR T研究难以将细胞异质性信号转化为患者水平反应预测，缺乏整合基因结构与临床结局的框架。
method: 提出gANCHOR，基于层级超图注意力框架，编码基因-通路关系，学习通路感知细胞嵌入，并通过细胞到患者注意力模块预测治疗反应。
result: 在5项CAR T研究的161名患者中，gANCHOR取得F1 0.87，优于基准单细胞基础模型，且生物保守性和批次校正表现最佳。
conclusion: gANCHOR可准确预测免疫治疗反应并识别可解释的基因程序，有助于理解CAR T细胞疗效与耐药机制。
---

## 摘要
单细胞转录组学解析了CAR T细胞的状态，但将异质性细胞信号转化为患者水平的治疗反应仍然具有挑战性。现有研究主要通过实验和统计分析识别与反应相关的基因或细胞群，但很少有预测框架将基因水平结构与临床结果相结合。在此，我们提出gANCHOR，一个基于分层超图注意力框架的T细胞基础模型，结合了生物学信息表示学习和患者水平反应预测。通过编码基因-通路关系，gANCHOR学习通路感知的细胞嵌入，提高了生物学保守性和批次鲁棒性。一个细胞到患者的注意力模块随后聚合细胞信息以推断治疗反应。在基准数据集上，gANCHOR在生物学保守性和批次校正评估中取得了最强的整体性能。在来自五项CAR T细胞研究的161名患者的反应预测中，gANCHOR达到了0.87的F1分数，优于基准的单细胞基础模型。gANCHOR还识别了可重复的反应相关和非反应相关基因程序，为CAR T细胞的疗效和耐药性提供了可解释的生物学见解。

## Abstract
Single-cell transcriptomics resolves CAR T-cell states, yet translating heterogeneous cellular signals into patient-level therapeutic response remains challenging. Existing studies primarily identify response-associated genes or cell populations through experimental and statistical analyses, but few predictive frameworks integrate gene-level structure with clinical outcomes. Here, we present gANCHOR, a T-cell foundation model built on a hierarchical hypergraph attention framework combining biologically informed representation learning with patient-level response prediction. By encoding gene-pathway relationships, gANCHOR learns pathway-aware cell embeddings that improve biological conservation and batch robustness. A cell-to-patient attention module then aggregates cellular information to infer therapeutic response. Across benchmark datasets, gANCHOR achieved the strongest overall performance in biological conservation and batch-correction assessments. In response prediction across 161 patients from five CAR T-cell studies, gANCHOR achieved an F1 score of 0.87, outperforming benchmarked single-cell foundation models. gANCHOR also identified reproducible response- and non-response-associated gene programs, providing interpretable biological insights into CAR T-cell efficacy and resistance.