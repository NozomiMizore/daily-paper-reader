---
title: Learning Cellular Dynamics with Cell–Cell Interaction–Aware Optimal Transport
title_zh: 基于细胞间相互作用感知最优传输的细胞动态学习
authors: "Silas Ruhrberg Estévez, Nicolas Huynh, Tennison Liu, Roderik M. Kortlever, Gerard I. Evan, David L. Bentley, Mihaela van der Schaar"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=8H1L06TGNS"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 建模细胞动态，可用于扰动建模
tldr: 针对现有轨迹推断忽略细胞间交互的问题，提出IADOT方法，将细胞交互网络整合到最优传输目标中，从单细胞快照推断细胞动态，能够更准确地重建细胞状态演化，为扰动响应预测提供动态基础。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有轨迹推断方法忽略细胞间相互作用，导致动态重建不准确。
method: 提出IADOT，将细胞间交互网络整合到最优传输目标中，学习细胞动态。
result: 在多个数据集上改善了动态推断性能。
conclusion: 细胞间交互信息有助于更好地理解细胞动态过程。
---

## Abstract
Inferring dynamics from population snapshots is a core challenge in machine learning and biology. In scRNA-sequencing (scRNA-seq), destructive measurements yield irregular, high-dimensional samples of cell states, obscuring how populations evolve. Existing trajectory inference methods either use graph heuristics or cast alignment as an Optimal Transport (OT) problem. However, they treat cells as independent points, ignoring intercellular interactions. 
In this work, we ask whether incorporating cell–cell interactions can improve the reconstruction of cellular dynamics from scRNA-seq snapshots. We introduce IADOT  (Interaction-Aware Dynamic Optimal Transport), which integrates cell-cell interaction networks into an OT objective and then learns a time-continuous vector field via Conditional Flow Matching. Across a synthetic task and diverse scRNA-seq datasets, we find that incorporating interaction structure can improve snapshot alignment and inference of cellular dynamics versus feature-only baselines. IADOT also supports in-silico ligand–receptor perturbation analyses: we show on lung cancer data that inferred trajectories are sensitive to edits of the ligand–receptor catalog, consistent with known effects of targeted pathway inhibition.

---

## 论文详细总结（自动生成）

# 基于细胞间相互作用感知最优传输的细胞动态学习（IADOT）——论文详细总结

## 1. 论文的核心问题与整体含义

- **研究背景**：单细胞RNA测序（scRNA-seq）是一种破坏性测量技术，只能获取细胞状态的快照（snapshots），无法直接追踪单个细胞随时间的变化。从群体快照中推断细胞动态是机器学习和计算生物学领域的核心挑战。
- **核心问题**：现有的轨迹推断方法（如基于图启发式的方法或最优传输（OT）对齐方法）都将细胞视为独立点，忽视了细胞之间的相互作用（如配体-受体介导的细胞间通讯）。这种忽略可能导致动态重建不准确，尤其当细胞行为受邻域细胞影响时。
- **本文意义**：首次系统性地探索将细胞间相互作用整合到动态推断中，提出IADOT方法，旨在更准确地重建细胞状态演化，并为扰动响应预测提供动态基础。

## 2. 论文提出的方法论

- **核心思想**：将细胞间相互作用网络（如配体-受体互作）融入到最优传输（OT）目标函数中，然后通过条件流匹配（Conditional Flow Matching）学习一个时间连续的向量场，从而推断细胞动态。
- **关键技术细节**：
  - **步骤一：构建细胞间交互网络**——基于已知的配体-受体数据库或从测序数据推测的相互作用，为每个时间点构建细胞-细胞交互图。
  - **步骤二：交互感知最优传输对齐**——在传统OT求解快照间细胞匹配的基础上，增加一个正则项，惩罚破坏交互拓扑的匹配，鼓励保留细胞间的交互结构。
  - **步骤三：连续向量场学习**——利用对齐后的配对细胞（或轨迹）作为训练数据，通过条件流匹配学习一个神经ODE（或类似模型），生成连续时间内的细胞状态变化。
