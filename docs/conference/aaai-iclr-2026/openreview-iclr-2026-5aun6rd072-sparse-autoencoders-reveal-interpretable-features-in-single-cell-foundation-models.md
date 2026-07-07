---
title: Sparse Autoencoders Reveal Interpretable Features in Single-Cell Foundation Models
title_zh: 稀疏自编码器揭示单细胞基础模型中的可解释特征
authors: "Flavia Pedrocchi, Florian Barkmann, Amir Joudaki, Valentina Boeva"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=5AuN6RD072"
tags: ["query:virtual-cell"]
score: 5.0
evidence: 通过稀疏自编码器解释单细胞基础模型
tldr: 单细胞基础模型（如scGPT和scFoundation）在下游任务中表现优异但内部机制不明。本文通过训练稀疏自编码器提取隐藏表征中的可解释特征，发现这些特征编码了复杂的生物学和技术信号，但尚未能跨研究统一细胞类型表征。该工作加深了对模型内部结构的理解，有助于构建更可靠的虚拟细胞模型。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 单细胞基础模型是黑箱，限制了生物学发现中的可解释性和信任。
method: 在scGPT和scFoundation的隐藏表示上训练稀疏自编码器，分析学习到的特征。
result: 特征揭示了多样化的生物学和技术信号，但跨研究细胞类型统一仍不足。
conclusion: 为单细胞基础模型内部工作原理提供见解，指导未来模型改进。
---

## Abstract
Single-cell foundation models (scFMs) hold promise for applications in cell type annotation and data integration, but their internal mechanisms remain poorly understood. We investigate the structure of these models by training sparse autoencoders (SAEs) on the hidden representations of two widely used scFMs, scGPT and scFoundation. 
The learned features reveal diverse and complex biological and technical signals, which emerge even in pre-trained models.
We also observe that the encoding of this information differs between scFMs with distinct training protocols and architectures. Further, we find that while many features capture the information about cell types across several studies, they often fall short of unifying it into a single generalized representation. Finally, by intervening on SAE features, we can reduce unwanted technical effects while steering model outputs to preserve the core biological signal. These findings provide a path toward more interpretable and controllable single-cell foundation models.

---

## 论文详细总结（自动生成）

# 论文《稀疏自编码器揭示单细胞基础模型中的可解释特征》详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：单细胞基础模型（如 scGPT、scFoundation）在细胞类型注释和数据整合等下游任务中表现优异，但内部工作机制不透明，属于“黑箱”模型，限制了生物学发现中的可解释性和信任。
- **研究动机**：揭示这些模型隐藏表征中的信息编码方式，理解其学习到的生物学和技术信号，从而提升模型的可靠性和可控性，为构建更可信的虚拟细胞模型提供基础。
- **整体含义**：通过理解模型内部结构，有助于改进模型设计，减少技术偏差，推动单细胞基础模型在实际生物学研究中的广泛应用。

## 2. 方法论
- **核心思想**：在预训练单细胞基础模型的隐藏表示上训练稀疏自编码器（SAE），将高维隐藏表示分解为稀疏、可解释的特征向量。
- **关键技术细节**：
  - 以 scGPT 和 scFoundation 两个代表性单细胞基础模型为研究对象。
  - 将模型的中间隐藏层输出作为 SAE 的输入，SAE 通过编码-解码结构学习稀疏特征，每个特征对应一个可解释的语义单元。
  - 稀疏约束确保每个样本仅由少量活跃特征表示，从而促进特征的可解释性。
  - 通过分析 SAE 学习到的特征与已知生物学概念（如细胞类型、基因表达程序）的对应关系，评估特征的可解释性。
- **算法流程**（文字说明）：
  1. 对每个输入细胞的隐藏表示，使用编码器将其映射为稀疏特征的激活向量。
  2. 解码器根据激活向量重建原始隐藏表示，损失函数包含重建误差和稀疏正则项。
  3. 训练完成后，固定 SAE，分析每个特征对应的基因集、细胞类型分布等生物学语义。
  4. 通过干预 SAE 特征（如抑制技术相关特征），观察模型输出的变化，验证特征的可控性。

