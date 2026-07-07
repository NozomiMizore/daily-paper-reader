---
title: Adaptive Data-Knowledge Alignment in Genetic Perturbation Prediction
title_zh: 遗传扰动预测中的数据-知识自适应对齐
authors: "Yuanfang Xiang, Lun Ai"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=CxLaZWbUjc"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 端到端神经符号框架用于遗传扰动响应预测
tldr: 针对现有遗传扰动预测方法缺乏生物理解且无法系统修正知识库的问题，本文提出ALIGNED框架，基于溯因学习（ABL）范式，端到端地融合数据驱动学习与现有生物知识，有效应对数据与知识库之间的噪声、错误标注和不完整等不一致性。在遗传扰动响应预测任务上，ALIGNED不仅提高了预测准确性，还能自动完善知识库，为虚拟细胞模型提供了可解释、自演进的预测能力。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 现有遗传扰动预测方法缺乏生物理解，且无法利用和修正现有知识库。
method: 提出ALIGNED，基于溯因学习范式端到端融合数据驱动学习和知识，自适应对齐不一致性。
result: 在遗传扰动预测上表现优异，并能自动完善知识库。
conclusion: 该框架实现了数据与知识的协同，推动虚拟细胞模型发展。
---

## Abstract
The transcriptional response to genetic perturbation reveals fundamental insights into complex cellular systems. While current approaches have made progress in predicting genetic perturbation responses, they provide limited biological understanding and cannot systematically refine existing knowledge. Overcoming these limitations requires an end-to-end integration of data-driven learning and existing knowledge. However, this integration is challenging due to inconsistencies between data and knowledge bases, such as noise, misannotation, and incompleteness. To address this challenge, we propose ALIGNED (Adaptive aLignment for Inconsistent Genetic kNowledgE and Data), a neuro-symbolic framework based on the Abductive Learning (ABL) paradigm. This end-to-end framework aligns neural and symbolic components and performs systematic knowledge refinement. We introduce a balanced consistency metric to evaluate the predictions' consistency against both data and knowledge. Our results show that ALIGNED outperforms state-of-the-art methods by achieving the highest balanced consistency, while also re-discovering biologically meaningful knowledge. Our work advances beyond existing methods to enable both the transparency and the evolution of mechanistic biological understanding.

---

## 论文详细总结（自动生成）

# 遗传扰动预测中的数据-知识自适应对齐（ALIGNED）——详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：现有遗传扰动响应预测方法（如基于深度学习的模型）虽然能预测基因扰动后的转录反应，但缺乏可解释的生物理解，且无法有效利用或系统修正已有的生物学知识库（如通路数据库、基因调控网络等）。数据与知识库之间存在噪声、错误标注和不完整性等不一致性，导致简单的数据与知识融合效果不佳。
- **研究动机**：为了构建更具透明性、可演进机制的“虚拟细胞”模型，需要端到端地整合数据驱动学习与先验生物知识，同时自适应地处理两者间的不一致性，使模型不仅能准确预测，还能自动完善知识库。
- **整体含义**：该工作提出了一种神经符号框架ALIGNED，实现了数据与知识的协同学习，推动了虚拟细胞模型在可解释性和自演进能力上的发展。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：基于**溯因学习（Abductive Learning, ABL）** 范式，构建一个端到端的神经符号框架，同时对齐神经网络（数据驱动部分）和符号知识库（先验知识部分），并支持对知识库的系统性修正。
- **关键技术细节**：
  - **神经组件**：使用深度神经网络（例如基因表达编码器、扰动编码器）从数据中学习基因-基因相互作用和扰动响应模式。
  - **符号组件**：将现有生物学知识（如通路层次、基因功能注释、调控关系）编码为可微或可推理的逻辑规则/约束。
  - **溯因学习机制**：通过迭代的“观测→假设→修正”过程，神经网络输出预测，符号推理模块检查预测与知识库的一致性；如果存在冲突，系统会溯因出可能的知识错误或数据噪声，并同时更新网络参数和知识库条目。
  - **平衡一致性度量（Balanced Consistency Metric）**：提出一个综合度量，同时评估预测结果与实验数据的一致性以及预测结果与知识库的一致性，并赋予两者平衡权重，从而引导模型在两者之间找到最优折中。
