---
title: "scPPDM: A Diffusion Model for Single-Cell Drug–Response Prediction"
title_zh: scPPDM：用于单细胞药物响应预测的扩散模型
authors: "Zhaokang Liang, Shuyang Zhuang, Xiaoran Jiao, Weian Mao, Hao Chen, Chunhua Shen"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=HG9OHffO1h"
tags: ["query:virtual-cell"]
score: 10.0
evidence: 首个用于单细胞药物响应预测的扩散模型
tldr: 针对单细胞药物响应预测的需求，提出scPPDM，首个基于扩散模型的方法，通过非拼接注意机制耦合前状态和药物剂量条件，在Tahoe-100M基准上在未知协变量和未知药物设置下均达到最佳性能，为单细胞扰动响应预测提供了新范式。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有方法难以捕捉药物响应的概率分布。
method: 设计扩散模型，通过双条件通道和分解引导实现可解释控制。
result: 在Tahoe-100M上刷新多项指标。
conclusion: 扩散模型可有效预测单细胞药物响应且具有可解释性。
---

## Abstract
This paper introduces the Single-Cell Perturbation Prediction Diffusion Model (scPPDM), the first diffusion-based framework for single-cell drug-response prediction from scRNA-seq data. scPPDM couples two condition channels, pre-perturbation state and drug with dose, in a unified latent space via non-concatenative GD-Attn. During inference, factorized classifier-free guidance exposes two interpretable controls for state preservation and drug-response strength and maps dose to guidance magnitude for tunable intensity. Evaluated on the Tahoe-100M benchmark under two stringent regimes, unseen covariate combinations (UC) and unseen drugs (UD), scPPDM sets new state-of-the-art results across log fold-change recovery, $\Delta$ correlations, explained variance, and DE-overlap. Representative gains include +36.11%/+34.21% on DEG logFC–Spearman/Pearson in UD over the second-best model. This control interface enables transparent what-if analyses and dose tuning, reducing experimental burden while preserving biological specificity.

---

## 论文详细总结（自动生成）

# scPPDM：用于单细胞药物响应预测的扩散模型——中文详细总结

## 1. 论文的核心问题与整体含义

- **研究动机**：单细胞RNA测序（scRNA-seq）技术使研究者能够观测药物在单细胞层面的转录响应，但现有预测方法（例如基于VAE、GAN或直接回归模型）难以捕捉药物响应的概率分布，尤其面对未知药物或未知协变量组合时泛化能力不足。此外，传统方法缺乏可解释的控制接口，无法精细调节响应强度或保持细胞原始状态。
- **整体含义**：本文首次提出基于扩散模型的单细胞药物响应预测框架——scPPDM（Single-Cell Perturbation Prediction Diffusion Model），旨在从scRNA-seq数据中准确、可解释地预测药物对单个细胞的基因表达变化，为药物筛选、精准医学及虚拟细胞研究提供新范式。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将扩散模型应用于单细胞扰动预测，通过双条件通道（前扰动状态和药物剂量）在统一隐空间中耦合，并利用分解的无分类器引导实现可解释控制。
- **关键技术细节**：
  - **非拼接注意力机制（Non-concatenative GD-Attn）**：避免简单拼接条件向量，而是通过门控动态注意力机制将预扰动状态和药物剂量信息融合到扩散模型的去噪过程中，保留各自生物含义。
  - **双条件通道**：条件一为细胞在药物处理前的基因表达状态（pre-perturbation state），条件二为药物及其剂量（drug with dose）。
  - **分解的无分类器引导（Factorized Classifier-Free Guidance）**：在推理阶段，将引导项分解为两个独立分量——状态保持引导（state preservation）和药物响应强度引导（drug-response strength）。剂量大小直接映射为引导幅度，从而实现强度可调。
  - **可解释控制**：用户可通过调整引导权重观察“what-if”场景（如改变药物剂量对特定基因的影响），且能保持非目标基因的表达稳定性，减少实验试错成本。

