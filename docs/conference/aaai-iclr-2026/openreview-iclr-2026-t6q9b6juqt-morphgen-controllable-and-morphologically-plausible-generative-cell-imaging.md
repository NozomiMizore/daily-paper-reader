---
title: "MorphGen: Controllable and Morphologically Plausible Generative Cell-Imaging"
title_zh: MorphGen：可控且形态合理的生成式细胞成像
authors: "Berker Demirel, Marco Fumero, Theofanis Karaletsos, Francesco Locatello"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=t6Q9B6jUQt"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 可控生成扰动下的细胞成像，支持虚拟细胞模型
tldr: 为推动药物发现和基因编辑中的高内涵成像分析，本文提出MorphGen，一种基于扩散模型的荧光显微图像生成模型，能够在多种细胞类型和不同扰动条件下可控生成形态逼真的图像。通过引入与生物基础模型OpenPhenom表征对齐的损失，MorphGen捕捉了与已知细胞形态一致的有意义模式，无需压缩多通道染色。该模型为虚拟细胞模型提供了生成模拟干预后细胞形态的能力。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有方法将多通道染色压缩为RGB图像，丢失细胞器细节，且无法控制不同扰动条件下的生成。
method: 提出MorphGen扩散模型，使用对齐损失匹配OpenPhenom表型嵌入，支持多细胞类型和扰动条件控制。
result: 生成形态合理、可控制扰动的荧光显微图像。
conclusion: 该模型为虚拟细胞模型提供了可控的细胞形态生成能力，加速药物筛选。
---

## Abstract
Simulating in silico cellular responses to interventions is a promising direction to accelerate high-content image-based assays, critical for advancing drug discovery and gene editing. To support this, we introduce MorphGen, a state-of-the-art diffusion-based generative model for fluorescent microscopy that enables controllable generation across multiple cell types and perturbations. To capture biologically meaningful patterns consistent with known cellular morphologies, MorphGen is trained with an alignment loss to match its representations to the phenotypic embeddings of OpenPhenom, a state-of-the-art biological foundation model. Unlike prior approaches that compress multichannel stains into RGB images --thus sacrificing organelle-specific detail-- MorphGen generates the complete set of fluorescent channels jointly, preserving per-organelle structures and enabling a fine-grained morphological analysis that is essential for biological interpretation. We demonstrate biological consistency with real images via CellProfiler features, and MorphGen attains an FID score over 35% lower than the prior state-of-the-art MorphoDiff, which only generates RGB images for a single cell type.

---

## 论文详细总结（自动生成）

# 论文总结：MorphGen：可控且形态合理的生成式细胞成像

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：高内涵成像分析在药物发现和基因编辑中至关重要，但现有的细胞成像生成方法存在两个主要缺陷：一是将多通道荧光染色压缩为RGB图像，损失了细胞器级别的细节信息；二是无法在多种细胞类型和不同扰动条件下进行可控生成。
- **背景与意义**：推动“虚拟细胞”模型的发展，通过计算机模拟细胞对干预措施（如药物、基因编辑）的形态响应，可大幅加速高内涵筛选，降低实验成本。MorphGen旨在填补这一空白，提供形态学合理的可控生成能力。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：构建一个基于扩散模型的生成式框架，能够同时生成完整的荧光多通道图像（而非压缩为RGB），并在多种细胞类型和多种扰动条件下实现可控生成。通过引入与生物基础模型 OpenPhenom 的表型嵌入对齐的损失函数，确保生成图像捕捉到与已知细胞形态一致的有意义模式。
- **关键技术细节**：
  - 使用扩散模型（Diffusion Model）作为主干生成架构。
  - 输入条件包括细胞类型标签和扰动类型标签，实现条件控制。
  - 训练过程中引入**对齐损失（alignment loss）**：让生成的图像的表征（扩散模型中间层或最终输出）与 OpenPhenom（一个先进的生物基础模型）提取的“真实”表型嵌入相匹配，从而在语义上保持一致。
  - 联合生成所有荧光通道（例如细胞核、线粒体、内质网等各自对应的通道），保持每个细胞器的独立结构和空间关系，支持细粒度的形态学分析。
- **无公式算法流程说明**：模型通过扩散过程逐步去噪生成图像；在每个去噪步骤中，模型不仅接收噪声图像，还接收细胞类型和扰动条件的嵌入；同时，生成过程中的隐层表征被送入一个对齐模块，使其与预先计算的 OpenPhenom 真实图像的表型嵌入的距离最小化。

