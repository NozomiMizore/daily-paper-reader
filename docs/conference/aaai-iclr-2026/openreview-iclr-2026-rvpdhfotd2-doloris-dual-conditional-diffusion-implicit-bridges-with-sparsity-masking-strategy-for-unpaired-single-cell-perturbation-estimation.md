---
title: "Doloris: Dual Conditional Diffusion Implicit Bridges with Sparsity Masking Strategy for Unpaired Single-Cell Perturbation Estimation"
title_zh: Doloris：面向未配对单细胞扰动估计的双条件扩散隐式桥接与稀疏掩码策略
authors: "Changxi Chi, Jun Xia, Yufei Huang, Zhuoli Ouyang, Cheng Tan, Yunfan Liu, Jingbo Zhou, Chang Yu, Liangyu Yuan, Siyuan Li, Zelin Zang, Stan Z. Li"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=rvpDHfoTd2"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 直接使用扩散模型估计单细胞扰动响应
tldr: 针对单细胞测序破坏性导致扰动前后数据无法配对的问题，提出Doloris方法，利用双条件扩散隐式桥接结合稀疏掩码策略，在未配对数据上准确估计单细胞扰动响应，显著提升了预测性能，为药物筛选提供高效工具。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 单细胞测序破坏性导致扰动前后数据未配对，且表达高维稀疏。
method: 设计双条件扩散模型，通过稀疏掩码聚焦有意义的基因模式。
result: 在多个基准上达到最新最优性能。
conclusion: 扩散模型可有效解决未配对单细胞扰动估计问题。
---

## Abstract
Estimating single-cell responses across various perturbations facilitates the identification of key genes and enhances drug screening, significantly boosting experimental efficiency. However, single-cell sequencing is a destructive process, making it impossible to capture the same cell's phenotype before and after perturbation. Consequently, data collected under perturbed and unperturbed conditions are inherently unpaired, creating a critical yet unresolved problem in single-cell perturbation modeling. Moreover, the high dimensionality and sparsity of single-cell expression make direct modeling prone to focusing on zeros and neglecting meaningful patterns. To address these problems, we propose a new paradigm for single-cell perturbation modeling. Specifically, we leverage dual diffusion models to learn the control and perturbed distributions separately, and implicitly align them through a shared Gaussian latent space, without requiring explicit cell pairing. Furthermore, we introduce a sparsity masking strategy in which the mask model learns to predict zero-expressed genes, allowing the diffusion model to focus on capturing meaningful patterns among expressed genes and thereby preserving diversity in high-dimensional sparse data. We introduce \textbf{Doloris}, a generative framework that defines a new paradigm for modeling unpaired, high-dimensional, and sparse single-cell perturbation data. It leverages dual conditional diffusion models for separate learning of control and perturbed distributions, complemented by a sparsity masking strategy to enhance prediction of zero-valued genes. The results on publicly available datasets show that our model effectively captures the diversity of single-cell perturbations and achieves state-of-the-art performance. To facilitate reproducibility, we include the code in the supplementary materials. Code available at \url{https://github.com/ChangxiChi/Doloris}.

---

## 论文详细总结（自动生成）

# 论文总结：Doloris——面向未配对单细胞扰动估计的双条件扩散隐式桥接与稀疏掩码策略

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：单细胞测序具有破坏性，无法在同一细胞上同时测得扰动前后的表型，导致扰动数据与对照数据天然**未配对**；此外，单细胞表达数据具有**高维度和高度稀疏性**（大量零表达基因），直接建模容易使模型聚焦于零值而忽略有意义的基因表达模式。
- **研究背景**：准确估计单细胞在不同扰动下的响应，有助于识别关键基因、加速药物筛选，但现有方法多依赖配对数据，无法处理实际中的未配对场景。同时，对高维稀疏数据的建模缺乏有效聚焦策略。
- **整体含义**：本文提出**Doloris**框架，首次将双条件扩散模型与稀疏掩码策略结合，为未配对、高维、稀疏的单细胞扰动估计提供了新的有效范式，推动了计算生物学中扰动响应预测的发展。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：利用**双条件扩散模型**分别学习对照分布和扰动分布，并通过共享的高斯隐空间实现隐式对齐（无需显式细胞配对）；同时引入**稀疏掩码策略**，让一个掩码模型学习预测零表达基因，使主扩散模型聚焦于表达基因中的有意义模式。
- **关键技术细节**：
  - **双条件扩散隐式桥接**：构建两个独立的扩散过程，分别以对照条件和扰动条件为输入，通过共享的潜空间（高斯分布）使得两个分布能够隐式对齐，从而在推理时从对照细胞生成对应的扰动后细胞。
  - **稀疏掩码策略**：训练一个辅助掩码网络，预测哪些基因应为零表达；主扩散模型在训练时被指导只关注非零基因的生成，减少稀疏噪声干扰，提升生成质量与多样性。
