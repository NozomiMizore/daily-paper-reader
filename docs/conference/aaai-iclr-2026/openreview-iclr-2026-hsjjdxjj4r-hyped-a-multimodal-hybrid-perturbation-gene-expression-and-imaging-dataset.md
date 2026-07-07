---
title: "HYPED: A Multimodal HYbrid Perturbation Gene Expression and Imaging Dataset"
title_zh: HYPED：一个多模态混合扰动基因表达与成像数据集
authors: "Ram Prakash Ayyam Perumal, Jillian Cwycyshyn, Nicholas Galioto, Sarah Nicole Golts, Joshua Pickard, Cooper M Stansbury, Lindsey A. Muir, Alvaro Velasquez, Indika Rajapakse"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=HsJJDxjJ4R"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 用于扰动响应预测的多模态基准数据集
tldr: 针对细胞扰动预测实验成本高、缺乏多模态基准的问题，本文生成了HYPED数据集，结合72小时时间序列活细胞成像（荧光细胞周期报告）和长读长单细胞RNA测序数据，捕捉人类成纤维细胞对瞬时转录因子扰动的动态响应。该数据集提供了预处理流程和评估基线，为开发多模态扰动响应预测模型及虚拟细胞研究提供了重要资源。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 缺乏同时包含成像和单细胞RNA-seq的扰动响应基准数据集。
method: 生成人类成纤维细胞在转录因子扰动下的时间序列活细胞成像和scRNA-seq数据。
result: 提供公开的多模态数据集、预处理流程和基线模型评估。
conclusion: 该数据集将推动多模态扰动响应预测模型的开发。
---

## Abstract
Integrating multimodal, high-resolution biological data is a useful way to characterize biological processes, such as how cells respond to perturbations. Cell perturbation prediction is a major experimental challenge and has motivated substantial research in machine learning for biology. In this work, we generated a multimodal benchmark dataset that captures the dynamic response of human fibroblasts to transient transcription factor perturbations. We performed time-series live cell imaging with fluorescent cell cycle reporters over 72 hours and collected long-read single-cell RNA sequencing data from the same population of cells. We release the processed dataset, preprocessing pipelines and benchmarking code along with the evaluation of existing models using our data as ground truth. This work supports the development and evaluation of machine learning methods for modeling dynamical systems from multimodal datasets. HYPED consists of RNA sequencing data from approximately 20,000 cells and 203 imaging timepoints across four experimental conditions, totaling 2030 imaging frames. HYPED makes the cell perturbation problem accessible to machine learning researchers with state-of-the-art experimental data.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：细胞对扰动的动态响应预测是生物学和机器学习领域的重要挑战，但目前缺乏同时包含 **高分辨率活细胞成像** 和 **单细胞RNA测序** 的多模态基准数据集，限制了多模态扰动响应预测模型的发展。
- **背景**：整合多模态、高分辨率生物学数据可有效表征生物过程（如细胞对扰动的响应），但现有扰动实验成本高、数据单一。HYPED数据集填补这一空白，为“虚拟细胞”等研究提供关键资源。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：通过同步采集 **时间序列活细胞成像**（荧光细胞周期报告蛋白）和 **长读长单细胞RNA测序**（scRNA-seq），构建人类成纤维细胞对瞬时转录因子扰动的动态响应多模态数据集。
- **关键技术细节**：
  - **细胞模型**：人类成纤维细胞。
  - **扰动方式**：瞬时转录因子（TF）扰动（具体TF种类未在摘要中说明）。
  - **成像模态**：72小时时间序列活细胞成像，使用荧光细胞周期报告蛋白（如FUCCI体系），共203个成像时间点。
  - **测序模态**：从相同细胞群体中收集长读长单细胞RNA测序数据，覆盖约20,000个细胞。
  - **数据规模**：4种实验条件（含对照），总计2030个成像帧。
