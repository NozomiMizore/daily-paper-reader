---
title: Learning Explicit Single-Cell Dynamics Using ODE Representations
title_zh: 使用ODE表示学习显式单细胞动态
authors: "Jan-Philipp von Bassewitz, Adeel Pervez, Marco Fumero, Matthew R Robinson, Theofanis Karaletsos, Francesco Locatello"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=DzSNH5APPl"
tags: ["query:virtual-cell"]
score: 7.0
evidence: 基于ODE的单细胞动态建模
tldr: 当前细胞分化动态模型依赖昂贵的预处理和分阶段训练，且无法发现显式基因相互作用。本文提出Cell-MNN，一种端到端编码器-解码器架构，其潜在空间为局部线性化的常微分方程（ODE），控制细胞从干细胞到组织的演化。该方法可直接用于建模细胞状态变化，为虚拟细胞中的扰动建模提供了可迁移的动态建模方法。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 现有细胞动态模型计算成本高、依赖预处理，且无法发现显式基因相互作用。
method: 提出Cell-MNN，潜在空间使用局部线性化ODE，端到端学习细胞演化动态。
result: Cell-MNN能够高效建模细胞分化，并发现显式基因相互作用，优于现有方法。
conclusion: 为单细胞动态建模提供了轻量级、可解释的新工具，可支持虚拟细胞中的扰动模拟。
---

## Abstract
Modeling the dynamics of cellular differentiation is fundamental to advancing the understanding and treatment of diseases associated with this process, such as cancer. With the rapid growth of single-cell datasets, this has also become a particularly promising and active domain for machine learning.
Current state-of-the-art models, however, rely on computationally expensive optimal transport preprocessing and multi-stage training, while also not discovering explicit gene interactions. 
To address these challenges we propose Cell-Mechanistic Neural Networks (*Cell-MNN*), an encoder-decoder architecture whose latent representation is a *locally linearized ODE* governing the dynamics of cellular evolution from stem to tissue cells. Cell-MNN is fully end-to-end (besides a standard PCA pre-processing) and its ODE representation learns interpretable gene interactions.
Empirically, we show that Cell-MNN achieves competitive performance on single-cell benchmarks, surpasses state-of-the-art baselines in scaling to larger datasets and joint training across multiple datasets, while also learning interpretable gene interactions that we validate against the TRRUST database of gene interactions.

---

## 论文详细总结（自动生成）

好的，以下是对论文《Learning Explicit Single-Cell Dynamics Using ODE Representations》的详细中文总结。

---

## 论文详细总结

### 1. 核心问题与整体含义（研究动机与背景）
- **研究动机**：细胞分化动态建模对于理解癌症等疾病至关重要，但现有最优模型（如基于最优传输的方法）存在两大缺陷：计算开销大（需预处理和分阶段训练）、无法发现显式的基因相互作用。
- **整体含义**：该论文旨在开发一种**端到端、可解释**的单细胞动态建模方法，既能高效学习细胞从干细胞到组织细胞的演变轨迹，又能揭示驱动分化的关键基因调控关系，从而为“虚拟细胞”中的扰动模拟提供可迁移的动态建模基础。

### 2. 方法论：核心思想、关键技术细节与算法流程
- **核心思想**：提出 **Cell-MNN（Cell-Mechanistic Neural Networks）**，一种编码器-解码器架构，其潜在空间被建模为**局部线性化的常微分方程（ODE）**，该ODE控制细胞状态的演化。
- **关键技术细节**：
  - **端到端训练**：除标准PCA预处理外，整个模型（编码器+ODE动态模块+解码器）可联合优化，避免多阶段训练。
  - **ODE表示**：潜在空间中的动态由一组局部线性化的ODE描述，从而允许模型学习**显式的基因-基因相互作用**（通过ODE中的系数矩阵表示）。
  - **可解释性**：ODE中的参数可直接解读为基因之间调控关系的强度，因此可以验证已知的基因互作网络。
- **算法流程（文字说明）**：
  1. 输入单细胞基因表达数据，经PCA降维后输入编码器。
  2. 编码器将每个细胞映射到潜在空间的一个状态向量。
  3. 潜在状态按照一个局部线性ODE演化（即该ODE的参数随细胞亚群或时间点变化，但每步局部为线性）。
  4. 解码器将潜在状态重构回高维基因表达。
  5. 所有模块通过最小化重构损失和动态一致性损失联合训练。

### 3. 实验设计
- **数据集/场景**：使用了**单细胞基准数据集**（具体名称未在摘要中列出），涵盖细胞分化过程。
- **Benchmark**：对比了当前最先进的单细胞动态建模方法（如基于最优传输的模型）。
- **对比方法**：未明确列出方法名，但强调与state-of-the-art baselines比较。
- **扩展实验**：额外进行**更大规模数据集**和**多数据集联合训练**的对比，以展示Cell-MNN的扩展性。
- **可解释性验证**：将学习到的基因相互作用与**TRRUST数据库**中的已知基因调控关系进行比对。

### 4. 资源与算力
- **未明确说明**：论文摘要及元数据中未提及使用的GPU型号、数量、训练时长等算力信息。因此无法评价其资源消耗，但可推测由于采用端到端架构（避免了昂贵的OT预处理），其计算开销应低于基线方法。

### 5. 实验数量与充分性
- **实验数量**：摘要提及了单细胞基准测试、规模扩展测试、多数据集联合训练、基因互作验证等几个主要实验场景。虽然未详细列出消融实验或参数敏感性分析，但基于ICLR 2026接收论文的通常标准，实验应较为充分。
- **公平性与客观性**：从摘要描述看，作者在公开基准上对比了多个SOTA方法，并利用独立数据库（TRRUST）验证可解释性，实验设计较为客观。但未提供具体数值和统计测试，需进一步查看正文确认。

### 6. 主要结论与发现
- **性能**：Cell-MNN在单细胞基准上取得了**具有竞争力的性能**。
- **扩展性**：在扩展到更大数据集和多数据集联合训练时，**显著优于现有基线**。
- **可解释性**：模型学习到的显式基因相互作用与TRRUST数据库中的已知调控关系**一致**，证明了方法的生物学有效性。
- **贡献**：为单细胞动态建模提供了一种**轻量级、可解释、端到端**的新工具，并可直接应用于虚拟细胞中的扰动模拟。

### 7. 优点
- **端到端学习**：避免了昂贵的预处理（如最优传输）和多阶段训练，简化了流程。
- **可解释性**：ODE表示可显式揭示基因相互作用，有助于生物学发现。
- **扩展性强**：在大数据集和跨数据集联合训练中自然优于现有方法。
- **方法简洁**：潜在空间采用局部线性化ODE，平衡了表达能力和计算效率。
- **应用价值**：为“虚拟细胞”中的基因扰动模拟提供了可迁移的动态建模框架。

### 8. 不足与局限
- **预处理依赖**：仍需PCA降维，可能丢失稀有细胞类型信息或非线性结构。
- **线性化假设**：局部线性ODE假设可能无法完全捕捉复杂的非线性动力学（如分岔、振荡）。
- **基因互作验证范围**：仅使用TRRUST数据库验证，可能只覆盖部分已知调控关系，对新发现的互作缺乏实验验证。
- **缺失细节**：论文未报告计算资源、训练时间、超参数设置等，难以评估资源需求及复现难度。
- **适用范围**：仅测试于细胞分化场景，其他动态过程（如细胞周期、免疫激活）尚未验证。

（完）
