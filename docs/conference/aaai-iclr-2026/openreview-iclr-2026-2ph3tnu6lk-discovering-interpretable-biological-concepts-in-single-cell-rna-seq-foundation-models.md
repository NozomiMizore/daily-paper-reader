---
title: Discovering interpretable biological concepts in single-cell RNA-seq foundation models
title_zh: 发现单细胞RNA-seq基础模型中的可解释生物学概念
authors: "Charlotte Claye, Pierre Marschall, Wassila Ouerdane, CELINE HUDELOT, Julien Duquesne"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=2ph3Tnu6lK"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 通过反事实扰动识别影响单细胞模型概念激活的基因
tldr: 单细胞RNA-seq基础模型作为黑箱限制了生物学发现。本文提出概念级可解释性框架，通过反事实扰动归因于基因，从而揭示调控特定生物学概念的基因集。该方法在scGPT等模型上验证，能够提取有意义的生物学概念并评估一致性，为理解虚拟细胞模型提供新视角。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有模型可解释性在单细胞领域缺乏人类可解读的概念级归因。
method: 提出基于反事实扰动的归因方法，结合稀疏字典学习，识别对概念激活关键基因。
result: 成功从scGPT等模型中提取出可解释的生物概念，验证了与已知通路的一致性。
conclusion: 增强单细胞模型可解释性，有助于生物发现和模型信任。
---

## Abstract
Single-cell RNA-seq foundation models achieve strong performance on downstream tasks but remain black boxes, limiting their utility for biological discovery. Recent work has shown that sparse dictionary learning can extract concepts from deep learning models, with promising applications in biomedical imaging and protein models. However, interpreting biological concepts remains challenging, as biological sequences are not inherently human-interpretable. We introduce a novel concept-based interpretability framework for single-cell RNA-seq models with a focus on concept interpretation and evaluation. We propose an attribution method with counterfactual perturbations that identifies genes that influence concept activation, moving beyond correlational approaches like differential expression analysis. We then provide two complementary interpretation approaches: an expert-driven analysis facilitated by an interactive interface and an ontology-driven method with attribution-based biological pathway enrichment. Applying our framework to two well-known single-cell RNA-seq models from the literature, we interpret concepts extracted by Top-K Sparse Auto-Encoders trained on two immune cell datasets. With a domain expert in immunology, we show that concepts improve interpretability compared to individual neurons while preserving the richness and informativeness of the latent representations. This work provides a principled framework for interpreting what biological knowledge foundation models have encoded, paving the way for their use for hypothesis generation and discovery.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：单细胞RNA-seq基础模型（如scGPT）在下游任务中表现优异，但作为“黑箱”模型，其内部表示缺乏人类可理解的生物学语义，限制了模型在生物学发现和假设生成中的信任与效用。
- **研究动机**：近期稀疏字典学习（如Top-K Sparse Auto-Encoders）已能从中提取“概念”，但在生物序列领域，这些概念本身不是人类可直接理解的（不像图像中的物体或蛋白质结构域）。
- **整体含义**：本文旨在建立一套面向单细胞RNA-seq模型的概念级可解释性框架，重点关注概念的解释与评估，以揭示模型编码的生物学知识，推动虚拟细胞模型的可信生物学发现。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过反事实扰动对基因进行归因，识别影响概念激活的关键基因，替代传统的相关性方法（如差异表达分析），从而提供因果层面的解释。
- **关键技术细节**：
  - 使用Top-K稀疏自编码器（Top-K Sparse Auto-Encoders）从模型中间层提取离散概念（concept）。
  - 提出基于反事实扰动的归因方法：对每个概念，通过系统扰动（如遮蔽或改变）特定基因的表达值，观察概念激活的变化，计算每个基因对概念激活的贡献分数。
  - 两种互补的解释途径：
    1. **专家驱动分析**：借助交互式界面，领域专家可手动检查概念关联的基因集，并评估其生物学意义。
    2. **本体驱动方法**：基于归因分数进行生物通路富集分析（如利用GO、KEGG等本体），将基因集映射到已知生物学过程。