## 3. 实验设计：数据集、基准与对比方法
- **使用的数据**：未在摘要中明确说明数据集名称（如 Cell Painting 数据集等），但提及“多种细胞类型”和“多种扰动条件”。可以推测使用了公开的多通道荧光显微镜成像数据集（如 Cell Painting 数据集或同类生物图像库）。
- **基准（Benchmark）**：以真实图像为基准，通过 **CellProfiler** 特征计算生物一致性指标，以及 **FID**（Fréchet Inception Distance）衡量生成图像的整体质量。
- **对比方法**：主要与现有最先进方法 **MorphoDiff** 进行了比较。MorphoDiff 仅能生成 RGB 图像且只支持单一细胞类型。实验结果表明 MorphGen 的 FID 分数比 MorphoDiff 降低超过 35%。

## 4. 资源与算力
- **未明确说明**：摘要和元数据中未提及训练所使用的 GPU 型号、数量、训练时长等算力细节。从论文标题为 ICLR-2026 被拒论文来看，可能正文中包含这些信息，但在提供的素材中缺失。因此无法总结。

## 5. 实验数量与充分性
- **实验数量**：仅从摘要可知，至少进行了以下评估：
  - 使用 CellProfiler 特征与真实图像对比（生物一致性）。
  - FID 分数对比（与 MorphoDiff 比较）。
  - 可能还有消融实验（如证明对齐损失的有效性）以及不同细胞类型/扰动条件下的生成效果评估，但摘要未详述。
- **充分性与公平性**：
  - 优点：对比了同类最先进方法，且显示了显著优势（FID 降低35%），指标选择（FID + 生物特征）较全面。
  - 不足：缺少详细的数据集划分、评价指标的细节（如是否统计显著性检验）、多细胞类型内的细粒度对比。由于只提供摘要，无法判断实验的全面性和公平性。推测正文可能有更充分的消融和可视化，但以现有信息难以评估。

## 6. 论文的主要结论与发现
- MorphGen 能够生成形态合理、可控制扰动的荧光显微图像，且完全保留多通道结构。
- 对齐损失使生成图像的表型嵌入与真实图像的表型嵌入一致，提升了生物学意义。
- 相比 MorphoDiff，FID 改善超过 35%，并且能处理多种细胞类型和扰动，而 MorphoDiff 仅限于单一细胞类型的 RGB 输出。
- 该模型为虚拟细胞模型提供了可控的细胞形态生成能力，有望加速药物筛选和基因编辑研究。

## 7. 优点：方法或实验设计上的亮点
- **完整多通道生成**：放弃常见的 RGB 压缩，直接生成多通道荧光图像，保留关键细胞器结构。
- **跨细胞类型+跨扰动控制**：支持对多个条件（细胞类型、扰动）的组合进行生成，更具实际应用价值。
- **引入生物基础模型对齐**：利用 OpenPhenom 的表型嵌入作为指导，在扩散训练中加入对齐损失，巧妙地将生成质量与生物学先验知识结合。
- **评估指标既有生成质量（FID）又有生物语义（CellProfiler特征）**，兼顾了视觉真实性与生物学一致性。

## 8. 不足与局限
- **缺乏详细实验细节**：由于只有摘要，无法判断模型是否在不同规模数据集上稳定、是否进行了充分的消融实验（如移除对齐损失的影响）、是否与其他非扩散模型进行了对比。
- **可能的偏差风险**：OpenPhenom 自身可能存在训练偏差（例如仅在有限细胞系上训练），对齐损失可能导致生成图像偏向该基础模型的隐空间分布，从而忽略了某些罕见且重要的形态变异。
- **应用限制**：生成图像的生物学有效性仍需通过下游任务（如药物响应预测、基因型-表型关联）验证；目前的验证仅基于特征相似度指标，缺乏真实的实验验证。
- **算力开销**：未提及训练成本，但扩散模型通常需要大量 GPU 时间，且联合对齐损失可能增加计算负担，限制了资源有限研究组的复现。
- **被拒稿状态**：该论文被 ICLR-2026 拒绝，暗示可能在某些方面（如方法新颖性、实验完整性或写作）存在不足，但具体原因未知。

（完）
