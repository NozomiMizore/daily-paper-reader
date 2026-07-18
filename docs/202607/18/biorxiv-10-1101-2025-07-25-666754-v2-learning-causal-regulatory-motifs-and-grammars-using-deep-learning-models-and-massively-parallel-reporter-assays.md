---
title: Learning causal regulatory motifs and grammars using deep learning models and massively parallel reporter assays
title_zh: 利用深度学习模型和大量并行报告基因检测学习因果调控模体和语法
authors: "Thompson, M., Lehner, B."
date: 2026-07-15
pdf: "https://www.biorxiv.org/content/10.1101/2025.07.25.666754v2.full.pdf"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 使用深度学习和大规模并行报告分析预测基因表达，从而实现遗传扰动响应预测
tldr: 解读基因表达的第二遗传密码需要准确预测和机制理解。结合MPRA数据与深度学习，通过模拟1500种基序架构评估不同模型和xAI方法。发现注意力模型在低数据量时高效，但大样本时扩张CNN性能更优；基序提取方法偏向报告效应量大的基序，效应量排序准确但校准偏差，尤其在存在交互作用时。提出了识别上位性基序的新指标，为MPRA实验从头到尾的建模与解释提供实用指导。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-07-25-666754-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1710, \"height\": 1074, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-07-25-666754-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1646, \"height\": 1011, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-07-25-666754-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1577, \"height\": 1867, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-07-25-666754-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1582, \"height\": 1141, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-07-25-666754-v2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1692, \"height\": 1044, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-07-25-666754-v2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1284, \"height\": 871, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-1101-2025-07-25-666754-v2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1397, \"height\": 624, \"label\": \"Table\"}]"
motivation: 预测和解释基因表达的第二遗传密码，需要通过大规模数据与AI结合来识别因果调控基序及其语法。
method: 通过大规模模拟1500种基序遗传架构，评估注意力模型、扩张CNN等架构及多种xAI方法预测表达和提取基序的能力。
result: 注意力模型低数据高效但大样本不如扩张CNN；基序提取优先报告大效应量；效应量排序准确但校准偏差，尤其存在上位性时。
conclusion: 提出识别上位性基序的新指标，并在三个实验数据集中验证，为MPRA实验建模与解释提供实用指导。
---

## 摘要
生物学中的一个核心挑战是理解、预测和设计“第二遗传密码”：序列如何编码基因表达。这一挑战的两个组成部分是：(1) 从序列准确预测（和设计）基因表达，以及 (2) 对序列到表达编码在细胞中实际运作机制的机理性理解。解决这一问题的一个强大通用方法是将大规模数据生成与人工智能相结合。例如，大量并行报告基因检测（MPRAs）可以在混合实验中量化数千种不同序列的表达，所得数据可用于训练深度学习模型。与长上下文基因组语言模型（其中基于Transformer的架构是主流范式）不同，对于MPRA数据集，其他架构组件是否能导致更有用、更可泛化的预测器，以及它们是否影响模型的可解释性（即捕获因果生物学机制的能力，无论是固有的还是在使用下游可解释性或解释性技术“xAI”时），仍然存在争议。消融分析可能有助于阐明重要的架构组件，但几乎都是零散的，无法描述可泛化的趋势，因为它们是在单个训练数据集或少数测试数据集上进行的。在这里，我们试图通过大规模模拟1,500个基于模体的遗传架构，并评估不同模型架构-xAI组合首先从序列输入预测结果、其次报告所涉及的模体及其相应语法的能力，来调和这些关切并为MPRA模型设计和xAI选择提供指导。我们发现基于注意力的模型是高效的学习者，虽然我们建议在低数据情况下使用它们，但在更大样本量下，它们的性能被替代模型（如扩张卷积神经网络）所超越。接下来，我们证明，在不同的语法和模型中，当前的模体提取方法趋向于报告同一组模体，这些模体主要由具有大效应大小的模体主导。然后，我们对各种模型及其发现的模体进行计算机模拟实验，发现这些方法根据学习到的效应大小准确地对模体进行排序，但学习到的效应大小系统地存在校准偏差，特别是在存在相互作用（上位性）的情况下。最后，我们提出了一种识别参与上位性的模体的新指标，并在三个实验数据集中确认了我们的发现。我们的工作为端到端建模和解释大量并行报告基因检测实验提供了实用指导。

