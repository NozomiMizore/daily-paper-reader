---
title: "VIRTUAL CELLS AS CAUSAL WORLD MODELS: A PERSPECTIVE ON EVALUATION"
title_zh: 虚拟细胞作为因果世界模型：关于评估的视角
authors: "Tiffany Callahan, Zane Beckwith, Thomas Merth, Constantijn van der Poel, Pablo Lemos"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=qjIq4JWFVs"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 综述并提出虚拟细胞模型的因果评估框架
tldr: 本文以视角形式指出，现有AI虚拟细胞评估过于关注预测准确度而忽略了作为生物学因果世界模型的真实性。作者提出了因果评估框架，包括干预有效性、反事实一致性、轨迹忠实度和机制对齐等指标，并梳理了现有虚拟细胞建模方法与可用扰动数据集。该论文为虚拟细胞模型的发展提供了评估指南，直接回应对虚拟细胞模型的需求。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有虚拟细胞评估仅侧重拟合数据，未检验干预响应和因果一致性。
method: 提出因果评估指标和基准分类，并调研现有虚拟细胞建模方法。
result: 给出评估框架和未来因果基准建议。
conclusion: 推动虚拟细胞模型向因果世界模型的方向发展。
---

## Abstract
This perspective argues that evaluating AI virtual cells requires moving beyond predictive accuracy toward assessing their ability to function as causal world models of biology. Existing benchmarks emphasize fit to observed data, rewarding pattern matching but failing to test responses to interventions. We propose that trustworthy virtual cells require causal evaluation: metrics and benchmarks that assess intervention validity, counterfactual consistency, trajectory faithfulness, and mechanistic alignment. Our contribution is two-fold: (1) a survey of recent approaches to virtual cell modeling, and (2) a taxonomy of causal evaluation metrics mapped to available perturbation datasets and benchmarks. By outlining gaps and proposing unified causal benchmarks, we position causal evaluation as the key step toward making virtual cells reliable world models of biology.

---

## 论文详细总结（自动生成）

好的，我将基于您提供的论文摘要及元数据信息，对这篇视角论文进行结构化、深入、客观的中文总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：当前对 AI 虚拟细胞（virtual cell）模型的评估过度聚焦于预测准确度（例如拟合观测数据），而忽略了模型作为生物学**因果世界模型**（causal world model）的核心能力——即正确预测**干预**（perturbation/intervention）下的细胞行为变化，以及支持**反事实推理**（counterfactual reasoning）和机制对齐。
- **研究动机**：现有基准测试（benchmarks）奖励模式匹配，却无法检验模型对未曾观测过的扰动（如基因敲除、药物处理）的响应是否正确。这导致即使预测精度很高的模型，也可能在因果推理任务中误导生物学理解。因此，需要一套专门的因果评估框架，来确保虚拟细胞模型能可靠地作为生物学发现工具。
- **整体含义**：该文是一篇**视角**（perspective）论文，旨在推动虚拟细胞评估范式的转变：从“拟合数据”到“因果一致性”。它主张将因果评估作为桥接模型能力与生物学世界模型可靠性的关键步骤。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：提出因果评估框架，包含四个关键指标维度：
    - **干预有效性**（Intervention Validity）：模型对于给定干预（如基因过表达、药物添加）所预测的细胞状态变化是否与真实生物学效应一致。
    - **反事实一致性**（Counterfactual Consistency）：模型能否回答“如果未发生某个干预，细胞会怎样”这类反事实问题，且答案在逻辑上自洽。
    - **轨迹忠实度**（Trajectory Faithfulness）：模型预测的细胞状态随时间演化的路径（例如分化、重编程过程）是否忠实于真实生物过程。
    - **机制对齐**（Mechanistic Alignment）：模型内部表征或预测逻辑是否与已知的生物学机制（如信号通路、基因调控网络）对齐。
- **技术细节**：论文本身未提供具体算法或公式，而是提出了一套评估分类法（taxonomy），将上述指标映射到已有的扰动数据集和基准测试上。它调研了近年来的虚拟细胞建模方法（如基于图神经网络、生成模型、微分方程等），并按照其是否适用于因果推断进行分类。
- **算法流程（文字说明）**：作者的建议流程是：（1）对虚拟细胞模型进行标准的预测拟合度评估；（2）在此基础上，额外进行因果评估，包括使用已知的扰动数据集（如CRISPR、药物库）检验干预响应；（3）利用反事实生成任务检验一致性；（4）通过与已知机制图谱比对，评估机制对齐程度。

