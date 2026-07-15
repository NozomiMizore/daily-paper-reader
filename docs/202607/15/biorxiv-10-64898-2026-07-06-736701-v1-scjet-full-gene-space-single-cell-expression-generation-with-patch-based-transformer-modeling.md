---
title: "scJET: Full-gene Space Single-cell Expression Generation with Patch-based Transformer Modeling"
title_zh: "scJET: 基于补丁Transformer建模的全基因空间单细胞表达生成"
authors: "Liang, Q., Lyu, Q. R."
date: 2026-07-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.06.736701v1.full.pdf"
tags: ["query:virtual-cell"]
score: 7.0
evidence: 全基因空间单细胞生成为虚拟细胞模型提供基础
tldr: 现有单细胞生成模型通常依赖高变基因或低维表示，难以捕捉全基因空间复杂性。为解决此问题，提出了scJET，一种基于patch的Transformer去噪框架，直接在全基因空间操作。scJET通过可扩展的patch分词与全基因去噪，能够保留全局流形结构、局部邻域统计和基因表达程序。这为全转录组单细胞矩阵生成提供了高效的新框架。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-06-736701-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 1578, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-06-736701-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1445, \"height\": 1108, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-06-736701-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1456, \"height\": 1728, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-06-736701-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1457, \"height\": 698, \"label\": \"Figure\"}]"
motivation: 现有模型依赖高变基因或低维表示，限制了对全基因特征复杂性的捕捉能力。
method: scJET采用基于patch的Transformer去噪框架，在全基因空间运行，结合可扩展的patch分词与全基因去噪。
result: scJET能保留全局流形结构、局部邻域统计和基因表达程序。
conclusion: 为全转录组单细胞矩阵生成提供了高效的框架。
---

## 摘要
大多数单细胞生成模型依赖于高度可变基因（HVG）或低维潜在表示，限制了其捕获全基因特征复杂性的能力。我们提出了scJET，一种在全基因空间运行的基于补丁的Transformer去噪框架。scJET保留了全局流形结构、局部邻域统计和基因级表达程序。通过将可扩展的补丁令牌化与全基因去噪相结合，scJET为转录组范围单细胞矩阵生成提供了一个高效框架。

## Abstract
Most single-cell generative models rely on highly variable genes (HVGs) or low-dimensional latent representations, limiting their capacity to capture the complexity of full-gene features. We present scJET, a patch-based Transformer denoising framework that operates in full-gene space. scJET preserves global manifold structure, local neighborhood statistics, and gene-level expression programs. By combining scalable patch tokenization with full-gene denoising, scJET provides an efficient framework for transcriptome-wide single-cell matrix generation.