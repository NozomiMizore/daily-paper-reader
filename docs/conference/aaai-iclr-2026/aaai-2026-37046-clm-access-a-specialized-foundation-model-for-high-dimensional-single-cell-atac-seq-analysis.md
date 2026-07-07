---
title: "CLM-Access: A Specialized Foundation Model for High-Dimensional Single-Cell ATAC-Seq Analysis"
title_zh: CLM-Access：针对高维单细胞ATAC-seq分析的专用基础模型
authors: "Ziqiang Liu, Bowen Li, Zhenyu Xu, Yantao Li, Junwei Zhang, Chulin Sha, Xiaolin Li"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37046/41008"
tags: ["query:virtual-cell"]
score: 5.0
evidence: 单细胞数据基础模型，与虚拟细胞相关
tldr: 针对单细胞ATAC-seq缺乏基础模型的问题，提出CLM-Access，借鉴细胞语言模型范式，学习染色质可及性的细胞表示，为下游分析提供通用表征，扩展了虚拟细胞模型的覆盖范围。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37046/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1505, \"height\": 822, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37046/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1806, \"height\": 942, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37046/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 755, \"height\": 477, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37046/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 829, \"height\": 235, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37046/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 852, \"height\": 311, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37046/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 800, \"height\": 235, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37046/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 850, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37046/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 820, \"height\": 304, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37046/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 760, \"height\": 192, \"label\": \"Table\"}]"
motivation: 现有细胞语言模型仅针对scRNA-seq，缺乏表观遗传模态。
method: 设计专门处理scATAC-seq数据特征的细胞语言模型架构。
result: 在多个下游任务中取得优异性能。
conclusion: 填补了单细胞表观遗传基础模型的空白。
---

## Abstract
Inspired by the success of large language models (LLMs) in natural language processing, cell language models (CLMs) have emerged as a promising paradigm to learn cell representations from high-dimensional single-cell data—particularly transcriptomic profiles from scRNA-seq. These foundation models have shown remarkable potential across a variety of downstream applications. However, there remains a lack of foundation models for scATAC-seq data, which measures chromatin accessibility at single-cell level and is critical for decoding epigenetic regulation. Developing such model is considerably more challenging due to the unique characteristics of scATAC-seq data, including the vast number of chromatin regions, lack of standardized annotations, extreme sparsity, and near-binary distributions. To address these challenges, we systematically explore various strategies and propose CLM-Access, a specialized foundation model for scATAC-seq data. CLM-Access incorporates three main innovations: (1) an unified data processing pipeline that maps 2.8 million cells onto an unified reference of over 1 million chromatin regions; (2) a specialized patching and embedding strategy to effectively manage high-dimensional inputs; and (3) a tailored masking and loss function design that preserves fine-grained regional information while enhancing training efficiency and representation quality. With comprehensive benchmarks, we show that CLM-Access significantly outperforms existing methods in key downstream tasks, including batch effect correction, cell type annotation, RNA expression prediction, and multi-modal integration. This work establishes a scalable and interpretable foundation model for single-cell epigenomic analysis and expands the application of CLMs in single-cell research.

---

## 论文详细总结（自动生成）

# 论文总结：CLM-Access: A Specialized Foundation Model for High-Dimensional Single-Cell ATAC-Seq Analysis

## 1. 论文的核心问题与整体含义

- **研究动机**：单细胞ATAC-seq（scATAC-seq）是测量染色质可及性的技术，对解码表观遗传调控至关重要。但现有细胞语言模型（如Geneformer、scGPT、scBERT）均针对scRNA-seq数据设计，缺乏专门为scATAC-seq数据构建的基础模型。
- **主要挑战**：scATAC-seq数据具有特征维度极高（候选顺式调控元件cCREs达10⁵~10⁶）、缺乏标准化注释、极度稀疏、信号近乎二值（开放/不开放）等特点，直接迁移转录组模型不可行。
- **整体目标**：提出第一个专门针对scATAC-seq数据的细胞语言基础模型CLM-Access，实现高维稀疏数据的高效表示学习，并在多个下游任务中超越现有方法。

## 2. 论文提出的方法论

### 核心思想
- 采用BERT风格Transformer架构进行自监督预训练，通过掩码重建学习染色质可及性的全局模式。
- 针对高维特征：将上百万个cCREs划分为固定大小的patch（区域块），每个patch作为一个token，同时保留每个peak的信号信息。

### 关键技术细节
1. **数据预处理与tokenization**：
   - 构建统一参考基因组上的cCRE集（约115万），将2.8M细胞映射为该参考。
   - 按染色体位置排序所有cCREs，然后划分为1998个patch（每个patch≈575个cCREs），加上[CLS]、[mask]、[pad]、[eoc]四个特殊token，形成长度为1998+1=1999的序列。
   - 对每个patch内的peak值进行长度标准化（固定长度L），不足时padding，并对所有peak值做二值化（0/1）处理。

2. **模型架构**：
   - **嵌入模块**：包含patch token嵌入层和peak value嵌入层，两者通过元素相加得到最终嵌入（维度256）。
     - \( E_i = \text{emb\_layer\_patch}(C_i) + \text{emb\_layer\_peak}(P_i) \)
   - **Transformer编码器**：8层，每层8头注意力，隐藏维度256，参数约12M。采用Flash Attention v2加速。
   - **Peak解码器**：单层全连接网络，将Transformer输出（特别是[CLS] token和各个patch的表示）映射到所有掩码peak的值。