## Abstract
A central challenge in biology is to understand, predict, and engineer the 'second genetic code': how sequence encodes gene expression. Two components of this challenge are: (1) accurate prediction (and design) of gene expression from sequence and (2) mechanistic understanding of how sequence-to-expression encoding actually works in cells. A powerful general approach to this problem is to combine large scale data generation with artificial intelligence. For example, massively parallel reporter assays (MPRAs) can quantify the expression of thousands of different sequences in pooled experiments and the resulting data can be used to train deep learning models. Unlike in the case of long-context genomic language models, where transformer-based architectures are a dominant paradigm, it remains contested whether for MPRA datasets other architectural components can lead to more useful, generalizable predictors, and whether they affect model interpretability, i.e. the ability to capture causal biological mechanisms (either inherently or when using downstream interpretability or explainability techniques, "xAI"). Ablation analyses may help elucidate important architectural components, but are almost always anecdotal, unable to describe generalizable tendencies, as they are done with a single training dataset or a few testing datasets. Here, we attempt to reconcile concerns and provide guidance for MPRA model design and xAI choice by simulating at scale 1,500 motif-based genetic architectures and evaluating the ability of different model architecture-xAI pairs to first predict an outcome given a sequence as input, and second, report involved motifs and their corresponding grammar. We find that attention-based models are efficient learners, and while we recommend their use in low-data regimes, their performance is surpassed by alternative models, like dilated CNNs, under larger sample sizes. We next show that across grammars and models, current methods for motif extraction converge toward reporting the same set of motifs, which is dominated by motifs with large effect sizes. We then perform in silico experiments across models and their discovered motifs and find that these methods accurately rank motifs based on learned effect size, but that their learned effect size is systematically miscalibrated, particularly in the presence of interactions (epistasis). Finally, we propose a novel metric for identifying motifs involved in epistasis and confirm our findings across three experimental datasets. Our work provides practical guidance for modeling and interpreting massively parallel reporter assay experiments from end to end.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：解读“第二遗传密码”——DNA序列如何决定基因表达——是生物学重要挑战。具体包括(1)从序列准确预测基因表达；(2)理解序列-表达编码的机制。
- **背景**：大规模并行报告基因检测（MPRA）可高通量测量数千条序列的表达，结合深度学习模型可从中学习调控语法。但针对MPRA数据集，不同神经网络架构（如Transformer、CNN、LSTM等）及可解释性方法（xAI）的选择尚存争议，缺乏系统性指导。
- **整体含义**：本研究旨在通过大规模模拟和实验验证，评估不同架构与xAI组合在预测性能和模体发现上的表现，提供端到端建模MPRA实验的实用指南。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：构建模拟框架，以模体（motif）作为主要遗传效应来源，生成大量具有不同遗传语法（加性、上位性、混合）的合成序列-表型数据集。在此基础上训练多种神经网络架构，并应用多种xAI方法提取模体，评价其发现因果模体及学习语法（效应大小、交互作用）的能力。
- **关键技术细节**：
  - **模拟生成过程**：基于随机序列（200 bp），从JASPAR数据库选取模体，按随机频率植入序列，表型由方差组分模型生成：
    \[
    y = M\beta + I\gamma + \epsilon
    \]
    其中 \(M\) 为模体存在矩阵，\(\beta\) 为加性效应，\(I\) 为交互项，\(\gamma\) 为上效应，\(\epsilon\) 为噪声。设置可解释性（heritability）为100%，并通过参数 \(\alpha\) 控制加性与上位性变异比例。
  - **交互类型**：包括简单共存、上游依赖、距离依赖（≤5 bp）、高阶（三模体）四种。
  - **神经网络架构**：统一使用第一层卷积（指数激活模拟位置权重矩阵），其后分别接入注意力、无池化注意力、堆叠卷积、扩张卷积（含/不含残差连接）、LSTM（仅最终状态/全隐藏状态）等8种结构，参数规模均控制在约50万。
  - **xAI方法**：包括第一层滤波器可视化、梯度（校正）、梯度×输入、in silico诱变（ISM）、SHAP（梯度近似）。使用TF-MoDISco从重要性得分中聚类发现模体，并与真实模体通过TOMTOM比对（q<0.05为发现）。
  - **效应大小评估**：全局重要性分析（GIA）：对每个候选模体，随机植入序列并计算模型输出变化均值。并扩展二阶矩（方差）及协方差指标来指示上位性参与。

### 3. 实验设计：使用了哪些数据集/场景，基准测试是什么，对比了哪些方法

