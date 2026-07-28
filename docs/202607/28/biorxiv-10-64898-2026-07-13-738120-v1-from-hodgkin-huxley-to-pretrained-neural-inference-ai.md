---
title: From Hodgkin-Huxley to Pretrained Neural Inference AI
title_zh: 从Hodgkin-Huxley模型到预训练神经推理AI
authors: "Zhang, Y., Han, D., Lv, Z., Ren, F., Wang, Y., Yang, Y., Li, D., Gu, Y."
date: 2026-07-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.13.738120v1.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 利用生物物理模拟预训练神经网络进行神经元活动推断，方法论上与虚拟细胞模型的扰动模拟类似
tldr: 高密度探针记录数千神经元，但单神经元身份识别仍是逆问题。本研究利用生物物理模拟生成海量合成数据，预训练神经网络，实现跨脑区、物种的零样本泛化，准确推断单神经元活动并发现被传统方法掩盖的弱活跃神经元。该方法解决了小鼠视皮层眼优势的长期矛盾，确立了生物物理模拟作为理论与实验间的桥梁，推动数据驱动推断。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738120-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1821, \"height\": 1554, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738120-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1770, \"height\": 1611, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738120-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1786, \"height\": 1724, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738120-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1757, \"height\": 1478, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738120-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1790, \"height\": 1222, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738120-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1811, \"height\": 2222, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738120-v1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1756, \"height\": 1386, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738120-v1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1776, \"height\": 671, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738120-v1/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1634, \"height\": 1139, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738120-v1/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1498, \"height\": 1173, \"label\": \"Figure\"}]"
motivation: 高密度探针记录海量神经元，但单神经元身份识别是病态逆问题，传统方法效果有限。
method: 基于霍奇金-赫胥黎等生物物理模拟生成大规模合成数据，预训练人工神经网络。
result: 零样本泛化跨脑区物种推断单神经元放电，发现被遮蔽的弱活跃神经元，解决眼优势矛盾。
conclusion: 生物物理模拟作为参考标准，通过数据驱动推断弥合理论与实验的鸿沟。
---

## 摘要
高密度探针可同时记录数千个神经元的活动，然而解析单个神经元的身份仍是一个病态逆问题。尽管精细的仿真能精确刻画生物物理正向过程，但其在解释脑信号方面的效用仍不明确。在此，我们展示群体神经元电信号的生物物理仿真作为理论与实验之间的有效桥梁。通过仅在大型合成数据上预训练人工神经网络，我们证明了其在多种脑区、实验范式和物种上的稳健零样本泛化能力，从而无需接触真实数据即可准确推断单个单元活动和细胞类型特性。此外，我们的框架发现了大量功能完备但活动较弱的神经元群体——这些神经元被传统启发式方法系统性地掩盖——从而解决了小鼠初级视觉皮层中关于眼优势的一个长期存在的矛盾。这些发现确立了生物物理仿真作为参考标准，通过数据驱动推断弥合了理论理解与实验观察之间的差距。

## Abstract
High-density probes record from thousands of neurons simultaneously, yet resolving single-neuron identity remains an ill-posed inverse problem. While detailed simulations precisely characterize the biophysical forward process, their utility for interpreting brain signal remains unclear. Here we show that biophysical simulations of population neuronal electrical signals serve as an effective bridge between theory and experiment. By pre-training artificial neural networks exclusively on large-scale synthetic data, we demonstrate robust zero-shot generalization across diverse brain regions, experimental paradigms and species, enabling the accurate inference of single-unit activities and cell-type properties without exposure to real data. Furthermore, uncovering a substantial population of functionally competent but weakly active neurons systematically obscured by conventional heuristics, our framework resolves a long-standing discrepancy regarding ocular dominance in mouse primary visual cortex. These findings establish biophysical simulations as a reference standard, bridging the gap between theoretical understanding and experimental observation through data-driven inference.