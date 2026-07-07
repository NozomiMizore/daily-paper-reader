---
title: "GREmLN: A Cellular Graph Structure Aware Transcriptomics Foundation Model"
title_zh: GREmLN：一种细胞图结构感知的转录组学基础模型
authors: "Mingxuan Zhang, Vinay S Swamy, Léo Dupire, Rowan Cassius, Charilaos I. Kanatsoulis, Evan Paull, Mohammed AlQuraishi, Theofanis Karaletsos, Andrea Califano"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=HdvI8bkdDG"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 图结构转录组学基础模型
tldr: 单细胞RNA数据缺乏自然顺序，语言模型难以直接应用。本文提出GREmLN，一种基于图结构（基因调控网络）的大规模模型，有效编码非局部基因依赖关系和潜在因果关系。该模型可作为虚拟细胞的基础组件，支持下游任务如扰动响应预测。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 单细胞转录组数据无序，需更有效的结构感知模型。
method: 构建基于基因调控网络的图嵌入大模型GREmLN，利用图结构编码基因依赖关系。
result: GREmLN在多个单细胞任务上表现优异，展示了图结构在代表学习中的优势。
conclusion: 为单细胞基础建模提供了图感知新方法，有望支持虚拟细胞中的因果推理。
---

## Abstract
The ever-increasing availability of large-scale single-cell profiles presents an opportunity to develop foundation models to capture cell properties and behavior. However, standard language models such as transformers benefits from sequentially structured data with well defined absolute or relative positional relationships, while single cell RNA data have orderless gene features. Molecular-interaction graphs, such as gene regulatory networks (GRN) or protein-protein interaction (PPI) networks, offer graph structure-based models that effectively encode both non-local gene token dependencies, as well as potential causal relationships. We introduce GREmLN (\textbf{G}ene \textbf{R}egulatory \textbf{Em}bedding-based \textbf{L}arge \textbf{N}eural model), a foundation model that leverages graph signal processing to embed gene token graph structure directly within its attention mechanism, producing biologically informed single cell specific gene embeddings. Our model faithfully captures transcriptomics landscapes and achieves superior performance relative to state-of-the-art baselines on cell type annotation, graph structure understanding, and fine-tuned reverse perturbation prediction tasks. It offers a unified and interpretable framework for learning high-capacity foundational representations that capture complex, long-range regulatory dependencies from high-dimensional single-cell transcriptomic data. Moreover, the incorporation of graph-structured inductive biases enables more parameter-efficient architectures and accelerates training convergence.

---

## 论文详细总结（自动生成）

好的，基于所提供论文的元数据及摘要信息，以下是对该论文的详细中文总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：大规模单细胞转录组数据不断涌现，为构建基础模型以捕捉细胞特性与行为提供了机遇。然而，标准语言模型（如Transformer）依赖于具有明确绝对或相对位置关系的顺序结构数据，而单细胞RNA数据中的基因特征是**无序的（orderless）**，这使得语言模型难以直接应用。
- **研究动机**：分子相互作用图（如基因调控网络 GRN 或蛋白质-蛋白质相互作用网络 PPI）提供了基于图结构的方法，这类方法可以有效编码**非局部基因 token 依赖关系**以及**潜在的因果关系**。
- **整体含义**：该工作旨在引入图结构感知机制，构建一个能够从高维单细胞转录组数据中学习复杂、长程调控依赖关系的基础模型，作为“虚拟细胞”研究的基础组件，支持扰动响应预测等下游因果推理任务。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：提出 **GREmLN（Gene Regulatory Embedding-based Large Neural model）**，一种利用图信号处理技术将基因 token 的图结构直接嵌入到注意力机制中的基础模型，从而生成生物学信息驱动的、细胞特异性的基因嵌入。
- **关键技术细节**：
  - 以**基因调控网络（GRN）** 作为先验图结构，构建基因之间的依赖关系。
  - 模型通过**图信号处理**方法，在注意力机制中引入图结构信息，使自注意力能够感知基因间的拓扑关系和非局部依赖。
  - 这是一种**统一且可解释**的框架，能够学习高容量的基础表示，同时保持较低参数数量（参数高效）并加速训练收敛。
