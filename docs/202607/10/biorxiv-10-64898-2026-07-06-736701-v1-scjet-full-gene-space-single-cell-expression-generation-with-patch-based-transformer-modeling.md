---
title: "scJET: Full-gene Space Single-cell Expression Generation with Patch-based Transformer Modeling"
title_zh: "scJET: 基于补丁变换器建模的全基因空间单细胞表达生成"
authors: "Liang, Q., Lyu, Q. R."
date: 2026-07-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.06.736701v1.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 全基因空间单细胞生成模型，可用于扰动响应预测
tldr: 现有单细胞生成模型多依赖高度可变基因或低维表示，难以捕获全基因空间的复杂性。scJET提出基于patch的Transformer去噪框架，在全基因空间进行生成。该框架通过可扩展的patch tokenization实现高效处理，能够保留全局流形结构、局部邻居统计及基因表达程序。scJET为全转录组单细胞矩阵生成提供了高效且保真度高的新范式。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-06-736701-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 1578, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-06-736701-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1445, \"height\": 1108, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-06-736701-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1456, \"height\": 1728, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-06-736701-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1457, \"height\": 698, \"label\": \"Figure\"}]"
motivation: 现有方法依赖高度可变基因或低维表示，限制了全基因特征复杂度的捕获能力。
method: 基于patch的Transformer去噪框架，通过可扩展patch tokenization实现全基因空间操作。
result: scJET在全基因空间生成单细胞表达矩阵，同时保留了全局流形、局部邻居和基因程序。
conclusion: scJET为全转录组单细胞矩阵生成提供了高效且保真度高的框架。
---

## 摘要
大多数单细胞生成模型依赖于高度可变基因（HVGs）或低维潜在表示，限制了它们捕捉全基因特征复杂性的能力。我们提出了scJET，一个基于补丁的变换器去噪框架，在全基因空间中运行。scJET保留了全局流形结构、局部邻域统计和基因级表达程序。通过将可扩展的补丁标记化与全基因去噪相结合，scJET为转录组范围单细胞矩阵生成提供了一个高效的框架。

## Abstract
Most single-cell generative models rely on highly variable genes (HVGs) or low-dimensional latent representations, limiting their capacity to capture the complexity of full-gene features. We present scJET, a patch-based Transformer denoising framework that operates in full-gene space. scJET preserves global manifold structure, local neighborhood statistics, and gene-level expression programs. By combining scalable patch tokenization with full-gene denoising, scJET provides an efficient framework for transcriptome-wide single-cell matrix generation.