- **模拟数据集**：1500个模拟场景（不同样本量：10k、50k、100k；不同加性/上位性比例α=0,0.5,1；不同噪声水平等）。每个场景生成10个独立数据集，共约15000个训练实例。
- **真实数据集**：
  1. **Frömel et al. (随机序列)**：合成随机序列（植入已知模体），K562细胞中测量活性，N=30,000，长度200 bp。
  2. **Agarwal et al. (基因组元件)**：内源性人基因组调控元件，K562和HepG2细胞系，N≈230,000和150,000，长度200 bp。
- **基准测试**：对比8种模型架构在预测性能（皮尔逊相关系数）上的差异，以及多种xAI方法在因果模体发现（AUROC）、效应大小排序（Spearman相关）、校准（回归斜率）上的表现。
- **对比方法**：基线（仅卷积+MLP）、注意力（有/无池化）、堆叠CNN、扩张CNN（有/无残差）、LSTM（两种输出方式）。xAI方法：梯度、梯度×输入、ISM、SHAP、第一层滤波器。

### 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量、训练时长等具体计算资源。仅提及使用了UCLA Hoffman2服务器支持。训练参数：batch size=1000，epochs=1000，早停（patience=50），学习率衰减（patience=5）。模型参数量约50万，训练实例数从10k到100k不等。对于1500个模拟场景×8种架构×多次运行，总计算量较大但未量化。

### 5. 实验数量与充分性

- **模拟实验**：共1500个参数组合（样本量×遗传架构×是否含非模体效应等），每个组合10次独立数据生成，每次训练一种模型，共训练约15000次。此外，真实数据集上每种架构训练10次，下采样实验训练30次（3种种子×10重复）。
- **消融实验**：对注意力模型测试池化与否；对CNN测试扩张与残差；对LSTM测试仅最终状态vs全部隐藏状态。
- **充分性**：实验规模大，覆盖多种遗传语法和样本量，统计检验充分（配对t检验、线性模型、置换检验），结果在三个独立真实数据集上验证。结论稳健，具有一定泛化性。但模拟基于随机序列背景，真实基因组上下文更为复杂，且参数空间有限（仅10个模体、固定交互类型等）。

### 6. 论文的主要结论与发现

1. **注意力模型是高效学习者**：在低样本（10k）时表现最优，尤其在非加性语法下领先其他架构10%以上；但样本增大后（100k），扩张CNN和LSTM超越注意力。
2. **不同xAI方法收敛于同一组模体**：模体发现结果高度重叠，以效应量大的模体为主。ISM在CNN/LSTM中最为鲁棒，梯度×输入在注意力模型中高效。
3. **GIA效应排序准确但校准偏差**：效应量排序与真实值高相关（Spearman >0.9），但规模上对交互模体存在偏差（校准斜率偏离1）。
4. **二阶矩指标可指示上位性**：GIA方差（尤其残差化后）可区分是否参与交互，AUC约0.7-0.8，但检测能力中等，且距离依赖交互难检测。
5. **验证于真实数据**：在Frömel et al. 数据中确认Fli1、Gata/Spil等已知交互；在Agarwal et al. 中发现CTCF、HNF1A/B等具高方差低均值效应，暗示上位性参与。

### 7. 优点

- **大规模模拟框架**：1500个场景覆盖广泛遗传语法，结果统计意义强，避免单数据集偏差。
- **系统性对比**：同时评估预测性能、模体发现、效应校准和交互检测，是首个端到端评估xAI与架构匹配的研究。
- **新指标提出**：二阶矩（方差/协方差）用于上位性检测，计算复杂度线性于模体数，比现有二次方法高效。
- **验证充分**：模拟结论在三个真实MPRA数据集上复现，增强可推广性。
- **实用指导**：提供具体建议（低样本用注意力、大样本用扩张CNN、用ISM获取模体等），实用性高。

### 8. 不足与局限

- **模拟局限**：背景序列为随机均匀，未模拟真实基因组复杂背景（重复元件、染色质状态等）。模体设置固定为10个，交互类型有限（4种），未涵盖更复杂层次。
- **架构固定**：未进行超参数优化，仅固定参数预算（约50万），实际应用可能通过调参改变结论。模型规模较小（~500k参数），与现代基础模型（数千万）差距大。
- **计算资源未报告**：无法复现具体训练成本。
- **交互检测能力有限**：二阶矩指标AUC仅0.7-0.8，尤其对距离依赖交互几乎失效，且无法区分交互类型。
- **真实数据验证局限**：基因组序列中背景模体数巨大（JASPAR 500+），且缺乏真实效应标签，某些分析（如效应校准）仅能定性。
- **未涉及预训练基础模型**：文中未探讨大规模预训练语言模型微调于MPRA数据的表现，这是当前重要方向。

（完）
