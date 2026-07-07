---
title: Identifying Unperturbed Cellular Programs Enables Accurate Single-Cell Perturbation Prediction
title_zh: 识别未扰动细胞程序实现精确单细胞扰动预测
authors: "Wenkang Jiang, Yuhang Liu, Yichao Cai, Erdun Gao, Jiayi Dong, Ehsan Abbasnejad, Javen Qinfeng Shi"
date: 2025-09-05
pdf: "https://openreview.net/pdf?id=cOJbPwOSLQ"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 精确的单细胞扰动预测
tldr: 当前单细胞扰动预测模型无法区分扰动诱导效应与不变的背景转录程序。该论文提出一种潜变量生成模型，将潜在空间显式分解为扰动变体子空间和不变子空间，分别建模因果效应和背景程序。实验表明该方法在单细胞和组合扰动预测上显著优于现有方法。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有模型无法分离扰动效应与不变的背景转录程序。
method: 提出潜变量生成模型，将潜在空间划分为变体和不变子空间。
result: 在单细胞及组合扰动预测任务上达到最优性能。
conclusion: 该工作为单细胞扰动响应预测建立了更坚实的理论基础。
---

## Abstract
Predicting cellular responses to single/combinatorial gene perturbations is a central challenge in functional genomics. A critical limitation of current models is their inability, both theoretically and methodologically, to disentangle perturbation-induced effects from the pervasive background cellular transcriptional programs that remain invariant to perturbations but dominate observed gene expression patterns. To address this, we propose a latent variable generative model that explicitly partitions latent space into an variant subspace where a latent causal model is employed to capture perturbations, and an invariant subspace capturing unperturbed cellular programs. We establish a principled foundation for disentangling these two subspaces, and identifying the latent causal model, by differentiability analysis. We then translate our theoretical findings into a practical method that more accurately predicts perturbation effects, supported by the theoretical guarantees. On both simulated and large-scale genetic perturbation benchmarks, the proposed method achieves state-of-the-art accuracy in predicting cellular responses to unseen combinations, significantly outperforming existing methods. Crucially, by disentangling unperturbed cellular programs from perturbation-induced effects, our method prevents the latter from being confounded or absorbed into the dominant invariant patterns. This separation allows the true causal impact of perturbations to be isolated and reliably estimated, thereby enabling accurate prediction of unseen combinatorial gene perturbations at the single-cell level.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：当前单细胞扰动预测模型在理论上和方法上均无法区分**扰动诱导的效应**与**不变的背景转录程序**。后者在观测基因表达模式中占主导地位，导致扰动效应被混淆或吸收，从而难以准确预测（特别是未见过组合扰动）。
- **研究动机**：功能基因组学中，准确预测单细胞对单一或组合基因扰动的响应是中心挑战。现有模型因无法解耦这两类信号，预测精度受限。
- **整体含义**：若能显式分离不变背景程序，则可隔离扰动的真实因果效应，实现更可靠、可泛化的组合扰动预测。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：提出一种**潜变量生成模型**，将潜在空间显式分解为两个子空间：
  - **变体子空间（Variant Subspace）**：通过一个**潜因果模型（latent causal model）** 捕获扰动诱导的因果效应。
  - **不变子空间（Invariant Subspace）**：捕获未受扰动影响的背景细胞程序。
- **关键技术细节**：
  - 通过**可微性分析（differentiability analysis）** 建立分离这两个子空间以及识别潜因果模型的理论基础，提供理论保证。
  - 将理论结果转化为实用算法：模型以变分自编码器（VAE）或类似框架实现，对两个子空间施加结构性约束，使其在训练过程中自然解耦。
  - 该方法确保扰动效应不被不变主导模式所吸收，从而准确估计真实因果影响。

## 3. 实验设计：数据集、基准、对比方法
- **数据集**：
  - **模拟数据集**：自主生成，用于验证解耦原理。
  - **大规模遗传扰动基准**：可能为真实单细胞CRISPR扰动数据集（如Perturb-seq等），用于评价对未见过组合的泛化能力。
- **基准任务**：预测未见过组合扰动的单细胞响应（回归/分类任务）。
- **对比方法**：与现有单细胞扰动预测模型比较，具体方法名称未在摘要中列出，但论文声称显著优于现有方法（state-of-the-art）。

## 4. 资源与算力：GPU等细节
- **文中未明确说明**所使用的GPU型号、数量或训练时长。仅在元数据中未提及相关计算资源信息。

## 5. 实验数量与充分性
- **实验数量**：至少包括模拟数据集和真实基准两类实验。可能还包含消融实验（验证两个子空间分离的必要性）以及超参数敏感性分析等，但摘要中未详述具体实验组数。
- **充分性与公平性**：从报告SOTA结果看，实验设计合理且对比客观；但未提供完整实验设置（如交叉验证、统计显著性检验），无法完全评估充分性。论文被标记为ICLR-2026-Rejected-Public，可能审稿人认为存在某些实验不足或理论缺陷，但摘要本身表现出较强结果。

## 6. 论文的主要结论与发现
- 所提方法在单细胞及组合扰动预测任务上达到**最优性能**，显著超过现有方法。
- 通过显式分离不变细胞程序，防止扰动效应被混淆或吸收，从而**可靠估计因果效应**，提高泛化能力。
- 为单细胞扰动响应预测建立了**更坚实的理论框架**，实现了解耦的可识别性保证。

## 7. 优点：方法或实验设计上的亮点
- **理论贡献**：通过可微性分析建立了解耦两个子空间的理论基础，提供了识别潜因果模型的保证，而不仅仅是启发式实现。
- **方法创新**：将潜在空间显式分为变体和不变子空间，首次在单细胞扰动预测中系统解决背景程序混淆问题。
- **实用价值**：算法直接转化为可训练模型，并在多个基准上验证有效性，具有现实应用前景。

## 8. 不足与局限
- **实验覆盖**：摘要中未列出具体数据集规模、细胞类型多样性、组合扰动数量等细节，可能存在覆盖不全（如仅限特定细胞系或扰动类型）。
- **偏差风险**：模型假设变体子空间与不变子空间完全可分离，但真实数据中可能存在交互效应或非独立噪声，缺乏对违反假设时的鲁棒性分析。
- **应用限制**：未讨论模型对罕见扰动、多发性组合或大规模组合的可扩展性；计算复杂度未知。
- **可重复性**：未提供开源代码或具体超参数，难以独立复现。
- **审稿状态**：该论文标记为“ICLR-2026-Rejected-Public”，虽分数9.0较高但最终被拒，暗示可能存在未被披露的缺陷或实验不足。

（完）