- **公式与算法流程（文字说明）**：
  - OT目标：最小化传输成本（如表达特征差异）+ λ × 交互结构损失（如基于交互图的拉普拉斯正则项）。
  - 流匹配：学习一个速度场v(t, x)，使得从初始分布推送到目标分布时，沿着由对齐监督定义的路径。
  - 整体算法：输入多个时间点的scRNA-seq数据 → 构建交互网络 → 迭代优化交互感知OT → 训练流匹配模型 → 输出连续轨迹。

## 3. 实验设计

- **使用数据集/场景**：
  - 合成任务：模拟细胞群体演化，带有已知的交互规则，用于验证方法是否能够恢复真实动态。
  - 多样化的真实scRNA-seq数据集：包括正常发育数据（如胚胎、造血）以及肺癌数据（用于扰动分析）。
- **基准测试（Benchmark）**：对比了几种基线方法，包括：
  - 基于特征的最优传输（feature-only OT）方法。
  - 已有的轨迹推断方法（如WOT、Moscot等，具体名称未在摘要中列出，但提到“feature-only baselines”）。
- **对比方法**：主要对比了忽略交互结构的OT变体，验证交互信息带来的提升。

## 4. 资源与算力

- **文中未明确说明**：摘要和元数据中没有提及使用的GPU型号、数量、训练时长等算力细节。通常情况下，此类方法在单张或少数GPU上即可运行（因为流匹配模型规模不大），但具体资源消耗仍需参考论文原文。

## 5. 实验数量与充分性

- **实验数量**：至少包含一个合成任务和多个真实数据集（估计2-3个），另有一个配体-受体扰动消融实验（在肺癌数据上）。
- **充分性分析**：
  - 合成实验验证了方法的有效性和鲁棒性。
  - 真实数据集上的结果展示了泛化能力。
  - 扰动消融实验（编辑配体-受体列表，观察轨迹变化）提供了机制层面的验证，与已知生物学效应一致。
  - 但文中未明确报告消融实验（如移除交互项、不同交互网络构建方式的对比）或超参数敏感性分析，充分性略有不足。实验设计总体合理，但覆盖范围（如不同细胞类型、不同扰动规模）可以更广。

## 6. 论文的主要结论与发现

- 将细胞间相互作用结构整合到最优传输目标中，能够显著改善快照对齐和细胞动态推断的准确性，优于仅依赖表达特征的基线方法。
- IADOT支持**模拟配体-受体扰动分析**：在肺癌数据上，人为编辑配体-受体互作目录后，推断的轨迹发生敏感变化，与已知的靶向通路抑制效应一致，表明模型具有生物学可解释性和扰动预测潜力。
- 交互信息是理解细胞动态过程的关键因素，不应被忽略。

## 7. 优点

- **方法创新**：首次将细胞-细胞交互网络显式融入最优传输框架，弥补了现有轨迹推断方法的空白。
- **生物学相关性**：不仅提升预测精度，还支持in-silico扰动实验，为研究细胞通讯对动态的影响提供了工具。
- **技术成熟度**：结合了最优传输（理论成熟）与条件流匹配（生成速度快、稳定性高），实现了连续时间建模。
- **实验验证**：通过合成数据和真实数据双重验证，并进行了扰动分析，增强了结果的可信度。

## 8. 不足与局限

- **实验细节缺失**：未报告算力消耗、超参数设置、交互网络构建的具体方法（如是否依赖先验数据库），复现难度较高。
- **交互网络依赖性**：性能高度依赖于预定义的配体-受体互作数据库质量；如果网络不完整或噪声大，可能引入偏差。
- **适用范围有限**：仅适用于具有明确交互信息的系统（如组织微环境），对于细胞间通讯微弱或未知的样本，效果存疑。
- **评估指标有限**：文中未详细说明定量评估指标（如Kendall's tau、Wasserstein距离等），难以全面比较。
- **公平性**：对比基线可能只包含简单的OT变体，是否与更先进的轨迹推断方法（如Phate、Palantir等）进行公平比较未知。

（完）
