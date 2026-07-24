---
title: "scRepresenter: a workflow for computing, integrating and benchmarking cellular representations in single-cell transcriptomics"
title_zh: scRepresenter：单细胞转录组学中计算、整合和基准测试细胞表征的工作流程
authors: "Pocas, G., Umar, M., Davis, O., Hemberg, M., Lamurias, A., Lakatos, A., Asif, M."
date: 2026-07-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.15.738660v1.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 计算单细胞数据细胞表示的工作流，支持下游扰动分析
tldr: 单细胞转录组分析面临数据稀疏和疾病异质性挑战，现有两类表示学习方法（基础模型与知识引导）互补但缺乏统一比较。scRepresenter工作流整合四种细胞嵌入（表达、知识、模型、混合），提供命令行与Shiny交互工具，实现系统性计算、集成与基准测试。该流程以基因表达矩阵为输入，输出可比较的嵌入对象，为复杂疾病研究提供标准化平台。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-15-738660-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 2080, \"height\": 1332, \"label\": \"Figure\"}]"
motivation: 单细胞数据稀疏与疾病异质性导致分析困难，现有表示学习方法缺乏统一比较与集成框架。
method: 开发scRepresenter工作流，集成表达式、知识、基础模型及混合四类嵌入，包含命令行和Shiny交互可视化。
result: 工作流以细胞-基因计数矩阵为输入，输出整合嵌入对象，支持交互式比较与下游分析。
conclusion: 开源工作流scRepresenter提供统一平台，促进复杂疾病中细胞表示的计算与基准测试。
---

## 摘要
摘要：动机：单细胞RNA测序（scRNA-seq）已成为研究复杂疾病的有力工具，此类疾病中影响不同细胞群的瞬时细胞状态刻画了疾病的发生与发展。然而，由于数据稀疏性和疾病异质性，分析通常具有挑战性。随着机器学习的最新进展，学习细胞表征的两种广泛使用的方法应运而生：大规模基础模型和生物知识引导方法。尽管它们具有互补优势，但目前尚无统一的工作流程来系统比较和整合这些方法。结果：本文提出scRepresenter，一个在复杂疾病背景下计算、整合和验证从基础模型和生物知识引导方法中获得的细胞嵌入的开源工作流程。它包含两个组件：一个计算细胞嵌入并执行下游分析的命令行工作流程，以及一个用于可视化和比较计算出的嵌入的交互式Shiny应用程序。scRepresenter支持四类细胞表征：（1）基于表达的，（2）知识引导的，（3）基础模型衍生的，以及（4）结合基础模型衍生表征与知识引导表征的混合嵌入。该方法以细胞-基因计数矩阵为输入，输出包含计算嵌入的整合对象。然后，该对象可上传到我们的交互式Shiny应用程序中以比较不同的嵌入。可用性：工作流程可在https://github.com/GuilhermePocas/scRepresenter获取。联系方式：AL291@cam.ac.uk；MA2129@cam.ac.uk。关键词：单细胞RNA测序，机器学习，表征学习，基础模型，细胞嵌入，复杂疾病，肌萎缩侧索硬化症，人类类器官。

## Abstract
Motivation: Single-cell RNA sequencing (scRNA-seq) has become an attractive tool for studying complex diseases, in which transient cell states affecting diverse cell populations characterise disease development and progression. However, due to data sparsity and disease heterogeneity analysis is often challenging. With recent advances in machine learning, two widely used approaches have emerged for learning cellular representations: large-scale foundation models and biological knowledge-guided methods. Despite their complementary strengths, there is currently no unified workflow for systematically comparing and integrating these approaches. Results: Here, we present scRepresenter, an open-source workflow for computing, integrating, and validating cellular embeddings derived from foundation models and biological knowledge-guided methods in the context of complex diseases. It consists of two components: a command-line workflow that computes cellular embeddings and performs downstream analyses, and an interactive Shiny application for visualizing and comparing the computed embeddings. scRepresenter supports four categories of cellular representations: (1) expression-based, (2) knowledge-guided, (3) foundation model-derived, and (4) hybrid embeddings that combine foundation model-derived representations with knowledge-guided representations. This approach takes a cell-by-gene count matrix as input and outputs an integrated object containing the computed embeddings. Then, this object can be uploaded into our interactive Shiny application to compare different embeddings. Availability: The workflow is available at https://github.com/GuilhermePocas/scRepresenter Contact: AL291@cam.ac.uk; MA2129@cam.ac.uk Keywords: single-cell RNA-sequencing, machine learning, representation learning, foundation models, cellular embeddings, complex diseases, amyotrophic lateral sclerosis, human organoid