---
title: Transcriptomics-Morphology Generation Via Treatment Conditioning With Rectified Flow
title_zh: 基于处理条件整流流的转录组-形态学联合生成
authors: "Shourya Verma, Mengbo Wang, Luopin Wang, Mario Sola, Majid Kazemian, Ananth Grama, Nadia Atallah Lanman"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=4pa7JHUl3o"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 联合预测药物扰动下的基因表达和形态
tldr: 针对单模态方法无法充分捕捉药物扰动下转录组与形态变化的复杂依赖的问题，本文提出PertFlow框架，利用整流流模型和多头跨模态注意力机制，将对照细胞状态、药物特征与处理规范融合为共享表示，同时预测基因表达谱和生成细胞形态图像。在相关数据集上的实验表明，该框架能够有效联合建模多模态扰动响应，为虚拟细胞模型和药物筛选提供了有力工具。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有单模态方法无法充分建模药物扰动下转录组与形态变化的复杂依赖关系。
method: 提出PertFlow，通过多模态交叉注意力融合对照数据与药物特征，利用整流流生成形态图像，同时回归RNA-seq。
result: 该框架能够联合预测基因表达和生成形态图像，响应不同药物处理。
conclusion: PertFlow为多模态扰动响应预测提供了统一框架，有助于虚拟细胞建模。
---

## Abstract
Predicting cellular responses to drug perturbations requires capturing complex dependencies between transcriptomic and morphological changes that single-modality approaches cannot adequately model. We introduce \textbf{PertFlow}, a unified framework that jointly predicts gene expression profiles and generates cellular morphology images in response to drug treatments, conditioned on control cellular states. Our method integrates control transcriptomic and imaging data through multi-head cross-modal attention mechanisms, learning a shared latent representation that incorporates drug compound features, background cellular profiles, and treatment specifications. From this unified representation, PertFlow employs a regression head for RNA-seq prediction and rectified flow dynamics for stable morphological image generation, with cross-modal consistency losses ensuring coherent molecular and phenotypic predictions. PertFlow enables accurate predictions from either complete multi-modal inputs or single-modality data alone, demonstrating robust cross-modal learning. Our evaluation on paired RNA-seq and Cell Painting fluorescent imaging datasets demonstrates that PertFlow achieves stronger cross-modal consistency and accurate prediction of drug-induced changes compared to diffusion baselines.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **研究动机**：药物扰动引起的细胞响应涉及转录组（基因表达）和形态学（细胞图像）两个层面的复杂变化，而传统的单模态方法仅能预测其中一个层面，无法捕捉二者之间的相互依赖关系。
- **核心问题**：如何联合建模药物处理下对照细胞状态、药物特征与处理规范，实现对基因表达谱和细胞形态图像的同步预测。
- **背景意义**：为虚拟细胞模型、药物筛选和精准医学提供多模态、统一的计算框架，增强对药物作用机制的理解。

## 2. 方法论：核心思想、关键技术细节与算法流程

- **核心思想**：设计一个统一的生成-回归框架（PertFlow），将对照细胞的转录组数据与形态图像通过多头跨模态注意力机制融合，学习包含药物化合物特征、背景细胞状态和处理规范的共享潜在表示，从而同时预测RNA-seq谱并生成形态图像。
- **关键技术细节**：
  - **多模态输入编码**：分别提取对照RNA-seq特征的嵌入向量和对照细胞图像的卷积特征。
  - **多头跨模态注意力**：在两模态之间进行交叉注意力计算，捕获转录组-形态间的复杂依赖，得到统一共享表示。
  - **药物特征注入**：将药物分子指纹、浓度等处理规范作为条件信息嵌入共享表示。
  - **双分支输出**：
    - 回归头：从共享表示直接预测处理后的RNA-seq表达谱（连续回归）。
    - 生成头：采用**整流流（Rectified Flow）** 动力学，以共享表示为条件，从噪声逐步生成稳定、逼真的细胞形态图像。
  - **跨模态一致性损失**：在训练过程中加入损失项，约束预测的基因表达与生成的图像在潜在空间或语义上保持一致，确保分子与表型预测的协调性。
