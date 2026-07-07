---
title: "CellxPert: An Efficient Reasoning Language Model for Single-Cell and Spatial Multi-Omics"
title_zh: CellxPert：一种用于单细胞和空间多组学的高效推理语言模型
authors: "Andac Demir, Srayanta Mukherjee"
date: 2025-09-20
pdf: "https://openreview.net/pdf?id=gfamCTnXMg"
tags: ["query:virtual-cell"]
score: 7.0
evidence: 单细胞扰动预测的多模态基础模型
tldr: 单细胞多模态数据融合面临异构整合挑战。本文提出CellxPert，一个可扩展的多模态基础模型，将转录组、染色质可及性和表面蛋白组等数据统一到共同表示空间。该模型支持细胞类型注释、高效微调和全基因组转录组预测，为单细胞扰动响应预测提供了基础能力。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 单细胞多模态数据异构，需要统一的基础模型以支持多种下游任务。
method: 构建多模态基础模型，联合编码多种组学数据，并整合空间视觉层。
result: CellxPert在细胞类型注释等任务上取得最优，且支持高效微调。
conclusion: 为单细胞多组学分析提供了统一的框架，可支撑扰动响应建模。
---

## Abstract
In this work, we introduce CellxPert, a scalable multimodal foundation model that unifies single-cell and spatial multi-omics within a common representation space. CellxPert jointly encodes transcriptomic (scRNA-seq), chromatin-accessibility (ATAC-seq), and surface-proteomic (CITE-seq) measurements, while directly incorporating MERFISH and imaging mass-cytometry data as 2D or 3D spatial–visual layers. CellxPert facilitates four key downstream tasks out of the box: (i) cell‑type annotation across a broad ontology of 154 largely overlapping identities—the largest label space addressed to date and a stringent test of fine‑grained discrimination, (ii) efficient fine-tuning using Low Rank Adaptation (LoRA), (iii) genome-wide transcriptomic response prediction to in silico perturbations (ISP), and (iv) seamless multi-omic integration across various assays and platforms. Unlike current single-cell foundation models, which approximate gene perturbations by deleting or reordering tokenized gene expression ranks, CellxPert employs a Metropolis–Hastings sampler whose proposal kernel uses the model’s masked conditional distributions to transition to new transcriptomic states conditioned on the perturbed genes. This Markov‑chain procedure mitigates out‑of‑distribution artifacts introduced by abrupt token manipulation and produces trajectories that are biologically interpretable. Evaluations on PBMC68K, Replogle Perturb-seq, Systema and BMMC benchmarks show CellxPert outperforming classical and state-of-the-art baselines in cell-type annotation, perturbation-aware reasoning, and multi-omic integration by a significant margin.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：单细胞和空间多组学数据高度异构，不同模态（转录组、染色质可及性、表面蛋白组、空间成像等）缺乏统一的表示空间，导致下游分析（如细胞类型注释、扰动预测、多模态整合）面临挑战。
- **研究动机**：现有单细胞基础模型通常仅处理单模态（如scRNA-seq），或通过简单删除/重排基因表达token来模拟扰动，产生分布外伪影。亟需一个可扩展的多模态基础模型，能够统一编码多种组学数据，并支持细粒度推理和高效微调。
- **整体含义**：CellxPert旨在作为单细胞和空间多组学的“虚拟细胞”基础模型，为细胞扰动响应预测、细胞类型注释等任务提供统一的推理框架。

## 2. 论文提出的方法论

- **核心思想**：构建多模态基础模型，将转录组（scRNA-seq）、染色质可及性（ATAC-seq）、表面蛋白组（CITE-seq）以及空间数据（MERFISH、成像质谱）统一嵌入到共同表征空间。模型支持：①细胞类型注释（154个标签）；②通过LoRA高效微调；③全基因组转录组响应预测（in silico perturbation, ISP）；④跨平台多模态整合。
- **关键技术细节**：
  - **扰动推理机制**：不同于现有方法直接删除或重排token化的基因表达排名，CellxPert采用**Metropolis-Hastings采样器**，其提议核使用模型自身的掩蔽条件分布，将采样转移到基于扰动基因的新转录组状态。这种马尔可夫链过程减少了突然token操作带来的分布外伪影，生成生物学可解释的轨迹。
  - **多模态编码**：将不同组学数据作为独立的输入模态，通过共享的编码器（可能基于Transformer或类似架构）映射到统一嵌入空间，并融合空间视觉层（2D/3D）。
  - **微调策略**：使用低秩适配（LoRA）进行高效微调，适用于不同下游任务。
