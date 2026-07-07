---
title: Efficient Cell Painting Image Representation Learning via Cross-Well Aligned Masked Siamese Network
title_zh: 基于跨孔对齐掩码孪生网络的高效细胞绘画图像表示学习
authors: "PinJui Huang, Yu-Hsuan Liao, Soo Heon Kim, Noseong Park, Park Jong Bae, Dongmyung Shin"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Ke5QBMEyd6"
tags: ["query:virtual-cell"]
score: 7.0
evidence: 利用细胞绘画预测扰动下的细胞表型响应
tldr: 针对细胞绘画表示受批次效应影响的问题，提出CWA-MSN框架，通过跨孔对齐掩码孪生网络，将相同扰动的细胞嵌入对齐，学习语义一致且批次鲁棒的表征，有效提升了对化学和遗传扰动表型响应的预测能力。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 细胞绘画表示学习受批次效应影响，现有方法需要大量数据。
method: 跨孔对齐掩码孪生网络，强制相同扰动细胞嵌入一致。
result: 在扰动响应预测任务中表现优异。
conclusion: 跨孔对齐可提升细胞绘画表征的鲁棒性和预测能力。
---

## Abstract
Computational models that predict cellular phenotypic responses to chemical and genetic perturbations can accelerate drug discovery by prioritizing therapeutic hypotheses and reducing costly wet-lab iteration. However, extracting biologically meaningful and batch-robust cell painting representations remains challenging. Conventional self-supervised and contrastive learning approaches often require a large-scale model and/or a huge amount of carefully curated data, still struggling with batch effects. We present Cross-Well Aligned Masked Siamese Network (CWA-MSN), a novel representation learning framework that aligns embeddings of cells subjected to the same perturbation across different wells, enforcing semantic consistency despite batch effects. Integrated into a masked siamese architecture, this alignment yields features that capture fine-grained morphology while remaining data- and parameter-efficient. For instance, in a gene-gene relationship retrieval benchmark, CWA-MSN outperforms the state-of-the-art publicly available self-supervised (OpenPhenom) and contrastive learning (CellCLIP) methods, improving the benchmark scores by +29\% and +9\%, respectively, while training on substantially fewer data (e.g., 0.2M images for CWA-MSN vs. 2.2M images for OpenPhenom) or smaller model size (e.g., 22M parameters for CWA-MSN vs. 1.48B parameters for CellCLIP). Extensive experiments demonstrate that CWA-MSN is a simple and effective way to learn cell image representation, enabling efficient phenotype modeling even under limited data and parameter budgets. The source code for CWA-MSN is available at [anonymous code link](https://anonymous.4open.science/r/cwa-msn-56D0DEZIMYNONA/README.md)

---

## 论文详细总结（自动生成）

# 中文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：在药物发现中，计算模型需要从细胞绘画（Cell Painting）图像中预测细胞对化学和遗传扰动的表型响应。然而，细胞绘画表示学习受到严重的 **批次效应（batch effects）** 影响——即使施加相同扰动的细胞，在不同实验孔（well）中成像时，其表征也会因实验条件差异而产生偏移。现有自监督和对比学习方法（如OpenPhenom、CellCLIP）要么依赖海量数据和庞大模型，要么仍难以有效消除批次效应。
- **研究动机**：希望提出一种 **数据高效、参数轻量** 的表示学习框架，能在有限数据下学到 **生物学语义一致且批次鲁棒** 的细胞图像表征，从而提升对扰动表型响应的预测能力。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：设计 **跨孔对齐掩码孪生网络（CWA-MSN）**，强制不同孔中同一扰动的细胞嵌入对齐，在掩码孪生架构下学习批次无关的语义特征。
- **关键技术细节**：
  - 采用 **Masked Siamese Network (MSN)** 作为基础框架，通过掩码图像重建和孪生对比学习提取细粒度形态特征。
  - 引入 **跨孔对齐（Cross-Well Alignment）** 损失：将来自不同实验孔但施加相同扰动的细胞图像对视为正样本，在嵌入空间中拉近其距离；同时保留不同扰动之间的区分性。
  - 整体损失函数包含：MSN的掩码预测损失 + 跨孔对比对齐损失。通过联合优化，模型学到既保留扰动特异性又对批次不敏感的表征。
- **算法流程（文字说明）**：
  1. 输入：一个批次的细胞图像，包含来自多个孔（well）的样本，每个样本标注扰动标签（如基因敲除或化合物处理）。
  2. 通过共享的编码器（如ResNet或Vision Transformer）提取原始与掩码图像的嵌入。
  3. 对于同一扰动标签的样本，无论其来自哪个孔，在嵌入空间计算跨孔正负样本对，应用对比损失（如InfoNCE）拉近同类、推开异类。
  4. 结合掩码图像的预测损失（与MSN相同），更新编码器参数。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：论文提及使用 **0.2M（20万）张细胞绘画图像** 进行训练（CWA-MSN），而对比方法OpenPhenom用了 **2.2M 张图像**，CellCLIP用了 **1.48B 参数**的预训练模型（但数据量未明确）。具体数据集名称未在摘要中给出，推测为公开细胞绘画基准（如JUMP-CP或RxRx等）。
- **基准任务**：**基因-基因关系检索（gene-gene relationship retrieval）**。该任务用于评估模型学习到的嵌入是否能够准确反映生物学关系。
- **对比方法**：
  - OpenPhenom（自监督方法，模型大小未提及但训练数据巨大）
  - CellCLIP（对比学习方法，模型参数量1.48B，数据量可能很大）
  - CWA-MSN（参数量22M，数据量0.2M）
- **结果**：CWA-MSN比OpenPhenom基准分数提升 **+29%**，比CellCLIP提升 **+9%**，同时训练数据和模型大小均大幅减少。

## 4. 资源与算力

- 摘要中**未明确说明**使用了多少GPU型号、数量或训练时长。仅提到CWA-MSN模型参数为22M，相比CellCLIP（1.48B）非常轻量。但未给出具体训练硬件配置和算力开销。因此无法量化资源消耗。

## 5. 实验数量与充分性

- 目前摘要内容仅汇报了 **一个基准任务（基因-基因关系检索）** 上的结果。虽然提到了“大量实验表明”，但未列出其他任务（如化合物-靶点预测、不同数据集、消融实验等）。
- 缺少对以下方面的详细说明：
  - 是否在多个细胞绘画数据集上验证？
  - 是否进行了消融研究（如移除跨孔对齐损失）？
  - 是否评估了批次校正的量化指标（如下游任务精度、嵌入的可视化分离度）？
- 因此，从现有信息看，**实验覆盖度有限**，仅凭单一基准结果不足以全面证明方法的通用性与稳健性。

## 6. 论文的主要结论与发现

- CWA-MSN能够在 **极低的数据量（0.2M）和模型参数量（22M）** 下，显著超越依赖海量数据与超大模型的自监督/对比学习方法（OpenPhenom、CellCLIP）。
- 跨孔对齐策略有效缓解了批次效应，使得学习到的表征具有更好的生物学语义一致性和批次鲁棒性。
- 该方法简单且高效，为数据/算力受限场景下的细胞图像表示学习提供了新思路。

## 7. 优点

- **数据高效**：仅需0.2M图像即可达到甚至超越用2.2M图像训练的方法，极大降低了数据采集成本。
- **参数轻量**：22M参数相比1.48B模型，训练和部署开销极低，适合资源有限的研究团队。
- **思想简洁**：通过直接的跨孔对齐约束解决批次效应，无需复杂的数据增强或额外生成模型。
- **结果显著**：在基因-基因关系检索任务上提升幅度高达29%，具有强烈对比效果。

## 8. 不足与局限

- **实验验证不充分**：仅报告了一个检索基准，缺少对其他下游任务（如化合物表型预测、聚类、分类）以及多个独立数据集上的验证，无法判断泛化能力。
- **算力信息缺失**：未提供训练时的GPU型号、数量和时间，难以重复和评估实用性。
- **批次效应消除的量化不足**：没有直接展示嵌入在批次校正前后的可视化或定量指标（如Alignment、Uniformity），仅通过下游任务间接证明。
- **潜在偏差风险**：跨孔对齐假设“相同扰动的细胞在所有孔中应完全一致”，但实际可能存在孔间生物变异（如位置效应、细胞密度差异），强制对齐可能抹掉有用变异。
- **应用限制**：仅适用于有扰动标签的场景（需要知道每个孔的扰动信息），在无标签的探索性分析中无法直接使用。

（完）
