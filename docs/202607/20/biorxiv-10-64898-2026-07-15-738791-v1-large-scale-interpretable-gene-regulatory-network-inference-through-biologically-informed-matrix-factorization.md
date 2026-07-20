---
title: "Large-scale, interpretable gene regulatory network inference through biologically informed matrix factorization"
title_zh: 基于生物信息矩阵分解的大规模、可解释基因调控网络推断
authors: "Micheletti, S., Fanfani, V., Vogt, J., Quackenbush, J., Fischer, J., Marx, A., Mandros, P."
date: 2026-07-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.15.738791v1.full.pdf"
tags: ["query:virtual-cell"]
score: 7.0
evidence: 基因调控网络推断用于建模扰动效应
tldr: 基因调控网络推断是理解细胞身份的关键，但现有方法多聚焦于调控证据而非效应方向。Giraffe通过生物信息矩阵分解，整合基因表达、基序先验和转录因子蛋白互作，估计带符号的部分调控效应。在合成数据、六个人类组织、酵母扰动实验和肝癌数据中，Giraffe准确重建网络并高区分激活与抑制。其推断的网络捕获组织特异性特征，识别癌症相关调控变化，为机制解释和假设生成提供互补视角。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-15-738791-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1461, \"height\": 876, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-15-738791-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1219, \"height\": 777, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-15-738791-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1397, \"height\": 1612, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-15-738791-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1419, \"height\": 504, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-15-738791-v1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1430, \"height\": 576, \"label\": \"Table\"}]"
motivation: 现有基因调控网络推断方法难以区分激活与抑制，且缺乏可解释的效应估计。
method: Giraffe利用矩阵分解整合表达、基序先验和蛋白互作，估计带符号的部分调控效应。
result: 在合成基准、人类组织、酵母扰动和肝癌数据中准确重建网络，并高精度区分激活与抑制。
conclusion: Giraffe提供可解释的调控方向，有助于理解组织特异性和癌症相关调控程序。
---

## 摘要
基因调控网络（GRN）为理解转录因子如何协调基因表达以建立细胞身份和表型提供了机制框架。整合基因表达与基序衍生的调控先验及其他生物信息来源的方法，通过重建条件特异性调控架构，显著推进了基因调控网络推断。这些方法估计支持调控相互作用的证据，并已在广泛的生物学应用中取得了显著成功。然而，调控网络的互补视角旨在估计这些相互作用对基因表达本身的影响，提供了一个框架，其中调控边可被解释为对转录的激活或抑制作用。

我们开发了Giraffe，一种生物信息矩阵分解框架，通过整合基因表达、基于基序的调控先验和转录因子蛋白质-蛋白质相互作用，联合估计转录因子活性和基因调控网络。Giraffe估计带符号的部分调控效应，其大小和符号可被解释为转录调控的强度和方向。Giraffe直接基于PANDA等方法建立生物学框架，提供了基因调控网络的互补表示，强调机制解释，同时保持可扩展性、灵活性和计算效率。

在合成基准、六个人体组织、酵母转录因子扰动实验和肝细胞癌中，Giraffe准确重构调控相互作用，同时高精度区分激活与抑制性调控。推断的网络恢复了组织特异性调控的已知特征，正确分类了转录因子扰动实验中的调控效应，并识别了与肝癌相关的调控程序的生物学一致性变化。这些结果共同表明，估计转录调控方向为基因调控网络提供了互补视角，有助于生物学解释和假设生成。

## Abstract
Gene regulatory networks (GRNs) provide a mechanistic framework for understanding how transcription factors coordinate gene expression to establish cellular identity and phenotype. Methods that integrate gene expression with motif-derived regulatory priors and other sources of biological information have substantially advanced gene regulatory network inference by reconstructing condition-specific regulatory architecture. These approaches estimate the evidence supporting regulatory interactions and have proven remarkably successful in a wide range of biological applications. A complementary view of regulatory networks, however, seeks to estimate the effect of those interactions on gene expression itself, providing a framework in which regulatory edges can be interpreted as activating or inhibitory influences on transcription.

We developed Giraffe, a biologically informed matrix factorization framework that jointly estimates transcription factor activities and gene regulatory networks by integrating gene expression, motif-based regulatory priors, and transcription factor protein-protein interactions. Giraffe estimates signed partial regulatory effects whose magnitude and sign can be interpreted as the strength and direction of transcriptional regulation. Building directly on the biological framework established by methods such as PANDA, Giraffe provides a complementary representation of gene regulatory networks that emphasizes mechanistic interpretation while remaining scalable, flexible, and computationally efficient.

Across synthetic benchmarks, six human tissues, yeast transcription factor perturbation experiments, and liver hepatocellular carcinoma, Giraffe accurately reconstructs regulatory interactions while distinguishing activating from inhibitory regulation with high accuracy. The inferred networks recover known features of tissue-specific regulation, correctly classify regulatory effects in transcription factor perturbation experiments, and identify biologically coherent changes in regulatory programs associated with liver cancer. Together, these results demonstrate that estimating the direction of transcriptional regulation provides a complementary perspective on gene regulatory networks that facilitates biological interpretation and hypothesis generation.