3. **预训练任务与损失函数**：
   - 仅对peak value进行掩码（而非同时掩码patch token和peak value），使用二进制交叉熵（BCE）损失在peak级别优化。
   - 设计动机：联合掩码增加复杂度且不利于学习局部特征，peak-level BCE优于patch-level MSE/BCE。

## 3. 实验设计

### 数据集与场景
- **预训练数据**：自建Human-scATAC数据库，包含约2.8M单细胞（通过统一流程处理得到115万cCREs）。消融实验中使用了0.33M（scCLIP处理）、1.3M（CATlas）、2.8M三个规模。
- **下游任务**：
  - **批次效应校正**：4个PBMC scATAC-seq数据集（来自Hu et al. 2024）。
  - **细胞类型注释**：两个大型数据集GSE219281和GSE181346（各约7万细胞）。
  - **RNA表达预测**：配对的scRNA-seq和scATAC-seq数据（来自Hu et al. 2024）。
  - **多模态整合**：相同配对数据。

### Benchmark与对比方法
- **批次效应校正**：PCA、Harmony（Korsunsky et al. 2019）
- **细胞类型注释**：scATAnno（Jiang et al. 2024）、Cellcano（Ma, Lu, Wu 2023）
- **RNA表达预测**：BABEL（Wu et al. 2021）、MultiVI（Ashuach et al. 2023）
- **多模态整合**：MultiVI、MIRA（Lynch et al. 2022）、Proust（Wang, Wang, Li 2023）、scTotalVI（Lotfollahi et al. 2022）

### 评估指标
- 批次效应校正：可视化（UMAP）比较（定性）。
- 细胞类型注释：Accuracy、Precision、Recall、Micro F1。
- RNA表达预测：Pearson相关系数、RMSE。
- 多模态整合：可视化定性（UMAP图展示模态对齐）。

## 4. 资源与算力

- **文中明确提到**：使用Flash Attention v2框架实现Transformer，模型参数约12M，训练15个epoch（batch size=8）。
- **未明确说明**：实验所使用GPU型号、数量、训练总时长。因此无法量化具体算力消耗。论文没有提供训练时间或硬件信息。

## 5. 实验数量与充分性

- **数量丰富**：
  - 预训练超参数探索（二值化 vs 非二值化、patch大小1k/2k/5k/TAD、损失函数patch-level MSE/BCE vs peak-level BCE、掩码形式联合 vs 仅掩码value）。
  - 模型和数据规模消融（小/中/大模型；0.33M/1.3M/2.8M数据）。
  - 4个下游任务，每个任务至少对比2~4个基线方法。
  - 每个任务使用公开标准数据集。
- **充分性与客观性**：
  - 消融实验全面，针对核心设计（二值化、损失函数、掩码形式、patch大小）均做了控制变量。
  - 对比方法均为领域内代表性方法，评估指标客观（ARI、NMI、Accuracy等）。
  - 多个数据集验证，避免单数据集偏差。
  - 整体实验设计合理，结论可信度高。

## 6. 论文的主要结论与发现

- CLM-Access在批次效应校正、细胞类型注释、RNA表达预测、多模态整合四个任务中均显著优于现有方法（如RNA表达预测Pearson 0.9175，高于BABEL的0.9101和MultiVI的0.8845）。
- 关键设计选择：
  - **二值化处理**可降低学习复杂性，提升性能。
  - **peak-level BCE损失**优于patch-level MSE/BCE。
  - **仅掩码peak value**优于联合掩码patch token和value。
  - **中等模型参数**（12M）性能最佳，更大模型因数据量限制出现过拟合。
  - **增加预训练数据规模**（从0.33M到2.8M）持续提升下游性能，近似线性关系。

## 7. 优点

- **首创性**：首个专门为scATAC-seq数据设计的基础模型，填补了表观遗传模态细胞语言模型的空白。
- **创新处理方法**：patch tokenization策略巧妙解决高维稀疏问题，既保留全部cCRE信息又控制输入长度；peak-level BCE损失适合二值数据。
- **统一数据处理管道**：构建280万细胞-115万cCRE的统一参考，便于跨数据集预训练。
- **强泛化能力**：在多个下游任务上零样本或微调后均超越专用模型，展示了基础模型的通用性。
- **开源代码**：提供GitHub仓库，促进复现和应用。
- **实验严谨**：消融实验覆盖所有关键设计维度，对比方法全面，数据规模大。

## 8. 不足与局限

- **物种限制**：仅使用人类细胞数据，未探索跨物种泛化能力（作者在讨论中已指出）。
- **模型规模与数据规模的平衡**：发现中等模型最优，但未深入分析更大数据+更大模型的潜力，可能受限于当前数据量（2.8M）。
- **资源消耗未公开**：缺少GPU型号、训练时间、峰值内存等算力信息，不利于其他研究者评估可复现性。
- **下游任务覆盖不完整**：仅评估了四个任务，其他重要应用如基因调控网络推断、扰动预测、顺式元件注释等未涉及。
- **潜在数据偏差**：预训练数据来源和构建细节在补充材料中，但正文未明确讨论可能的数据来源偏差（如组织类型、测序平台等）。
- **对比方法选择**：部分对比方法（如Harmony、PCA）为通用降维方法而非专门为scATAC-seq设计，可能略有不公平，但主要对比了领域内最新的深度学习模型。
- **多模态整合评估**：主要依靠UMAP可视化定性比较，缺少定量指标（如LISI、ASW等），说服力有所降低。

（完）
