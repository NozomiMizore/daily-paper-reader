---
title: Deep dynamical models of single-cell multiomic velocities predict loss-of-function and rescue perturbations in B cells
title_zh: 单细胞多组学速度的深度动力学模型预测B细胞中的功能缺失和拯救扰动
authors: "Karbalayghareh, A., Pelzer, B., Chin, C. R., Melnick, A., Barisic, D., Leslie, C. S."
date: 2026-07-08
pdf: "https://www.biorxiv.org/content/10.1101/2025.04.24.650458v2.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 深度动力学模型利用单细胞多组学预测扰动结果
tldr: 单细胞多组学数据为研究细胞动态提供新视角，但现有模型难以联合分析基因表达与染色质可及性。本文提出DynaVelo，一种神经ODE生成模型，利用RNA速度与转录因子motif可及性学习细胞状态轨迹。模型成功恢复小鼠生发中心B细胞动态，揭示突变影响，并通过原位扰动预测功能丧失的挽救因子。体内实验验证了预测，为动态系统建模与扰动提供强大框架。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1663, \"height\": 1302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1701, \"height\": 1334, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1713, \"height\": 928, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 424, \"height\": 285, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 424, \"height\": 261, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 424, \"height\": 265, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 424, \"height\": 272, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 427, \"height\": 284, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 415, \"height\": 283, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 426, \"height\": 265, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 410, \"height\": 260, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 416, \"height\": 262, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 424, \"height\": 257, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 423, \"height\": 292, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 424, \"height\": 284, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1695, \"height\": 1614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1692, \"height\": 610, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1704, \"height\": 2295, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1698, \"height\": 2255, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1450, \"height\": 860, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1684, \"height\": 982, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1626, \"height\": 2299, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1682, \"height\": 813, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1710, \"height\": 1931, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-04-24-650458-v2/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 838, \"height\": 834, \"label\": \"Figure\"}]"
motivation: 现有方法无法联合建模基因表达与染色质可及性动态，且难以预测遗传扰动对细胞状态的影响。
method: 提出DynaVelo，基于神经ODE的生成模型，整合RNA速度与TF motif可及性，学习单细胞多组学的联合动力学。
result: 恢复野生型GC B细胞动态，预测Arid1a功能丧失的挽救因子（Ctcf、Bcl6、Stat3），经双杂合小鼠验证。
conclusion: DynaVelo提供通用框架，可建模动态系统并预测扰动，推动多组学理解与实验验证。
---

## 摘要
我们提出了DynaVelo，一种生成式神经常微分方程模型，它利用联合基因表达和染色质可及性读出的单细胞多组学，学习演化细胞系统中基因表达和转录因子（TF）基序活性的联合动力学。DynaVelo利用部分RNA速度信息以及单细胞TF基序可及性数据，改进了细胞状态动力学的建模和TF驱动因子的识别。我们展示了DynaVelo能够恢复野生型小鼠生发中心（GC）B细胞的复杂分叉体内动力学，并揭示这些细胞动力学在表观遗传调控因子Arid1a和Ctcf功能缺失突变下如何变化。DynaVelo通过分析训练细胞或从模型生成的轨迹，解析了TF基序活性沿着潜在时间轨迹的演化过程。进一步的计算机模拟扰动分析使DynaVelo能够推断动态的、细胞状态特异性的基因调控网络（GRN），恢复了野生型GC GRN中许多已知的TF到基因的边，并预测了突变体中受扰动的边。最后，计算机模拟的基因和TF扰动既允许预测功能缺失基因突变下的细胞动力学，也允许识别可以拯救功能缺失动力学和免疫表型的TF扰动。该分析预测Ctcf敲除将拯救GC反应中的Arid1a功能缺失表型，并提名Bcl6和Stat3作为额外的TF，其敲除可拯救Arid1a缺失。我们使用双杂合突变小鼠在体内验证了这些预测，在所有情况下确认了Arid1a暗区表型的拯救，并使用Arid1aHet;CtcfHet双杂合小鼠的多组学定量评估了模型预测。因此，DynaVelo通过利用单细胞多组学数据集，为建模和扰动动态细胞系统提供了一个强大的新深度学习框架。

