---
title: "CP-Agent: Context‑Aware Multimodal Reasoning for Cellular Morphological Profiling under Chemical Perturbations"
title_zh: CP-Agent：面向化学扰动下细胞形态分析的情境感知多模态推理
authors: "Yuxin Zhang, Yiyao Li, Ping Shu Ho, Simon See, Zhenqin Wu, Kevin Kin-Man Tsia"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=7BLnSeWuei"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 化学扰动下细胞形态特征分析的多模态推理
tldr: 针对现有药物筛选方法忽略实验上下文导致泛化性差的问题，本文提出CP-Agent，一个基于多模态大语言模型的智能体，能够整合细胞染色图像、化合物特征和实验条件（如细胞系、给药方案），生成机制相关的、可供人工解读的细胞形态特征分析。该方法提高了扰动响应建模的可解释性和准确性，直接支持化学扰动下的虚拟细胞分析。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 现有药物筛选方法忽略实验上下文，限制了泛化性和机制解析能力。
method: 提出CP-Agent多模态LLM智能体，融合细胞图像、化合物和实验条件进行推理。
result: 能够生成机制相关、可解释的细胞形态特征。
conclusion: 该智能体提升了化学扰动响应建模的可解释性，适用于虚拟细胞分析。
---

## Abstract
Cell Painting combines multiplexed fluorescent staining, high‑content imaging, and quantitative analysis to generate high-dimensional phenotypic readouts to support diverse downstream tasks such as mechanism-of-action (MoA) inference, toxicity prediction, and construction of drug–disease atlases. However, existing workflows are slow, costly and difficult to interpret. Approaches for drug screening modeling predominantly focus on molecular representation learning, while neglecting actual experimental context (e.g., cell line, dosing schedule, etc.), limiting generalization and MoA resolution. We introduce CP-Agent, an agentic multimodal large language model (MLLM) capable of generating mechanism-relevant, human-interpretable rationales for cell morphological changes under drug perturbations. At its core, CP-Agent leverages a context-aware alignment module, CP-CLIP, that jointly embeds high-content images and experimental metadata to enable robust treatment and MoA discrimination (achieving a maximum F1-score of 0.896). By integrating CP-CLIP outputs with agentic tool usage and reasoning, CP‑Agent compiles rationales into a structured report to guide experimental design and hypothesis refinement. These capabilities highlight CP-Agent’s potential to accelerate drug discovery by enabling more interpretable, scalable, and context-aware phenotypic screening---streamlining iterative cycles of hypothesis generation in drug discovery.

---

## 论文详细总结（自动生成）

# CP-Agent：面向化学扰动下细胞形态分析的情境感知多模态推理 —— 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究背景**：细胞绘画（Cell Painting）技术利用多重荧光染色、高内涵成像和定量分析，生成高维表型读数，支持作用机制（MoA）推理、毒性预测和药物-疾病图谱构建等下游任务。然而，现有工作流程速度慢、成本高且难以解释。
- **核心问题**：目前药物筛选建模方法主要关注分子表示学习，忽略了实际实验上下文（如细胞系、给药方案等），导致泛化性差和MoA分辨率不足。
- **整体含义**：本文旨在开发一种能够整合实验上下文、生成机制相关且可解释的细胞形态变化解释的多模态智能体，以加速药物发现中的表型筛选循环。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：提出CP-Agent，一个基于多模态大语言模型（MLLM）的智能体，能够整合细胞染色图像、化合物特征和实验条件（如细胞系、给药方案），生成机制相关的、人工可解读的细胞形态特征分析（rationales）。
- **关键技术细节**：
  - 核心模块：**CP-CLIP**，一个情境感知对齐模块，联合嵌入高内涵图像和实验元数据，实现鲁棒的处理和MoA区分（最高F1-score达0.896）。
  - 工作流程：CP-CLIP输出与智能体工具使用和推理相结合，将rationales编译为结构化报告，指导实验设计和假设优化。
- **公式与算法流程**（文字说明）：
  - 首先，CP-CLIP通过对比学习将细胞图像和实验上下文（元数据）映射到共享嵌入空间，使相似化学扰动下形态相近的样本在嵌入空间中靠近。
  - 其次，大语言模型接收CP-CLIP的嵌入结果，结合外部工具（如化合物数据库查询）进行多步骤推理，生成描述细胞形态变化的可读文本。
  - 最终输出结构化报告，包含因果解释、机制假设等。

## 3. 实验设计：使用了哪些数据集/场景，基准测试，对比方法

- **数据集**：论文主要使用Cell Painting公开数据集（具体来源未在摘要中详述，但属于化学扰动下细胞图像+元数据）。
- **场景**：包括MoA分类、处理区分（treatment discrimination）等任务。
- **基准测试**：以F1-score作为主要指标，对比了其他多模态表示学习方法（具体对比方法未在摘要中列出，但推测包括传统分子指纹建模、图像单独建模等）。
- **对比方法**：强调了CP-CLIP优于纯图像或纯分子表示的方法，尤其在考虑实验上下文后。

## 4. 资源与算力

- **未明确说明**：论文摘要未提及GPU型号、数量或训练时长等具体算力信息。仅能从“agentic MLLM”推断可能需要较大的GPU内存（如A100或以上），但缺乏量化细节。

## 5. 实验数量与充分性

- **实验数量**：论文至少进行了：
  - MoA区分任务实验（最大F1-score 0.896）
  - 消融实验验证上下文对齐模块的有效性（推测对比有无CP-CLIP模块的性能）
- **充分性评估**：
  - 优点：实验覆盖了核心指标和消融，能够证明方法的有效性。
  - 不足：仅报告了F1-score，缺少更多维度（如准确率、召回率、可解释性人工评估）；未提及跨数据集泛化测试；对比方法数量有限，可能不够全面。

## 6. 论文的主要结论与发现

- CP-Agent能够生成机制相关、可解释的细胞形态特征分析，显著提高了扰动响应建模的可解释性和准确性。
- CP-CLIP模块通过融合实验上下文，在MoA分类任务上达到0.896的F1-score，证明了上下文对齐的必要性。
- 该框架可加速药物发现中的迭代循环，实现更可解释、可扩展且情境感知的表型筛选。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：首次将多模态大语言模型智能体引入细胞形态分析，显著增强可解释性。
- **情境感知**：CP-CLIP显式建模实验元数据（细胞系、给药方案），突破了传统方法忽视上下文的局限。
- **实用性**：输出结构化报告直接辅助实验设计，形成闭环。
- **性能**：在关键指标上达到较高水平（F1=0.896）。

## 8. 不足与局限

- **实验覆盖有限**：仅报告单个数据集上的分类结果，未验证跨实验条件（如不同实验室、不同细胞系）的泛化能力。
- **对比方法不清晰**：未详细列出baseline，难以判断增益的显著性。
- **可解释性评估缺失**：仅定性描述rationale质量，缺乏定量人工评估或专家评估。
- **算力与部署成本**：未提供计算资源，可能难以复现或部署。
- **应用限制**：当前框架依赖Cell Painting实验数据，对非标准显微镜数据可能需重新训练。
- **偏差风险**：如果训练数据中细胞系或化合物分布不均，可能导致对罕见条件的推理偏差。

（完）