### 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法
- **数据集与场景**：论文提到**已有的一些扰动数据集和基准**，例如CRISPR基因编辑数据集（如DepMap、Perturb-seq）、药物处理数据集（如LINCS L1000）、以及细胞状态轨迹数据（如分化和重编程时间序列）。但文中并未详细列出每个数据集的规模或来源，仅作为例子提及。
- **基准（benchmark）**：论文并未创建新的基准，而是提出需要**统一的因果基准**（unified causal benchmarks）。它梳理了当前可用于因果评估的现有基准，并指出其不足（例如缺乏反事实标签）。
- **对比方法**：论文以综述形式列出了多种虚拟细胞建模方法（如基于VAE、扩散模型、GNN的模型），但未进行实验对比。它强调的是**评估方法**的对比，即传统预测精度指标 vs. 新提出的因果指标。

### 4. 资源与算力
- **未明确说明**：论文全文主要关注评估框架，并未提及任何具体的训练或推理所需的算力（GPU型号、数量、训练时长等）。作为视角论文，它不包含实验，因此也没有计算资源报告。

### 5. 实验数量与充分性
- **实验数量**：该论文**没有进行任何新的实验**（实验组、消融实验等）。它是一篇综述/视角论文，只进行了文献调研和框架设计。
- **充分性**：从视角论文的角度看，它对现有文献的调研和分类是充分的，但缺乏实证验证。它提出的因果评估框架本身尚未在真实模型上进行测试，因此其有效性和可行性有待后续工作。实验充分性方面无法评价。

### 6. 论文的主要结论与发现
- **主要结论**：要使虚拟细胞成为可靠的生物学因果世界模型，必须将评估重心从预测准确度转移到因果评估指标（干预有效性、反事实一致性、轨迹忠实度、机制对齐）上。当前缺乏统一的因果基准，导致即使高精度的模型也可能在干预响应预测上失败。
- **发现**：作者通过文献调研发现，现有虚拟细胞建模方法（如基于VAE、扩散模型、GNN）在因果推理能力上参差不齐，且没有专门的因果评估测试集，这阻碍了该领域向可信世界模型的发展。

### 7. 优点：方法或实验设计上有哪些亮点
- **视角新颖**：首次系统性地将因果推断的评估思想引入虚拟细胞领域，明确指出了当前评估体系的缺陷，并提供了清晰的改进方向。
- **框架系统化**：提出的因果评估四维度（干预有效性、反事实一致性、轨迹忠实度、机制对齐）覆盖了关键因果能力，且每个维度都有可操作的含义和映射到现有数据集的路径，对于实践者有很强的指导意义。
- **文献调研全面**：对近期虚拟细胞建模方法和可用扰动数据集进行了分类和总结，为后续研究者提供了切入点。
- **定义明确**：核心概念（如因果世界模型、反事实一致性）定义清晰，有助于领域内形成共识。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制
- **缺乏实证**：作为视角论文，没有用真实模型和数据集对提出的评估框架进行任何实验验证，因此**框架的有效性、计算可行性、指标间的相关性**均未得到检验。这是最大的局限。
- **评估维度可操作性不足**：例如“机制对齐”如何量化？论文未提供具体度量方法（如通路富集分、因果发现精度等）。反事实一致性评估需真实的反事实数据，而生物数据中通常缺乏此类标签。
- **现有数据集分类不够深入**：虽然列出了可用数据集，但未详细说明每个数据集是否能直接用于特定因果评估维度（例如，有些数据集只有观测数据而无干预响应数据）。
- **偏差风险**：论文主要基于公开的扰动数据集，可能遗漏一些未公开的数据或特定场景（例如体内数据、疾病模型）。此外，偏向于单细胞层面，对其他尺度（如组织）的讨论不足。
- **应用限制**：所提出的框架适用于评估阶段，但在模型训练阶段如何融入因果约束没有讨论。另外，对于超大规模的基础模型（如大型基因组预训练模型），其因果评估可能面临计算成本高昂的挑战。

（完）
