---
title: Generating whole-brain neural activity and behavior through unified latent dynamics
title_zh: 通过统一潜在动力学生成全脑神经活动和行为
authors: "Nuzzi, D., Mattia, M., Pezzulo, G."
date: 2026-07-14
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.05.730482v2.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 全脑神经活动的生成模型，包含潜在动力学扰动
tldr: 理解高维神经活动和行为如何从共享的底层动力学涌现是神经科学的核心挑战。本文提出NEBULA框架，通过统一潜动力学联合建模全脑神经活动和行为。在秀丽隐杆线虫脑-wide记录上，该框架识别出共享的低维动力学流形，实现了长时程生成和靶向计算机模拟干预。扰动学习动力学揭示行为相关的转换点，操控干预无需重新训练即可控制神经和行为状态。该工作建立了连接脑动力学与行为的可扩展虚拟实验框架。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-05-730482-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1599, \"height\": 1654, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-05-730482-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1598, \"height\": 1461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-05-730482-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1568, \"height\": 1573, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-05-730482-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1693, \"height\": 1163, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-05-730482-v2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1648, \"height\": 1465, \"label\": \"Figure\"}]"
motivation: 解决高维神经活动和行为从共享底层动力学涌现的挑战，以实现可复现和预测多尺度脑-行为动力学的数字孪生。
method: 提出NEBULA生成框架，通过统一潜动力学联合建模全脑神经活动和行为，并应用于秀丽隐杆线虫全脑记录。
result: 识别出共享低维动力学流形，实现长时程生成；扰动揭示行为相关转换点，操控干预无需重新训练即可控制神经和行为状态。
conclusion: 建立了连接脑动力学与行为的框架，为神经科学中的可扩展虚拟实验奠定基础。
---

## 摘要
理解高维神经活动和行为如何从共享的底层动力学中涌现仍然是神经科学的一个基本挑战。解决这个问题是实现能够忠实再现和预测活体系统多尺度脑-行为动力学的数字孪生的关键。在这里，我们提出了NEBULA（通过统一潜在动力学进行神经和行为建模），这是一个联合建模全脑神经活动和行为的生成框架。通过将NEBULA应用于秀丽隐杆线虫的全脑记录，我们识别出一个共享的低维动力学流形，它支撑着神经活动和行为，实现了长时程生成和靶向计算机干预。对学习动力学的扰动揭示了行为相关的转变点，而引导干预则可以在无需重新训练的情况下实现对神经和行为状态的可控操作。这些结果建立了一个将活体生物的大脑动力学与行为联系起来的框架，并为神经科学中可扩展的虚拟实验提供了基础。

## Abstract
Understanding how high-dimensional neural activity and behavior emerge from shared underlying dynamics remains a fundamental challenge in neuroscience. Addressing this problem is key to enabling digital twins that can faithfully reproduce and predict the multiscale brain-behavior dynamics of living systems. Here we present NEBULA (NEural and Behavioral modeling through Unified LAtent dynamics), a generative framework that jointly models whole-brain neural activity and behavior. By applying NEBULA to brain-wide recordings from C. elegans, we identify a shared low-dimensional dynamical manifold that underlies both neural activity and behavior, enabling long-horizon generation and targeted in silico interventions. Perturbations of the learned dynamics reveal behaviorally relevant transition points, whereas steering interventions enable controlled manipulation of neural and behavioral states without retraining. These results establish a framework for linking brain dynamics to behavior in a living organism and provide a foundation for scalable virtual experimentation in neuroscience.