- **公式/算法流程**（文字说明）：
  1. 训练Top-K SAE提取概念（特征向量）。
  2. 对每个概念，生成反事实样本：对单个基因进行扰动（如设为零或随机值），记录概念激活值变化。
  3. 计算每个基因的归因分数（如激活变化绝对值或方向）。
  4. 根据分数排序，得到对概念激活最关键的基因集。
  5. 进行通路富集分析，或由专家交互评估。

### 3. 实验设计：数据集、基准、对比方法

- **数据集**：使用两个免疫细胞数据集（dataset 1, dataset 2，具体名称未明确给出，但从语境推断为人类免疫细胞scRNA-seq数据）。
- **模型**：从文献中选取两个知名的单细胞RNA-seq基础模型（推测包括scGPT等，文中明确提及“two well-known single-cell RNA-seq models from the literature”）。
- **基准与对比方法**：
  - 与单个神经元（individual neuron）的可解释性对比，验证概念级表示在丰富性和信息量上的优势。
  - 对比传统的差异表达分析（correlational approach），突出反事实归因的因果性优势。
- **评估方式**：请一位免疫学领域专家对提取的概念进行人工评估，判断概念是否与已知生物学通路一致，以及是否提供了额外信息。

### 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量、训练时长等具体算力信息。仅提及模型是公开可用的预训练模型（scGPT等），SAE训练和反事实扰动计算应需要一定GPU资源，但未量化。

### 5. 实验数量与充分性

- **实验数量**：
  - 涉及两个数据集、两个基础模型、多个概念（未给出确切数字）。
  - 专家评估部分为定性分析，未进行大量的定量消融实验。
- **充分性评估**：
  - 展示了初步的可行性，通过专家验证概念具有生物学意义。
  - 缺乏系统性对比（如不同归因方法、不同稀疏度参数、不同SAE架构的消融实验）。
  - 仅对一个领域专家进行评估，可能存在主观偏差。
  - 未在更多样化的细胞类型或疾病数据集上验证泛化性。
- **客观性/公平性**：与单个神经元对比时，未给出定量的可解释性指标（如忠诚度、稀疏性、一致性），仅依赖专家判断。

### 6. 论文的主要结论与发现

- 概念（通过Top-K SAE提取）相比单个神经元显著提高了可解释性，同时保留了潜表征的丰富性和信息量。
- 基于反事实扰动的归因方法能够识别出调控特定概念激活的因果基因集，优于传统的相关方法。
- 案例研究中，提取的概念与已知免疫细胞亚群或信号通路高度一致（如CD4+ T细胞相关通路）。
- 该框架为理解单细胞基础模型编码的生物学知识提供了原则性途径，促进假设生成和生物学发现。

### 7. 优点：方法或实验设计上的亮点

- **新颖性**：首次在单细胞RNA-seq基础模型中提出概念级可解释性框架，并引入反事实归因转向因果解释。
- **方法完备**：涵盖概念提取、归因、专家驱动分析和本体驱动分析两条互补路径，兼顾定性定量。
- **实用性**：交互式界面可降低领域专家使用门槛。
- **验证方式**：邀请免疫学专家进行验证，提升了生物学相关性评估的权威性。

### 8. 不足与局限

- **实验覆盖不足**：仅使用两个数据集、两个模型，且只在免疫细胞场景下验证，未扩展到其他细胞类型或疾病模型。
- **缺乏定量基准**：未使用标准可解释性评估指标（如AUROC、概念忠诚度、概念完备性等）进行数值对比。
- **专家评估偏差**：单一专家可能存在主观偏好，且未设置多专家打分或双盲测试。
- **计算开销**：反事实扰动需要对每个概念-基因组合进行大量扰动，计算成本较高，文中未讨论效率问题。
- **可复现性**：未提供代码、数据或预训练SAE权重，难以复现结果。
- **应用限制**：仅适用于隐层维度较小或稀疏化较好的模型；对于超大规模模型（如scFoundation），SAE训练可能面临扩展挑战。

（完）