- **公式/算法流程说明**：未给出具体公式，但核心算法为Metropolis-Hastings采样结合掩蔽条件分布，流程可描述为：（1）给定扰动基因集合；（2）从当前状态通过模型条件分布生成提案状态；（3）根据接受概率决定是否转移；（4）迭代生成最终转录组预测。

## 3. 实验设计

- **使用的数据集与场景**：
  - PBMC68K（外周血单核细胞）
  - Replogle Perturb-seq（大规模扰动测序数据）
  - Systema（多组学数据集）
  - BMMC（骨髓单核细胞）
  - 共四个基准数据集，覆盖不同模态和扰动场景。
- **基准测试（benchmark）**：细胞类型注释、扰动感知推理、多模态整合等任务。
- **对比方法**：包括经典方法（如PCA、聚类）和最新最先进的方法（具体名称未在摘要中列出，但提到“outperforming classical and state-of-the-art baselines”）。

## 4. 资源与算力

- 论文摘要及元数据中**未明确说明**使用的GPU型号、数量、训练时长等计算资源信息。因此无法推断算力开销，但根据“可扩展”、“高效微调”等描述，推测模型训练可能需要较高算力，但推理和微调相对轻量。

## 5. 实验数量与充分性

- **实验数量**：明确在四个数据集上进行了评估，涵盖细胞类型注释、扰动预测、多模态整合等任务。但未提及消融实验、参数敏感性分析等内部验证。
- **充分性与公平性**：实验覆盖了多个标准单细胞多组学基准，对比了经典和SOTA方法，并取得了显著提升。但缺少对模型规模的消融、不同采样策略的对比、以及跨领域泛化性的测试。总体而言验证了核心贡献，但全面性尚有提升空间。

## 6. 论文的主要结论与发现

- CellxPert在细胞类型注释（154个细粒度标签）上优于所有对比方法，证明其细粒度判别能力。
- 通过Metropolis-Hastings采样进行扰动预测，相比直接token操作减少了分布外伪影，生成了生物学可解释的轨迹。
- 支持高效的LoRA微调，便于适应不同下游任务。
- 统一了多种组学数据（包括空间模态），实现了无缝的多模态整合。

## 7. 优点

- **方法创新**：首次将Metropolis-Hastings采样引入单细胞扰动预测，有效避免传统方法的分布外伪影，提升生物学可解释性。
- **多模态统一**：联合编码转录组、染色质、蛋白组和空间数据，覆盖了当前主要单细胞组学类型，实用性强。
- **标签空间最大**：细胞类型注释覆盖154个重叠标签，是迄今为止最大的细粒度标签空间，验证了模型对高度相似类别的区分能力。
- **高效微调**：采用LoRA，降低了模型适应新任务的计算成本。

## 8. 不足与局限

- **实验覆盖有限**：只使用了四个公共数据集，未在更多样化的组织/疾病数据上验证泛化性。
- **消融实验缺失**：未明确报告对模型设计（如编码器结构、采样器配置、LoRA秩等）的消融研究，难以评估各组件贡献。
- **计算资源未公开**：影响可复现性和实际部署评估。
- **偏差风险**：训练数据可能主要来自健康样本，在疾病或罕见细胞类型上的表现未知；扰动预测可能依赖于已知扰动基因，对新扰动的外推能力需进一步验证。
- **应用限制**：Metropolis-Hastings采样可能增加推理时间，对实时分析场景不友好；且最终模型是“Rejected”状态，可能仍有缺陷未被评审接受。

（完）