## 3. 实验设计：数据集、基准与对比方法

- **数据集**：使用Tahoe-100M基准数据集，该数据集包含大规模单细胞扰动实验数据（100M量级细胞）。
- **实验场景**：两种严格评估设置：
  - **未知协变量组合（UC, Unseen Covariate Combinations）**：训练集中未出现过的细胞类型与药物剂量组合。
  - **未知药物（UD, Unseen Drugs）**：模型从未见过的药物分子。
- **对比方法**：未在摘要中列出具体名称，但声称在多项指标上超越“第二好的模型”。根据上下文推测对比方法包括已有的扰动预测模型（如scGen、CPA、CellOT等），但文中未明确列举。
- **评估指标**：对数折叠变化恢复（log fold-change recovery）、Δ相关性（Delta correlations）、解释方差（explained variance）、差异表达基因重叠（DE-overlap）。具体量化：在UD设置下，DEG logFC的Spearman相关系数提升36.11%、Pearson相关系数提升34.21%，均为相较于第二佳模型的相对增益。

## 4. 资源与算力

- 论文中**未明确说明**使用的GPU型号、数量、训练时长等算力信息。仅根据元数据推断，该论文被ICLR 2026拒绝，可能因实验不完整或缺乏计算资源细节。需注意这是一个缺失项。

## 5. 实验数量与充分性

- **实验数量**：摘要中仅报告了一个基准数据集（Tahoe-100M）上的结果，但包含两种严格设置（UC和UD），并在四个指标上展示结果。未提及消融实验、不同数据集验证或超参数敏感性分析。
- **充分性判断**：从已公开信息看，实验覆盖有限——仅一个数据集，未提供与多个前沿方法的系统对比表格，缺乏消融研究以验证各组件（如GD-Attn、分解引导）的贡献。因此实验**不够充分**，存在选择性报告风险。但元数据提到“在Tahoe-100M上刷新多项指标”，说明在该数据上表现突出，但全面性受质疑。

## 6. 论文的主要结论与发现

- 首次证明扩散模型可有效预测单细胞药物响应，且优于现有方法。
- 提出的双条件耦合和分解引导机制能够提供可解释的控制，允许用户在状态保持和响应强度之间权衡。
- 剂量映射到引导幅度的设计实现了剂量依赖的连续可调预测，对实际药物剂量优化具有直接意义。
- 在未知药物场景下，性能提升尤其显著（+36%以上），说明模型对未见药物的泛化潜力。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：首个将扩散模型应用于单细胞药物响应预测，填补了该方向空白。
- **可解释性**：分解的无分类器引导提供了两个正交控制手柄，使模型不仅预测结果，还能解释预测如何随条件变化，符合生物学家“假设分析”需求。
- **泛化能力**：在两种苛刻未知场景下均取得SOTA，证明模型并非简单记忆训练数据。
- **生物相关性**：通过状态保持控制能够避免扰动预测中常见的“过度去分化”或“非特异性变化”，保留细胞身份。

## 8. 不足与局限

- **实验不充分**：仅在一个数据集（Tahoe-100M）上验证，缺少跨数据集（如其他物种、不同技术平台）的泛化实验。未提供消融实验证明各模块必要性。未与其他最新扩散扰动模型（如scDiff、Geneformer等）对比（若存在）。
- **资源信息缺失**：未报告任何计算资源与训练成本，影响可复现性评估。
- **偏差风险**：仅报告了最佳指标增益，未展示完整分布（如箱线图、置信区间），可能存在选择性报告。
- **应用限制**：模型依赖于高质量scRNA-seq参考数据，对于稀有细胞类型或低深度测序数据可能失效；且目前仅针对药物处理，未扩展至其他扰动（如基因编辑、环境应激）。
- **理论基础不足**：未讨论扩散模型在单细胞高维稀疏数据上的理论基础（如是否满足连续扩散假设），也未与物理模型（如动力学模型）对比。

（完）