- **算法流程**（文字说明）：  
  ① 对培养的成纤维细胞进行转录因子瞬时转染诱导扰动。  
  ② 在72小时内持续拍摄活细胞成像，记录细胞周期状态（荧光标记）。  
  ③ 在成像结束后，对同一群体细胞进行单细胞分离、裂解和长读长scRNA-seq。  
  ④ 对成像数据进行预处理（对齐、分割、轨迹追踪），对scRNA-seq数据进行质控、降维、聚类。  
  ⑤ 整合多模态数据，形成时间-空间-基因表达的对齐基准。
- **公式**：未提及明确数学公式。

## 3. 实验设计：数据集、基准与对比方法

- **使用的数据集**：
  - **HYPED数据集**（自建）：来自人类成纤维细胞，4种实验条件，203个成像时间点，~20,000个细胞scRNA-seq数据，共2030帧图像。
  - 未使用外部公开数据集（原文未提及）。
- **基准（Benchmark）**：
  - 数据集本身作为 **ground truth**，用于评估现有模型的预测性能。
  - 提供了预处理流程和基准测试代码（benchmarking code）。
- **对比方法**：
  - 使用现有模型（未具体列出模型名称）在HYPED数据上进行评估，以HYPED为ground truth验证预测准确性。

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量、训练时长等算力信息。仅提及“提供了预处理流程和基准测试代码”，但未描述训练模型所需的计算资源。

## 5. 实验数量与充分性

- **实验数量**：共4种实验条件（包括对照），成像时间点203个，细胞数约20,000。实验组数量有限，但覆盖了不同转录因子扰动。
- **充分性评估**：
  - **充分**：提供了多模态时间序列数据，可支撑动态建模和多模态融合研究。
  - **局限性**：仅使用一种细胞类型（人类成纤维细胞）、一种扰动类型（瞬时转录因子），未在其他细胞系或扰动方式下验证；未进行消融实验（如仅使用成像或仅使用RNA-seq的对比）。实验设计集中于数据生成而非模型消融，因此作为基准数据集是充分的，但作为方法验证的充分性需依赖后续工作。

## 6. 主要结论与发现

- 成功生成了第一个结合 **时间序列活细胞成像** 和 **长读长单细胞RNA-seq** 的多模态扰动响应基准数据集。
- 该数据集使机器学习研究者能够利用 **最先进的实验数据** 解决细胞扰动预测问题，推动了多模态动力学系统建模方法的发展。
- 提供了完整的预处理流程和基准代码，便于社区复现和扩展。

## 7. 优点：方法或实验设计亮点

- **多模态同步采集**：在同一细胞群体上同时获取成像和转录组数据，避免了批次效应，实现了跨模态直接对齐。
- **时间分辨率高**：72小时连续成像，203个时间点，可捕捉细胞周期和扰动动态响应。
- **长读长测序**：利用长读长scRNA-seq，能捕获全长转录本，提供更丰富的基因表达信息。
- **公开与可复现**：开放处理后的数据、预处理pipeline和基准代码，降低机器学习研究者使用门槛。
- **针对“虚拟细胞”需求**：直接回应了ICLR-2026虚拟细胞主题，具有较强的领域关联性。

## 8. 不足与局限

- **细胞类型单一**：仅使用人类成纤维细胞，无法代表其他组织或疾病模型。
- **扰动类型有限**：仅使用瞬时转录因子扰动，未涉及药物、基因编辑、环境应激等常见扰动。
- **成像标记局限**：仅使用细胞周期报告蛋白，未纳入其他亚细胞结构或蛋白标记。
- **缺乏跨模态验证**：未提供成像与RNA-seq数据在单细胞水平上的严格配准（如通过细胞条形码技术），存在配对模糊性。
- **未提供基线模型性能**：论文仅提及“评估现有模型”，但未报告具体性能指标，无法判断数据集的难度和基线。
- **未报告算力需求**：缺少对后续建模计算资源的参考。
- **潜在偏差**：长读长测序可能引入技术偏差，活细胞成像的光毒性可能影响细胞行为。

（完）
