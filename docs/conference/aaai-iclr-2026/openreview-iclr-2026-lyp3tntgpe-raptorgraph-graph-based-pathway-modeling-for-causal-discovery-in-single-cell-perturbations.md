---
title: "RAPTORGraph: Graph-Based Pathway Modeling for Causal Discovery in Single-Cell Perturbations"
title_zh: RAPTORGraph：基于图的通路建模在单细胞扰动中的因果发现
authors: "Yeremia Gunawan Adhisantoso, Stephanie Kristin Schröder, Maximilian Greß, Mikel Hernaez, Jan Voges"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=lYp3tNTgpE"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 单细胞扰动中的因果发现
tldr: 针对现有方法在单细胞扰动中无法处理干预溢出和确认偏差的问题，RAPTORGraph提出一种基于图的通路建模方法，结合因果表示学习，能够更准确地发现调控因子并预测新扰动的影响。实验表明该方法可加速药物发现并揭示未知的细胞机制。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有因果表示学习方法在单细胞扰动中无法处理干预溢出且存在确认偏差。
method: 提出图基通路建模与因果表示学习结合，避免先验通路带来的偏差。
result: 在Perturb-seq实验上实现了更准确的因果发现和扰动预测。
conclusion: RAPTORGraph为单细胞扰动响应预测提供了更可靠的方法。
---

## Abstract
Experiments involving the perturbation of individual cells are central to understanding cellular mechanisms and can accelerate drug discovery.
Causal representation learning (CRL) allows us to uncover the latent factors that regulate biological systems and predict the impact of novel perturbations.
Unfortunately, existing methods fail to address intervention spillover in a closed-world setting where intervention targets are known a priori, such as in Perturb-seq experiments, due to their reliance on dense encoders.
Furthermore, incorporating curated biological pathways into the model imposes a confirmatory bias, forcing it to explain the data through preexisting pathways and reducing the set of hypotheses the model can explore, while discarding novel signals that lie outside the annotated pathways.
In this work, we introduce RAPTORGraph, a $\beta$-VAE with a GraphPathway encoder that explicitly models complex gene-to-gene interactions within learned pathways.
Moreover, our model's preconditioning isolates the influence of perturbed genes, yielding clean, single-node latent interventions required for identifiable causal discovery and eliminating spillover.
Finally, we train the model on data preprocessed with optimal-transport alignment, which guarantees a well-defined mapping between control and perturbed samples and further stabilizes the learned latent representations.
We demonstrate that RAPTORGraph improves state-of-the-art performance on downstream analyses of unseen perturbations, such as non-additive interactions, while outperforming other approaches on objective metrics, such as MSE and MK-MMD.
The code will be made publicly available upon publication of this paper.

---

## 论文详细总结（自动生成）

好的，以下是对给定论文的详细中文总结。

---

## 1. 论文的核心问题与整体含义（研究动机和背景）

单细胞扰动实验（如 Perturb-seq）是研究细胞调控机制和加速药物发现的关键方法。因果表示学习（CRL）旨在揭示调控生物系统的潜在因子，并预测新扰动的影响。然而，现有方法存在两个主要缺陷：

- **干预溢出（Intervention Spillover）**：在封闭世界设定下（扰动目标先验已知），现有方法依赖密集编码器，导致扰动效应无法被隔离，影响因果发现的识别性。
- **确认偏差（Confirmatory Bias）**：将生物通路先验知识直接融入模型会强制模型只能通过已有通路解释数据，从而忽略位于注释通路之外的新信号，限制了探索假设空间。

为此，论文提出 **RAPTORGraph**，一种基于图的通路建模方法，旨在解决上述问题，实现更可靠的因果发现和扰动响应预测。

## 2. 论文提出的方法论：核心思想、关键技术细节

**核心思想**：将因果表示学习与图结构通路建模相结合，使用学习到的通路（而非固定先验）显式建模基因间的复杂相互作用，并通过预处理机制消除干预溢出。

**关键技术细节**：