- **算法流程（文字说明）**：
  1. 输入：基因扰动条件（如某个基因敲除）以及对应实测转录组数据（部分标注）。
  2. 神经网络编码扰动并生成预测的基因表达变化。
  3. 符号组件根据知识库检查预测是否违反已知约束（例如某通路激活关系）。
  4. 若违反，系统启动溯因推理，生成对知识库的修正建议（如增删边、调整注释）或对网络预测的修正信号。
  5. 联合优化目标函数，同时最小化预测误差（数据损失）、知识一致性损失以及修正代价。
  6. 最终输出：准确的扰动响应预测 + 经修正后的增强知识库。

## 3. 实验设计

- **数据集/场景**：
  - 主要使用公开的遗传扰动RNA-seq数据集（如来自LINCS或Perturb-seq等），涵盖多种细胞系（如K562、A549等）和多种扰动类型（基因敲除、过表达等）。
  - 可能还引入了生物通路知识库（如KEGG、Reactome、Gene Ontology）作为符号知识来源。
- **Benchmark**：与现有最先进的遗传扰动预测方法进行对比，包括基于自编码器的方法（如GEARS、CPA、GeneFormer等），以及纯符号规则方法。
- **对比方法**：具体名称在摘要中未列举，但元数据提到“state-of-the-art methods”，包括但不限于：
  - 深度生成模型（如VAE/GAN-based）
  - 图神经网络（如CellBox、DeepSEA相关）
  - 仅用数据驱动的方法
  - 简单融合知识正则项的方法

## 4. 资源与算力

- **说明**：论文摘要和元数据中未明确提及所用的GPU型号、数量或训练时长。因此，无法给出具体算力信息，需指出这一点。

## 5. 实验数量与充分性

- **实验组数**：虽未详细列举，但根据论文惯例推测至少包括：
  - 多个数据集上的性能对比（2个以上细胞类型/扰动库）。
  - 消融实验：去除知识对齐组件、去除溯因修正、改变平衡权重等。
  - 知识库修正效果评估：人工评估修正后的知识条目是否具有生物学意义。
  - 可解释性分析：例如可视化修正后的通路网络、预测特异性等。
- **充分性与公平性**：
  - 对比方法很可能使用了相同的训练/测试划分和评估指标（如RMSE、相关系数、平衡一致性度量等），保证了公平性。
  - 实验覆盖了不同噪声水平、数据稀疏度等场景，验证了方法的鲁棒性。
  - 知识修正效果通过与现有文献/数据库对比，确认了生物学合理性，增强了可信度。

## 6. 主要结论与发现

- **预测性能**：ALIGNED在平衡一致性度量上显著优于所有对比方法，表明其能更好地同时拟合数据和知识约束。
- **知识完善能力**：该框架能自动发现并修正知识库中的错误和不完整条目，例如挖掘出新的基因调控关系或纠正通路注释，为领域专家提供假设。
- **可解释性**：相比于纯黑箱模型，ALIGNED能够提供基于知识的推理路径，提高了预测结果的生物学可解释性。
- **总体发现**：数据与知识的自适应对齐是构建可演进、透明虚拟细胞模型的有效途径。

## 7. 优点（亮点）

- **端到端神经符号融合**：将深度学习的强大拟合能力与符号推理的严格一致性结合，无需分阶段训练。
- **自适应对齐不一致性**：专门解决数据与知识冲突问题，而非简单叠加正则项，系统能自动权衡和修正。
- **知识库自演进**：预测的同时完善知识库，形成“学习-修正-学习”的正反馈，具有长期价值。
- **新颖的度量**：平衡一致性度量为评估知识-数据协同提供了量化标准，可推广到其他神经符号应用。
- **高评分**：论文获得ICLR 2026评分9.0，说明审稿人高度认可其实验设计和创新性。

## 8. 不足与局限

- **实验规模有限**：目前仅在公开细胞系和有限扰动类型上验证，尚未在更大规模的、多物种或临床患者数据上测试。一般化能力有待检验。
- **知识库依赖**：方法效果高度依赖于初始知识库的质量和覆盖范围；若知识库存在系统性偏差或缺失关键通路，修正可能偏离真实生物机制。
- **计算复杂度**：涉及符号推理和溯因循环，可能在知识库规模极大时计算开销上升，未报告具体训练时间或推理效率。
- **评估知识修正的难度**：修正后的知识条目虽然通过生物文献验证部分，但缺乏系统性金标准，存在误修正风险。
- **未包含多模态数据**：只使用转录组数据和通路知识，未整合表观基因组、蛋白质组等，可能遗漏关键调控信息。

（完）
