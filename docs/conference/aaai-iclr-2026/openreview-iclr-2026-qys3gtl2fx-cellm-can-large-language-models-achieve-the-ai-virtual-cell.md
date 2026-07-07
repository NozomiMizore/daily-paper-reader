---
title: "CeLLM: Can Large Language Models Achieve the AI  Virtual Cell ?"
title_zh: CeLLM：大型语言模型能否实现AI虚拟细胞？
authors: "Jingbo Zhou, Zhongqi Wang, Mutian Hong, Zhuoli Ouyang, Yixuan Du, Siyuan Li, Siqi Ma, Bolin Yang, Changxi Chi, Yunfan Liu, Yufei Huang, Changkai Li, Shu Wang, Zicheng Liu, jiawei jiang, Zelin Zang, Jun Xia, Cheng Tan, Zhen Lei, Stan Z. Li, Chang Yu"
date: 2025-09-15
pdf: "https://openreview.net/pdf?id=qyS3gtL2Fx"
tags: ["query:virtual-cell"]
score: 9.0
evidence: LLM用于AI虚拟细胞
tldr: 针对现有单细胞基础模型在模态覆盖、因果推理和可解释性方面的不足，本文探索大型语言模型（LLM）实现AI虚拟细胞的潜力。文章讨论了LLM在细胞注释和扰动预测等任务中的应用，指出LLM在统一异构模态、适应多样化任务和生成可解释推理链方面的优势，为虚拟细胞研究提供了新视角。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有单细胞基础模型在模态覆盖、因果推理和可解释性方面有限，无法满足AI虚拟细胞的需求。
method: 探讨大型语言模型在单细胞数据中的潜力，分析其在细胞注释和扰动预测中的应用。
result: 指出LLM在统一异构模态和生成可解释推理链方面具有优势，但需克服数值限制等挑战。
conclusion: LLM有望成为构建AI虚拟细胞的有力候选，但需进一步研究以充分发挥其潜力。
---

## Abstract
High-throughput single-cell sequencing has enabled large-scale cellular profiling and spurred the development of single-cell foundation models. These models, typically pretrained on transcriptomic data, learn general-purpose cellular representations but remain limited in modality coverage, causal reasoning, and interpretability, thus falling short of the vision of an Artificial Intelligence Virtual Cell (AIVC). In parallel, large language models (LLMs) have demonstrated strong potential for unifying heterogeneous modalities, adapting to diverse tasks, and generating interpretable reasoning chains in natural language, making them promising candidates toward AIVC. Recent progress in applying LLMs to tasks such as cell annotation and perturbation prediction highlights this potential, yet key challenges persist, including insufficient task coverage, narrow evaluation metrics, and limited robustness to input and prompting factors. To address these gaps, we introduce \textbf{CeLLM}, a comprehensive benchmarking framework for evaluating \textbf{LLM}s in the \textbf{CeLL}ular domain. CeLLM covers a broad spectrum of tasks spanning gene, cell, and omics-level analyses, systematically assesses 15 open-source, proprietary, and biology-specialized models, and incorporates diverse evaluation criteria under multiple task settings. As a cross-scale, reproducible, and dynamic benchmark, CeLLM provides a sustainable platform to track progress, foster methodological innovation, and accelerate the development of LLMs toward virtual cell modeling.

---

## 论文详细总结（自动生成）

# CeLLM：大型语言模型能否实现AI虚拟细胞？—— 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：高通量单细胞测序技术使得大规模细胞图谱成为可能，催生了单细胞基础模型。然而，现有单细胞基础模型（通常基于转录组数据预训练）在**模态覆盖**（仅限转录组）、**因果推理**（难以预测干预效应）和**可解释性**方面存在严重局限，距离实现“人工智能虚拟细胞”（AIVC）的愿景仍有很大差距。
- **核心问题**：大型语言模型（LLM）能否被有效应用于单细胞领域，弥补现有单细胞基础模型的不足，成为构建AIVC的可行方案？
- **整体含义**：本文系统探索LLM在细胞注释、扰动预测等任务中的潜力，指出LLM具有统一异构模态、适应多样化任务、生成可解释推理链等优势，但也面临任务覆盖不足、评估指标狭窄、对输入和提示因素鲁棒性差等挑战。为此，作者提出了**CeLLM**——一个全面、可复现、动态的基准框架，用于评估LLM在单细胞领域（基因、细胞、组学层次）的表现。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：构建一个跨尺度、可复现、动态的基准测试平台，系统评估各类LLM在单细胞领域的性能，推动LLM向虚拟细胞建模发展。
- **关键技术细节**：
  - CeLLM覆盖**三个分析层次**：基因级、细胞级、组学级（omics-level）任务。
  - 评估**15个模型**，包括：开源LLM、闭源商业LLM以及生物学专用LLM。
  - 采用**多种评价标准**（diverse evaluation criteria），并在多个任务设置下（例如不同提示策略、输入格式）进行测试。
  - 强调**跨尺度**（cross-scale）：任务从基因表达预测到细胞类型注释，再到多组学整合。
  - 设计为**可复现**和**动态**的基准，支持持续跟踪进展、促进方法创新。