## Abstract
We present DynaVelo, a generative neural ordinary differential equation model that learns the joint dynamics of gene expression and transcription factor (TF) motif activities in evolving cell systems using single-cell multiome with joint gene expression and chromatin accesibility readout. DynaVelo leverages partial RNA velocity information together with single-cell TF motif accessibility data to improve the modeling of cell state dynamics and identification of TF drivers. We show that DynaVelo recovers the complex and bifurcating in vivo dynamics of wildtype murine germinal center (GC) B cells and reveals how these cell dynamics change under loss-of-function mutations in epigenetic regulators Arid1a and Ctcf. DynaVelo resolves how TF motif activities evolve along latent time trajectories using analysis of training cells or through generated trajectories from the model. In silico perturbation analysis further enables DynaVelo to infer dynamic and cell-state-specific gene regulatory networks (GRNs), recovering many known TF-to-gene edges in the wildtype GC GRN and predicting those that are disrupted in mutants. Finally, in silico gene and TF perturbations allow both the prediction of cell dynamics under loss-of-function genetic mutations and the identification of TF perturbations to rescue loss-of-function dynamic and immunological phenotypes. This analysis predicted that Ctcf knockout would rescue Arid1a loss-of-function phenotype in the GC reaction and nominated Bcl6 and Stat3 as additional TFs whose knockout would rescue Arid1a loss. We validated these predictions in vivo using double heterozygous mutant mice, confirming rescue of the Arid1a dark zone phenotype in all cases and quantitatively assessing model predictions using multiome in Arid1aHet;CtcfHet double heterozygous mice. DynaVelo therefore provides a powerful new deep learning framework for modeling and perturbing dynamic cell systems by harnessing single-cell multiome data sets.

---

## 论文详细总结（自动生成）

# 单细胞多组学速度的深度动力学模型：DynaVelo 的总结

## 1. 论文的核心问题与整体含义

- **研究动机**：单细胞多组学技术（同时测量基因表达和染色质可及性）为研究细胞动态过程提供了前所未有的视角，但现有方法无法联合建模这两种模态的动力学。尤其是，已有模型难以从多组学数据中预测遗传扰动（如基因敲除）对细胞状态和分叉轨迹的影响。
- **核心问题**：如何利用单细胞 RNA 速度部分信息与转录因子（TF）基序可及性数据，学习细胞状态的联合动力学，并进一步推断动态基因调控网络（GRN）以及预测功能缺失或拯救性扰动？
- **整体含义**：若能准确建模细胞动态并模拟扰动，将极大推动系统生物学和精准医学中“虚拟细胞”的构建，实现从数据到机制的闭环验证。

## 2. 方法论

- **核心思想**：提出 **DynaVelo**，一种基于**神经常微分方程（neural ODE）**的生成模型，整合基因表达与染色质可及性，以学习细胞状态随时间演化的联合动力学。
- **关键技术细节**：
  - **多组学融合**：同时利用 scRNA-seq 测得的基因表达（部分 RNA 速度信息）和 scATAC-seq 衍生的 TF motif 可及性数据。
  - **动力学建模**：将细胞状态（基因表达向量、TF motif 活性向量）作为 ODE 的隐藏状态，使用神经网络参数化其时间导数，并利用 ODE 求解器生成连续时间轨迹。
  - **部分速度监督**：通过 RNA 剪接信息（unspliced / spliced ratio）估计的 RNA 速度作为 ODE 速度的弱监督信号，约束模型学习正确的方向性。
  - **TF 活性推断**：利用染色质可及性数据计算每个细胞中特定 TF motif 的开放程度，作为 TF 活性的代理指标。
  - **扰动模拟**：在训练好的 ODE 模型上进行 in silico 扰动：通过修改特定基因或 TF 的动力学参数（例如将某基因表达强制为零模拟敲除），再通过 ODE 积分预测细胞状态轨迹的变化。
  - **动态 GRN 推理**：通过分析 ODE 模型中不同基因/TF 之间的偏导数或灵敏度，导出细胞状态特异性的调控边。
- **算法流程**：
  1. 输入：多组学矩阵（基因表达、剪接比例、TF motif 可及性）。
  2. 用 autoencoder 或直接编码得到细胞潜在状态。
  3. 训练 neural ODE 以拟合观测到的基因表达变化率（RNA 速度）和 TF 活性变化率。
  4. 从任意初始细胞状态，通过 ODE 积分生成连续轨迹。
  5. 用训练好的模型进行 in silico 扰动实验，预测突变体动力学或寻找拯救性因子。

## 3. 实验设计

