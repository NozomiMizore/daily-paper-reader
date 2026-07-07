---
title: Robust causal gene network estimation for large-scale single-cell perturbation screens using reduced control function
title_zh: 使用简化控制函数的大规模单细胞扰动筛选的稳健因果基因网络估计
authors: "Ge, C., Li, H."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.20.719759v2.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 从单细胞CRISPR扰动筛选中进行因果网络估计
tldr: 单细胞CRISPR扰动筛选可用于基因调控网络的因果发现，但现存方法面临潜在混杂、计数型表达数据和高感染复数设计的挑战。本文提出RICE框架，通过针对网络估计改进的控制函数、约束负二项模型和可微无环惩罚，统一解决这些问题。在合成数据和CRISPRi筛选中，RICE优于现有方法，稳定重建干扰素-γ信号通路并提名稳定候选调控因子。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有因果网络估计方法难以同时处理潜在混杂、计数型表达和高感染复数设计。
method: RICE融合了改进的控制函数、约束负二项模型和可微无环惩罚，支持硬干预和软干预。
result: 在合成数据中RICE表现最优，在CRISPRi筛选和干扰素-γ通路重建中验证了有效性。
conclusion: RICE为单细胞扰动基因组学提供了稳健可扩展的因果发现框架。
---

## 摘要
单细胞CRISPR扰动筛选为基因调控网络中的因果发现提供了基础，但现有方法难以处理潜在混杂、计数型表达数据和高多重感染（high-MOI）设计。我们提出了RICE，一个统一框架，同时解决这三个挑战。其核心是针对网络估计场景重新表述的控制函数，该函数恢复了对真实CRISPR筛选中普遍存在且导致标准控制函数方法失效的排他性约束违反的稳健性。RICE将该估计量与约束负二项模型和可微无环性惩罚配对，适应硬干预和软干预，并在单个GPU可扩展模型中原生支持高MOI设计。在广泛的合成基准测试中，RICE始终优于现有方法，并在强混杂、排他性违反和高MOI条件下保持稳定。应用于CRISPRi筛选时，RICE在留出数据上实现了更强的因果发现性能。RICE进一步重构了免疫刺激后黑色素瘤细胞中的经典干扰素（IFN）-γ信号通路，并提名了由于统计功效有限而可能被常规显著性检验忽略的稳定调控候选基因。这些结果共同确立了RICE作为单细胞扰动基因组学中因果发现的稳健且可扩展的框架。

## Abstract
Single-cell CRISPR perturbation screens provide a foundation for causal discovery in gene regulatory networks, but existing methods struggle with latent confounding, count-valued expression data, and high-multiplicity-of-infection (high-MOI) designs. We introduce RICE, a unified framework that addresses all three challenges. At its core is a reformulated control function tailored to the network-estimation setting, which restores robustness to exclusion-restriction violations that are pervasive in real CRISPR screens and that cause standard control function approaches to fail. RICE pairs this estimator with a constrained negative binomial model and a differentiable acyclicity penalty, accommodating hard and soft interventions and natively supporting high-MOI designs within a single, GPU-scalable model. Across extensive synthetic benchmarks, RICE consistently outperforms existing methods and remains stable under strong confounding, exclusion violations, and high-MOI conditions. Applied to CRISPRi screens, RICE achieves stronger causal-discovery performance on held-out data. RICE further reconstructs the canonical interferon (IFN)-{gamma} signaling pathway in melanoma cells upon immune stimulation, and nominates stable regulatory candidates that conventional significance tests may overlook due to limited statistical power. Together, these results establish RICE as a robust and scalable framework for causal discovery in single-cell perturbation genomics.