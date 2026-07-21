---
title: A hybrid machine learning and enzyme-constrained metabolic model for ab initio prediction of proteome reallocation
title_zh: 一种混合机器学习和酶约束代谢模型用于从头预测蛋白质组重新分配
authors: "Motamedian, E., Nikoloski, Z."
date: 2026-07-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.20.739489v1.full.pdf"
tags: ["query:virtual-cell"]
score: 7.0
evidence: 预测异源蛋白表达下的蛋白质组重新分配作为扰动响应
tldr: 异源蛋白高表达引发细胞蛋白质组重分配负担，传统模型难以从头预测。本文提出HyTT框架，结合多变量自适应回归样条与酶约束代谢模型，并施加80S核糖体完整性约束，形成混合整数线性规划。在酿酒酵母稳态恒化器数据验证中，HyTT预测蛋白质丰度精度达Pearson r=0.501，准确捕捉资源重分配及Crabtree效应。该框架无需条件特异性多组学数据，提供敏捷计算平台指导理性菌株设计。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739489-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1491, \"height\": 1568, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739489-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1670, \"height\": 896, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739489-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1633, \"height\": 874, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739489-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1689, \"height\": 824, \"label\": \"Figure\"}]"
motivation: 传统约束模型依赖条件特异性组学数据，无法从头预测异源蛋白表达引发的资源重分配。
method: 提出HyTT框架，耦合MARS与酶约束代谢模型，施加80S核糖体完整性约束，通过二分搜索求解混合整数线性规划。
result: 在酿酒酵母上预测蛋白质丰度精度提升（Pearson r=0.501），准确模拟重组蛋白负担下的生长抑制、核糖体比例下降和乙醇产量激增。
conclusion: HyTT提供序列驱动的计算平台，无需条件特异性多组学数据即可解码动态资源重分配，指导代谢工程菌株设计。
---

## 摘要
微生物细胞工厂中异源蛋白的高表达常因有限细胞蛋白质组的重新分配而引发严重负担。传统的约束模型难以在不依赖条件特异性组学数据的情况下从头预测这些资源变化。为弥补这一差距，我们开发了混合转录-翻译（HyTT）框架，通过强制执行80S核糖体完整性约束，将多元自适应回归样条（MARS）与酶约束代谢模型相结合。HyTT以混合整数线性规划问题形式，通过二分搜索数学上将宏观空间边界与微观序列衍生的翻译成本耦合起来。针对稳态恒化器定量蛋白质组学数据的验证表明，HyTT在预测酿酒酵母全系统资源（重新）分配方面优于竞争模型。从头运行该框架，与常规模型相比，蛋白质丰度的预测精度翻倍（皮尔逊r=0.501），成功将最小必需蛋白质组与细胞储备库区分开。关键的是，HyTT自主捕获对代谢工程至关重要的复杂应激反应。在模拟15%重组蛋白负荷时，该框架准确预测了系统性生长迟滞、核糖体蛋白质组比例下降以及乙醇产量激增，与Crabtree效应一致。系统级分析揭示，细胞通过非均匀代谢重排适应受限的蛋白质组容量，下调呼吸复合物以支持高周转率的糖酵解酶，并依赖核糖体旁系同源物切换以最小化序列特异性组装成本。最终，HyTT提供了一个计算敏捷、序列驱动的平台，用于解码动态资源重新分配，为导航代谢权衡和指导理性菌株设计提供了强大的预测工具，无需条件特异性多组学输入。

## Abstract
High expression of heterologous proteins in microbial cell factories frequently triggers a severe burden due to reallocation of finite cellular proteome. Conventional constraint-based models struggle to predict these resource shifts ab initio without relying on condition-specific omics data. To bridge this gap, we developed the Hybrid Transcription-Translation (HyTT) framework, combining multivariate adaptive regression splines (MARS) with enzyme-constrained metabolic models by enforcing an 80S ribosome integrity constraint. Cast as a mixed-integer linear programming problem, HyTT mathematically couples macroscopic spatial boundaries with microscopic, sequence-derived translational costs based on a bisection search. Validation against steady-state chemostat quantitative proteomics data demonstrated the superior capability of HyTT over contenders in predicting system-wide resource (re)allocation in Saccharomyces cerevisiae. Operating ab initio, the framework doubled the predictive accuracy of protein abundances (Pearson r=0.501) compared to conventional models, successfully segregating the minimal essential proteome from the cellular reserve pool. Crucially, HyTT autonomously captures complex stress responses vital for metabolic engineering. Upon simulating a 15% recombinant protein burden, the framework accurately predicted systemic growth retardation, decrease of ribosomal portion of the proteome, and surge of ethanol production, in line with the Crabtree effect. System-level analysis uncovered that cells adapt to restricted proteomic capacity through non-uniform metabolic rerouting, downregulating respiratory complexes in favor of high-turnover glycolytic enzymes, and relying on ribosomal paralog switching to minimize sequence-specific assembly costs. Ultimately, HyTT provides a computationally agile, sequence-driven platform for decoding dynamic resource reallocation, offering a powerful predictive tool to navigate metabolic trade-offs and guide rational strain design without requiring condition-specific multi-omics inputs.