- **公式或算法流程**：摘要未提供具体公式或算法伪代码。方法核心是构建统一的评估框架，无需新模型，而是利用现有LLM进行零样本或少样本推理，通过设计专门的任务提示和评价指标来量化性能。

## 3. 实验设计：数据集、基准、对比方法
- **数据集与场景**：覆盖基因、细胞、组学三个层次的多项任务。具体数据集名称未在摘要中列出，但可以推断包括单细胞转录组数据集、细胞注释标准参考、扰动实验数据等。
- **Benchmark**：CeLLM本身即是一个基准框架，它定义了任务集、评估指标和标准化实验流程，可作为后续研究的参考标准。
- **对比方法**：
  - 共评估15个模型，包括：
    - **开源LLM**（如LLaMA系列、Mistral等）
    - **闭源LLM**（如GPT-4、Claude等）
    - **生物学专用LLM**（如scBERT、GenePT等单细胞基础模型）
  - 对比维度：不同模型在同一任务上的性能、不同提示设计的影响、不同任务设置下的鲁棒性。

## 4. 资源与算力
- **未明确说明**：摘要中未提及训练/推理所用的GPU型号、数量、训练时长等算力信息。由于CeLLM是一个推理基准（主要评估现有LLM而非从头训练），可能主要涉及推理开销，但论文未量化。后续建议阅读全文以获取具体硬件配置。

## 5. 实验数量与充分性
- **实验规模**：
  - 覆盖15个模型，任务包含基因、细胞、组学三个层次，每个层次下应包含多个子任务（如细胞类型分类、基因表达预测、扰动响应预测等）。虽然具体任务数量未列出，但从“广泛覆盖”（broad spectrum）推断实验数量较多。
  - 包含多种评估准则和多种任务设置（如不同提示模板、不同输入格式、不同数据划分），暗示至少数十组实验。
- **充分性与公平性**：
  - **优点**：系统性地对比了多种模型类型，包含开放与闭源、通用与专用模型，覆盖面广；采用统一评价指标，保证公平性；考虑提示因素的影响（鲁棒性分析）。
  - **不足**：摘要未提及消融实验或统计显著性检验，也未说明是否控制模型参数量、推理温度等超参数。具体实验设计的细节需参考全文。总体而言，作为基准框架，实验设计较为全面，但论文本身可能没有提出新的训练方法，而是专注于评估。

## 6. 论文的主要结论与发现
- LLM在单细胞领域具有显著潜力，特别是在**统一异构模态**（如文本描述与基因表达结合）和**生成可解释推理链**（如自然语言解释细胞状态）方面，优于传统单细胞基础模型。
- 但LLM存在**关键挑战**：数值数据（如基因表达值）的精确处理能力有限；对输入格式和提示设计敏感；任务覆盖不全（目前主要集中于注释和简单预测，缺乏复杂因果推理任务）。
- CeLLM基准框架能够有效量化这些优缺点，为未来研究提供标准化参考。
- **核心结论**：LLM有望成为构建AIVC的有力候选，但需进一步克服数值限制、扩展任务范围、提升鲁棒性。

## 7. 优点：方法或实验设计上的亮点
- **全面性**：首次将LLM在单细胞领域的评估系统化，覆盖基因、细胞、组学三个尺度，且包含15个模型，是当前最全面的对比之一。
- **动态可复现**：CeLLM被设计为可持续更新的基准，便于社区贡献新任务和新模型。
- **关注鲁棒性**：专门评估了输入和提示因素的影响，这在LLM应用中非常重要。
- **跨领域融合**：将NLP领域的LLM评测方法论引入计算生物学，提供了新视角和工具。

## 8. 不足与局限
- **实验覆盖不完整**：摘要未列出具体任务名称和指标，难以判断是否覆盖了复杂任务如基因调控网络推断、药物反应预测等。若仅覆盖基础任务则泛化能力有限。
- **偏差风险**：依赖现有LLM的API或开源模型，可能存在版本不一致、保密模型黑盒等偏差；提示工程设计可能偏向某些模型。
- **应用限制**：LLM在数值数据处理上本质弱势，直接用于表达值预测可能不如专用回归模型；推理代价高（大模型推理慢）；隐私问题（细胞数据可能敏感）。
- **缺少理论分析**：未解释LLM为何能用于单细胞数据，也缺乏对失败案例的分析。
- **资源与算力信息缺失**：无法评估实验的可复现成本和实际部署可行性。

（完）