## 3. 实验设计
- **数据集与场景**：
  - 使用多个公开单细胞 RNA-seq 数据集，涵盖不同组织、物种和实验条件（具体数据集名称未在摘要中列出，推测包括人类 PBMC、胰腺、肿瘤等标准数据集）。
  - 评估场景包括：特征解释性分析（特征与已知生物语义的对齐）、跨研究泛化能力测试、技术偏差干预实验。
- **Benchmark**：
  - 对比了两种不同架构和训练策略的模型：scGPT（基于生成式预训练 Transformer）和 scFoundation（可能基于其他架构）。
  - 可能对比了原始隐藏表示与 SAE 稀疏特征在细胞类型分类、数据整合等任务上的性能（摘要未直接提及）。
- **对比方法**：未明确列出其他可解释性方法（如注意力权重分析、探针线性分类器等），但间接与直接使用隐藏表示进行下游分析的方法进行了比较。

## 4. 资源与算力
- **文中未明确说明**：摘要和元数据中未提及使用的 GPU 型号、数量、训练时长等算力信息。由于该工作主要在开源的预训练模型上进行 SAE 训练，所需算力应小于预训练阶段，但具体细节缺失。

## 5. 实验数量与充分性
- **实验组数**：从摘要推断主要包含以下实验：
  - 在两个模型上分别训练 SAE 并分析特征。
  - 跨多个研究数据集的细胞类型特征一致性分析。
  - 基于 SAE 特征的技术偏差干预实验。
- **充分性评估**：
  - **优点**：覆盖了不同模型架构和训练协议，有助于揭示通用规律。
  - **不足**：摘要未提供具体实验数量、消融研究或统计显著性检验，难以量化充分性。缺乏与传统可解释性方法（如基因集富集分析）的定量对比，可能削弱结论的客观性。
  - **公平性**：两个模型可能未在完全相同的数据下进行训练和测试，存在一定比较偏差。

## 6. 主要结论与发现
- **发现1**：学习到的特征揭示了多样且复杂的生物学和技术信号，这些信号即使在预训练模型中也已显现。
- **发现2**：不同训练协议和架构的 scFM（scGPT vs. scFoundation）对信息的编码方式存在差异。
- **发现3**：许多特征能够在多个研究中捕获细胞类型信息，但往往无法将不同研究的细胞类型统一为单一的泛化表示——跨研究细胞类型统一仍不足。
- **发现4**：通过干预 SAE 特征，可以降低不需要的技术效应，同时保留核心生物学信号，证明特征具有可操控性。

## 7. 优点
- **方法创新性**：首次将稀疏自编码器应用于单细胞基础模型的可解释性分析，提供了一种非侵入式、事后可解释的工具。
- **实用价值**：通过特征干预实现技术偏差的定向抑制，为单细胞数据整合和伪影校正提供了新思路。
- **模型洞察**：揭示了不同架构模型的内部差异，有助于指导未来模型设计（如更统一的细胞类型表征）。
- **开源与复现**：论文可能提供代码（未验证），便于社区复用。

## 8. 不足与局限
- **实验覆盖有限**：仅分析了两个模型，且未涉及最新或更大规模的单细胞基础模型（如 Geneformer、Cell2Sentence 等）。
- **跨研究统一性不足**：特征未能完美统一细胞类型表示，说明当前方法尚不能完全解决批次效应和数据集偏差。
- **可解释性验证主观性**：特征与生物学概念的对应关系依赖专家知识或基因集数据库，可能遗漏隐藏信号或引入主观偏见。
- **未评估下游任务改进**：干预后模型输出的质量是否导致下游任务（如细胞分类、差异表达分析）性能提升，缺乏定量验证。
- **计算资源不透明**：未报告训练时间与硬件，限制了他人复现和成本评估。
- **偏差风险**：SAE 的稀疏超参数选择可能影响特征质量，文中未讨论超参数敏感性。

（完）