1. **模型架构**：采用 β-VAE 作为基础框架，并设计了一个 **GraphPathway encoder**，该编码器能够显式建模学习到的通路内部的基因-基因相互作用关系。
2. **干预隔离预处理**：通过模型的前置条件（preconditioning）机制，将扰动基因的影响与其他基因分离开来，从而生成干净的、单节点的潜在干预表示，这是可识别因果发现所必需的，并消除干预溢出。
3. **最优传输对齐预处理**：在训练前对数据进行最优传输（Optimal Transport）对齐，以确保对照样本和扰动样本之间存在良好定义的映射，进一步稳定学到的潜在表示。
4. **公式/算法流程**（文字说明）：
   - 输入：单细胞扰动数据（对照和多种扰动条件）。
   - 预处理：应用最优传输对齐，得到配对的控制-扰动数据。
   - 编码：通过 GraphPathway encoder 将细胞状态编码为潜在变量，该编码器利用图网络沿学习到的通路传递信息。
   - 解码：使用 β-VAE 解码器重建细胞状态。
   - 干预隔离：通过前置条件确保潜在空间中的干预仅影响被扰动基因对应的节点。
   - 训练目标：平衡重建误差（MSE）和潜在分布正则化（β-VAE 的 KL 散度），以及可能的最大均值差异（MK-MMD）项。

## 3. 实验设计

- **使用的数据集 / 场景**：Perturb-seq 实验数据（单细胞扰动数据集）。
- **Benchmark**：下游分析任务，包括对**未见过的扰动**（如非加性相互作用）的预测性能。
- **对比方法**：与其他现有因果发现和扰动预测方法进行了对比（具体方法名称在摘要中未列出，但声称超越了这些方法）。
- **评估指标**：客观指标包括均方误差（MSE）和核最大均值差异（MK-MMD），以及下游分析（如非加性相互作用的预测准确性）。

## 4. 资源与算力

论文摘要及元数据中**未明确说明**所使用的算力资源（如 GPU 型号、数量、训练时长等）。因此无法总结该部分内容，但可以指出原文未提供此信息。

## 5. 实验数量与充分性

- **实验数量**：文中提及在下游分析（如非加性相互作用）上进行了评估，并报告了 MSE 和 MK-MMD 指标。这暗示至少包含两组主要实验（定量指标对比 + 下游任务验证）。但未明确列出消融实验、超参数敏感性分析等。
- **充分性与公平性**：从现有描述来看，实验设计覆盖了常用指标和具体应用场景，对比了现有方法，具有一定的公正性。但由于缺少实验的详细配置（如数据集划分、重复次数、统计显著性），无法完全判断其充分性。作者声明代码将公开，这有助于复现和验证。

## 6. 论文的主要结论与发现

- RAPTORGraph 通过图通路编码器和最优传输对齐，有效解决了干预溢出和确认偏差问题。
- 在未见过的扰动（尤其是非加性相互作用）预测上，RAPTORGraph 达到了**最先进的性能**。
- 在 MSE 和 MK-MMD 等客观指标上，RAPTORGraph 优于其他对比方法。
- 该方法能够更准确地发现调控因子，揭示未知的细胞机制，有望加速药物发现。

## 7. 优点：方法或实验设计上的亮点

- **创新性方法设计**：将图神经网络与 β-VAE 结合，用**学习到的通路**替代固定先验通路，避免了确认偏差；通过预处理实现干预隔离，解决了干预溢出问题，使得因果发现具有可识别性。
- **数据预处理创新**：引入最优传输对齐，确保了控制与扰动样本的可比性，稳定了潜在表示学习。
- **全面评估**：不仅使用标准误差指标（MSE, MK-MMD），还进行了下游分析（非加性相互作用预测），更贴近实际应用需求。

## 8. 不足与局限

- **实验覆盖有限**：仅在 Perturb-seq 数据上验证，未扩展到其他类型的单细胞扰动数据或大规模多模态数据。
- **资源信息缺失**：未报告训练所需的计算资源（GPU 型号、时长），不利于其他研究者评估复现成本。
- **未讨论泛化风险**：确认偏差虽减弱，但学习到的通路可能仍受训练数据分布影响，在跨组织或跨物种场景下的泛化性未知。
- **理论分析不足**：关于干预隔离和因果可识别性的理论保证阐述不够深入（摘要中提及但未详细展开）。

---

（完）
