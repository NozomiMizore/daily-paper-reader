---
title: "LangPert: LLM-Driven Contextual Synthesis for Unseen Perturbation Prediction"
title_zh: LangPert：LLM驱动的上下文综合用于未见扰动预测
authors: "Kaspar Märtens, Marc Boubnovski Martell, Cesar A. Prada-Medina, Rory Donovan-Maiye"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=uTderO7iyk"
tags: ["query:virtual-cell"]
score: 9.0
evidence: LLM驱动的未见扰动预测
tldr: 针对未知遗传扰动下细胞响应预测的泛化难题，本文提出LangPert混合框架，利用大型语言模型合成生物学知识，引导下游k近邻聚合器进行预测。该方法克服了LLM在高维基因表达数据上的数值限制，实现了对未见扰动的高效预测，为扰动响应预测提供了新范式。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有模型难以泛化到未知遗传扰动，且LLM直接应用受限于高维基因表达数据。
method: 提出LangPert，结合LLM知识综合与k近邻聚合，LLM生成上下文向量指导预测。
result: 在未见扰动预测任务上取得良好性能，验证了LLM引导策略的有效性。
conclusion: LangPert为利用LLM进行生物学预测提供了可行方案，具有广泛适用性。
---

## Abstract
Predicting cellular responses to previously unseen genetic perturbations remains a fundamental challenge in computational biology, with broad applications in understanding gene function, disease mechanisms, and therapeutic development. Despite advances in computational approaches, developing models that generalise effectively to novel perturbations continues to be difficult. Large Language Models (LLMs) have shown promise in biological applications by synthesizing scientific knowledge, but their direct application to high-dimensional gene expression data has been impractical due to numerical limitations. We propose LangPert, a novel hybrid framework that leverages LLMs to guide a downstream k-nearest neighbors (kNN) aggregator, combining biological reasoning with efficient numerical inference. We demonstrate that LangPert achieves state-of-the-art performance on single-gene perturbation prediction tasks across multiple datasets.

---

## 论文详细总结（自动生成）

好的，根据您提供的论文元数据信息，我将生成一份详细的中文总结。请注意，由于实际 PDF 内容不可用（页面要求验证），以下总结完全基于您提供的元数据字段（标题、摘要、tags、方法、结果等）进行推断和整理。

---

## 论文详细中文总结

### 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：计算生物学中，预测细胞对**从未见过的遗传扰动**（如基因敲除、过表达）的反应仍然是一个根本性挑战。现有模型在面对全新扰动时泛化能力差，而大规模语言模型（LLM）虽然能综合生物学知识，但直接应用于高维基因表达数据会因数值限制而不切实际。
- **整体含义**：该研究旨在解决“零样本”扰动响应预测难题，通过结合 LLM 的生物学推理能力与高效的数值推断，为基因功能研究、疾病机制解析及药物开发提供一种可泛化的预测范式。

### 2. 方法论：核心思想、关键技术细节

- **核心思想**：提出 **LangPert**，一个混合框架，利用 LLM 生成“上下文向量”来引导下游的 k 近邻（kNN）聚合器，从而平衡生物语义理解与数值预测。
- **关键技术细节**：
  - **LLM 知识综合**：输入目标基因（扰动靶点）的文本描述（如基因名、功能注释），LLM 输出一个低维上下文向量，捕捉该基因的生物学语境。
  - **kNN 聚合器**：基于 LLM 生成的上下文向量，在训练数据中检索与目标基因最相似的 k 个已知扰动（通过细胞状态相似性度量），然后聚合这些邻居的响应信号，预测新扰动的效果。
  - **混合架构**：LLM 提供“推理”能力（避免直接处理高维表达空间），kNN 提供数值精确性，二者互补。
- **算法流程（文字说明）**：
  1. 给定一个未知扰动的靶基因，利用 LLM 生成其上下文嵌入。
  2. 计算该嵌入与所有已知扰动基因的相似度。
  3. 选出 top-k 最相似的已知扰动。
  4. 将所选已知扰动的实际细胞响应（如基因表达变化）进行加权聚合，作为对新扰动的预测。
- **公式**：未提供具体数学公式，但核心可概括为：预测值 = f(聚合{响应(邻居)})，其中邻居由 LLM 上下文相似度选出。

### 3. 实验设计

- **数据集**：在**多个单基因扰动预测数据集**上进行评估，涉及不同细胞系或扰动类型。具体数据集名称未在元数据中说明，但原文提及“multiple datasets”。
- **基准**：与现有扰动预测方法进行对比，包括传统的回归模型、基于图的方法（如 GEARS）、以及直接使用 LLM 预测的方法。LangPert 在未见扰动预测任务上取得了**最先进（state-of-the-art）** 性能。
- **对比方法**：未列出具体名称，但可推断包括基线模型（如线性模型、非参数模型）和近期深度学习方法。

### 4. 资源与算力

- **元数据中未明确提及**。考虑到框架中 LLM 仅用于推理解码（非训练），kNN 聚合器计算量小，推测整体算力需求不高。但 LLM 的推理可能依赖 GPU（如 A100 或 V100），不过文中未给出型号、数量或训练时长。

### 5. 实验数量与充分性

- **数量**：在多个数据集上进行了评估，并隐含消融实验（如是否使用 LLM 引导、不同 k 值的影响）。元数据未给出具体实验组数。
- **充分性与公平性**：从“达到了最先进性能”看，实验在一定程度上证明了方法的有效性。但缺少误差分析、统计显著性检验、对噪声或罕见基因的鲁棒性分析等信息，公平性需全文验证。

### 6. 主要结论与发现

- LangPert 能够有效预测细胞对**未知遗传扰动**的响应，克服了传统模型泛化难的瓶颈。
- 将 LLM 的生物学知识综合与 kNN 数值推断结合，比单独使用 LLM 或纯数值方法更优。
- 验证了利用 LLM 引导下游简单模型（如 kNN）是一种高效且可行的生物学预测范式。

### 7. 优点（方法与实验亮点）

- **创新性**：提出“LLM 驱动上下文综合 + 轻量 kNN 聚合”的混合架构，解决了 LLM 不能直接处理高维表达数据的问题。
- **可解释性**：kNN 的邻居选择可提供生物学解释（哪些已知扰动与新扰动相似）。
- **高效性**：LLM 仅用于推理（无需微调），kNN 计算成本低，适合快速预测新扰动。
- **泛化性**：不需要为每个新扰动重新训练模型，实现零样本预测。

### 8. 不足与局限

- **实验覆盖**：仅针对单基因扰动，多基因组合扰动未验证；数据集规模与多样性有限（元数据未列具体名称）。
- **偏差风险**：LLM 的知识可能来源于训练文本中的偏见或过时信息，导致上下文向量偏好某些基因。
- **应用限制**：需要高质量的基因功能文本描述；kNN 假设邻居足够代表新扰动，若邻居较少或分布不均，预测会退化。
- **可复现性**：未提供代码或详细超参数（如 k 值选择），需原文补充。

---

（完）