- **算法流程简述**：
  1. 输入对照RNA-seq、对照细胞图像、药物特征。
  2. 分别编码，经多头跨模态注意力得到融合表示。
  3. 融合表示馈入回归头（预测RNA-seq）和整流流生成器（生成图像）。
  4. 通过跨模态一致性损失联合优化两个任务。

## 3. 实验设计

- **数据集**：配对的**RNA-seq和Cell Painting荧光成像数据集**（未具体说明数据集名称，推测为公开或自建的细胞药物响应数据集）。
- **基准（Benchmark）**：与**扩散模型（Diffusion Baselines）** 进行比较，作为图像生成/联合预测的基线方法。
- **对比方法**：主要包括扩散模型（未列出具体名称），PertFlow与这些基线在跨模态一致性、药物诱导变化的预测准确性上进行对比。
- **评估指标**：原文未详细列出，但从结论可推断涉及图像生成质量（如FID?）、基因表达预测误差（如RMSE?）以及跨模态一致性得分。

## 4. 资源与算力

- **原文未明确说明**使用的GPU型号、数量、训练时长等具体算力信息。
- 仅能推测为深度学习标准资源配置（例如单个或多个高端GPU），但无法量化。

## 5. 实验数量与充分性

- **实验数量**：原文仅概括性地提到“在配对RNA-seq和Cell Painting数据集上评估”，未列出消融实验或不同超参数设置的组数。
- **充分性与客观性**：
  - 仅与扩散基线对比，对比组数有限；未与其他多模态联合模型（如VAE、GAN、多任务学习等）比较，可能不够全面。
  - 好在强调“可从完整多模态或单模态数据准确预测”，隐含着可能进行了输入模态缺失的消融实验，但未详细展开展示。
  - 整体实验设计尚可，但公开细节不足，难以完全判断公平性。

## 6. 主要结论与发现

- PertFlow在跨模态一致性上**显著优于扩散基线**，能更准确地联合预测药物引起的转录组变化和形态变化。
- 学到的共享表示能有效融合两模态信息，即使只有单一模态输入（例如仅RNA-seq或仅图像），也能进行合理预测，体现了鲁棒的跨模态学习能力。
- 整流流生成框架比扩散模型更稳定，适合显微镜图像的生成任务。

## 7. 优点（方法或实验设计亮点）

- **多模态统一框架**：首次（或少见地）将转录组回归与形态图像生成纳入同一条件生成模型，而非分步处理。
- **多头跨模态注意力**：有效对齐不同模态特征空间，捕捉细粒度依赖关系。
- **整流流（Rectified Flow）**：相比扩散模型，采样步骤少、生成路径更直，训练稳定，更适合连续图像生成。
- **跨模态一致性损失**：强制分子与表型预测协调，提升生物学合理性。
- **支持单模态输入推断**：在实际应用中，若仅有一种数据可用，仍能工作，增加了实用性。

## 8. 不足与局限

- **实验覆盖不足**：仅在单一类型的配对数据集上评估，未在不同细胞系、不同药物库或更复杂的扰动（如基因编辑）上验证泛化性。
- **对比基线单一**：仅与扩散基线比较，缺少与其他多模态框架（如VAE、GAN、基于Transformer的多任务模型）的对比。
- **算力与训练细节缺失**：无资源消耗信息，可复现性降低。
- **未分析失败案例**：未讨论何种药物或细胞类型下模型预测效果差，缺乏鲁棒性分析。
- **可能的数据依赖**：需要大规模的配对RNA-seq和Cell Painting数据，数据获取成本高，限制了应用场景。
- **未提及可解释性**：模型内部注意力能否提供生物机制见解未说明。

（完）