- **使用的数据集/场景**：
  - **小鼠生发中心（GC）B 细胞** 的野生型（WT）多组学数据（10x Multiome）。
  - 两种功能缺失突变体：**Arid1a 敲除** 和 **Ctcf 敲除** 的 GC B 细胞多组学数据。
  - 体内验证场景：**双杂合突变小鼠**（Arid1aHet;CtcfHet 等）的 GC 表型分析。
- **Benchmark**：论文未明确列出标准基准数据集对比，而是以**已知生物学知识**（如 GC 中已知的 TF–靶基因边、WT 的分叉轨迹）作为金标准评估模型恢复能力。
- **对比方法**：摘要未提及直接与其他模型进行数值对比，可能主要与经典 RNA 速度方法（如 scVelo）或现有 GRN 推断方法进行定性比较。补充材料中可能有更详细对比但未提供完整 PDF。

## 4. 资源与算力

- **未明确说明**：论文摘要及元数据中未提及 GPU 型号、数量、训练时长等具体算力信息。可推测使用了深度学习常用的 GPU（如 NVIDIA V100/A100），但细节未知。

## 5. 实验数量与充分性

- **实验组数**：
  - 1. 恢复 WT GC B 细胞的复杂分叉动力学。
  - 2. 揭示 Arid1a 和 Ctcf 突变体下的动力学变化。
  - 3. 解析 TF 基序活性沿潜时轨迹的演化。
  - 4. 推断 WT 和突变体的动态 GRN，验证已知边。
  - 5. 计算机模拟扰动预测（敲除拯救因子）。
  - 6. 体内验证：使用双杂合小鼠（3 种组合：Arid1aHet;CtcfHet、Bcl6 杂合、Stat3 杂合）验证拯救表型，并用多组学对 Arid1aHet;CtcfHet 进行定量评估。
- **充分性与客观性**：
  - 实验覆盖了从数据拟合到机制推断再到体内验证的完整流程，证据链比较完整。
  - 体内实验直接支持了模型预测，具有强说服力。
  - 但仅在**一个细胞系统（GC B）**上测试，泛化性待验证；未进行大规模基准测试；消融实验（如去掉速度监督、去 motif 信息）未知。

## 6. 主要结论与发现

- DynaVelo 能**准确恢复野生型 GC B 细胞在体内的双叉动力学**（暗区/明区）。
- 模型揭示了 **Arid1a 和 Ctcf 功能缺失突变**如何扭曲 GC 轨迹（如暗区表型异常）。
- 通过 in silico 扰动预测：**Ctcf 敲除可拯救 Arid1a 功能丧失表型**，并提名 **Bcl6 和 Stat3** 为额外可拯救的 TF。
- **体内验证**：双杂合小鼠实验证实了所有预测的拯救效应（暗区表型正常化），并用多组学定量确认了模型捕获的分子改变。
- 该框架提供了**动态、细胞状态特异的 GRN**，恢复了 WT GRN 中许多已知调节边。

## 7. 优点

- **创新性**：首次将神经 ODE 与单细胞多组学深度融合，联合建模基因表达和染色质可及性动力学。
- **可预测性**：能够进行 in silico 扰动模拟，预测基因敲除或 TF 扰动的结果，直接产生可检验的实验假设。
- **可解释性**：通过 ODE 参数动态推断 GRN，并提供 TF 活性轨迹。
- **体内验证**：用小鼠模型实体验证计算预测，增强了可靠性，是计算生物学研究的亮点。
- **框架通用性**：方法原则上适用于任何具有时间（或伪时间）信息的多组学数据集。

## 8. 不足与局限

- **应用范围有限**：仅在 GC B 细胞上进行验证，能否推广到其他组织、疾病或发育系统尚不清楚。
- **数据依赖性强**：模型需要同时具有基因表达和染色质可及性的单细胞多组学数据，且 RNA 速度部分（剪接比例）的准确性会影响性能。
- **计算复杂度**：神经常微分方程训练较慢且对超参数敏感，未提供算力开销可能不利于复现。
- **扰动模拟的简化**：in silico 敲除通过强制设定基因表达为零实现，未模拟真实调控网络中的反馈效应。
- **未讨论偏差风险**：无法排除批次效应或测序噪声导致假阳性 GRN 边；体内验证仅针对双杂合突变，未测试全敲除更极端的表型。
- **缺乏与现有方法的定量对比**：未在标准基准（如 BEELINE 等）上评估 GRN 推断性能，优势主要靠生物学知识验证，缺少量化指标。

（完）