- **算法流程（文字说明）**：
  1. 输入：单细胞转录组数据（基因表达矩阵）及对应的基因调控网络。
  2. 将每个基因视为一个 token，通过图信号处理将其在图中的位置和邻域信息编码为嵌入向量。
  3. 在 Transformer 的注意力计算中，融合图嵌入的偏置或掩码，使得 token 间的交互受到图结构约束。
  4. 经过预训练后，模型输出细胞特异性的基因表示，可用于下游任务微调。

### 3. 实验设计：数据集、benchmark 与对比方法
- **使用数据集 / 场景**：文中未明确列出具体数据集名称，但实验覆盖了多种单细胞分析任务，包括：
  - 细胞类型注释（cell type annotation）
  - 图结构理解（graph structure understanding）
  - 微调的反向扰动预测（fine-tuned reverse perturbation prediction）
- **Benchmark**：对比了最先进的基线方法（state-of-the-art baselines），具体方法名称未在元数据中给出。
- **对比方法**：未列举具体对比算法，仅声称 GREmLN 在多个任务上优于 baseline。

### 4. 资源与算力
- **文中未明确说明**使用的 GPU 型号、数量、训练时长等算力资源。仅提及模型具有“参数高效”（parameter-efficient）的特点，且训练收敛更快，但未提供具体计算成本数据。

### 5. 实验数量与充分性
- **实验数量**：从元数据看，主要实验覆盖了三个任务场景（细胞类型注释、图结构理解、反向扰动预测），但未说明每个任务下的子实验数量或消融实验细节。
- **充分性判断**：由于缺乏详细实验表格、具体数据集规模、统计显著性分析等信息，难以全面评估实验的充分性和公平性。该论文被ICLR-2026拒稿（Rejected-Public），可能说明其在实验对比或结果可信度方面存在不足。

### 6. 论文的主要结论与发现
- 模型能够准确捕捉转录组景观，在细胞类型注释、图结构理解和反向扰动预测任务上优于现有最先进基线。
- 图结构归纳偏置的引入使得模型**参数效率更高**、**训练收敛更快**。
- 提供了一个统一且可解释的框架，能够从高维单细胞数据中学习复杂、长程的调控依赖关系，有望支持虚拟细胞中的因果推理。

### 7. 优点
- **创新性**：将图信号处理与Transformer注意力结合，解决了单细胞转录组数据无序的问题，是一种新颖的图结构感知方法。
- **参数高效**：通过引入图结构归纳偏置，而非单纯扩大模型规模，实现了更紧凑的架构和更快的训练收敛。
- **可解释性**：模型基于生物先验的基因调控网络，其注意力机制具备生物学解释潜力。
- **应用前景**：作为虚拟细胞的基础模型组件，能够支持扰动响应预测等下游任务，推动因果建模。

### 8. 不足与局限
- **实验细节匮乏**：元数据中未列出具体数据集、对比方法、性能指标（如准确率、F1等），也未提供消融实验或超参数分析，难以验证方法鲁棒性。
- **资源信息缺失**：未提供任何算力消耗数据，影响对实际部署可行性的评估。
- **被拒稿风险**：该论文被ICLR-2026拒绝，可能意味着在审稿阶段评审人指出了方法论或实验上的重大缺陷，如与现有方法的对比不够全面、创新性不足或结果复现困难。
- **依赖高质量GRN**：模型性能高度依赖基因调控网络的质量，而实际中GRN构建可能存在噪声或不完整，限制了模型在缺乏可靠先验图结构场景下的应用。
- **仅覆盖部分任务**：未在更广泛的单细胞任务（如基因表达预测、药物反应预测等）上验证，通用性有待进一步证实。

（完）