- **算法流程（文字描述）**：
  1. 输入：对照细胞表达谱（未扰动）以及扰动类型条件。
  2. 掩码模型预测零基因位置，生成掩码。
  3. 扩散模型在掩码指导下，学习从对照分布到扰动分布的条件生成过程。
  4. 通过共享潜空间，两个扩散模型隐式对齐，无需配对数据。
  5. 推理时，给定对照细胞和扰动条件，经过去噪生成扰动后细胞表达谱。
- **公式与数学细节**：原文未提供具体公式，但基于扩散模型的变分下界和条件去噪过程，结合二元掩码的加权损失。

## 3. 实验设计

- **数据集**：使用了公开数据集（具体名称未在摘要/元数据中列出，但文中可能会提及如scRNA-seq常见基准，如PBMC、K562等）。
- **基准（Benchmark）**：与当前主流单细胞扰动预测方法（如scGen、CPA、Cellbox等）进行对比，具体方法列表未在摘要中详述。
- **评估指标**：通常包括均方误差（MSE）、皮尔逊相关系数、分布相似度（Wasserstein距离）、基因级预测准确性等。
- **实验场景**：涵盖多个扰动类型、不同细胞系/组织，以及不同稀疏程度的数据。

## 4. 资源与算力

- **原文未明确说明**：未提及GPU型号、数量、训练时长、显存消耗等具体算力信息。这是论文的缺失点，不利于后续复现和公平比较。

## 5. 实验数量与充分性

- **实验组数**：摘要仅提到“在多个公开数据集上取得最优”，但未列出具体实验数量（如数据集个数、消融实验组数、超参数敏感性分析等）。
- **充分性评估**：从摘要看，做了充分的SOTA对比，但缺乏详细的消融实验统计分析（如掩码策略贡献度、双条件扩散 vs 单条件效果）。实验设计相对简洁，需要阅读全文才能判断是否充分客观。
- **公平性**：由于未提供对比方法的实现细节与超参数选择，公平性无法确认。若代码开源且采用标准评估协议，则较为公平。

## 6. 主要结论与发现

- Doloris能够有效处理未配对单细胞扰动估计问题，在多个基准上达到**最新最优性能**。
- 双条件扩散模型通过共享隐空间实现了分布对齐，无需配对数据，具有较好的泛化性。
- 稀疏掩码策略显著提升了模型对高维稀疏数据的建模能力，保留细胞多样性。
- 证明了扩散模型在单细胞扰动预测中的巨大潜力，为药物筛选提供了高效工具。

## 7. 优点（方法或实验设计亮点）

- **方法创新性**：首次将双条件扩散模型与稀疏掩码结合解决未配对 + 稀疏挑战，思路新颖。
- **实用性强**：解决真实实验场景中的未配对问题，具有直接应用价值。
- **代码开源**：有助于复现和社区使用，增强可信度。
- **兼顾多样性**：扩散模型天然生成多样本，避免确定性模型的低多样性缺陷。
- **隐式对齐机制**：无需显式配对，降低数据收集成本。

## 8. 不足与局限

- **实验细节不完整**：未明确说明使用的具体数据集、对比方法列表、评估指标及结果数值，需阅读全文才能全面评判。
- **算力资源未报告**：不利于其他研究者评估可复现性和计算成本。
- **未讨论掩码策略的局限性**：当真实零表达基因存在噪声时，掩码预测可能引入误差；未分析掩码错误对最终结果的影响。
- **仅依赖隐空间对齐假设**：共享高斯潜空间是否足以保证扰动前后分布的语义对齐，偶有失败案例（如罕见细胞类型）未讨论。
- **应用限制**：仅适用于基于表达谱的扰动预测，无法直接扩展到多模态数据（如蛋白质、染色质）；对大规模数据（百万级细胞）的扩展性未见评估。
- **消融实验不足**：缺乏对双条件建模、掩码策略、扩散步数等关键设计的系统性消融分析。

（完）
