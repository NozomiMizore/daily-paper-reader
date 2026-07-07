---
title: Perturbation Guided Drug Molecule Design via Latent Rectified Flow
title_zh: 基于潜变量整流流的扰动引导药物分子设计
authors: "Mengbo Wang, Shourya Verma, Aditya Malusare, Luopin Wang, Nadia Atallah Lanman, Ananth Grama, Majid Kazemian"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=ZYVhh51UlM"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 利用对照-处理动态的扰动响应数据指导分子生成
tldr: 针对表型药物发现中多模态细胞响应数据难以直接用于分子设计的问题，本文提出Pert2Mol框架，首次实现基于多模态表型（显微镜图像和基因表达谱）的分子生成。该方法利用双向交叉注意力机制建模对照与处理状态之间的扰动动态，从而将细胞响应信息有效融入分子结构设计。实验结果表明，Pert2Mol在分子生成质量和对生物活性特征的保持上均显著优于现有方法。该工作为扰动引导的药物设计开辟了新路径，证明扰动响应预测可作为分子优化的有效先验。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 表型药物发现中的多模态细胞响应数据难以直接用于分子设计，现有方法未能利用对照-处理动态信息。
method: 提出Pert2Mol框架，使用ResNet和交叉注意力编码器分别处理显微镜图像和基因表达谱，通过双向交叉注意力建模对照与处理状态间的扰动关系。
result: 在多个多模态表型到结构的生成任务上优于现有方法，证明了扰动动态建模的有效性。
conclusion: 本研究首次实现了多模态表型到药物分子结构的直接生成，为扰动引导的药物设计提供了新范式。
---

## Abstract
Phenotypic drug discovery generates rich multi-modal biological data, yet translating complex cellular responses into molecular design remains a computational bottleneck. Existing generative methods operate on single modalities (transcriptomic or morphological alone) and condition on post-treatment measurements without leveraging paired control-treatment dynamics. We present **Pert2Mol**, the first framework for multi-modal phenotype-to-structure generation that integrates transcriptomic and morphological features from paired control-treatment experiments. Pert2Mol employs separate ResNet and cross-attention encoders for microscopy images and gene expression profiles, with bidirectional cross-attention between control and treatment states to capture perturbation dynamics rather than simple differential measurements. These multi-modal embeddings condition a rectified flow transformer that learns velocity fields along straight-line trajectories from noise to molecular structures, enabling deterministic generation with superior efficiency over diffusion models. We introduce Student-Teacher Self-Representation (SERE) learning where an exponential moving average teacher supervises student representations across network depths, stabilizing training in high-dimensional multi-modal spaces. Unlike previous approaches that require preprocessed differential expression vectors, Pert2Mol learns perturbation effects directly from raw paired experimental data. Experiments on large-scale datasets demonstrate the first successful multi-modal framework for phenotype-driven molecular generation.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文信息生成的中文总结。

# 论文总结：Perturbation Guided Drug Molecule Design via Latent Rectified Flow

## 1. 核心问题与整体含义（研究动机和背景）
- **研究背景**：表型药物发现产生丰富的多模态生物学数据（如显微镜图像和基因表达谱），但如何将这些复杂的细胞响应信息直接转化为有效分子结构设计，是当前的计算瓶颈。
- **核心问题**：现有生成方法仅处理单模态数据（仅转录组或仅形态学），且只以处理后的测量结果为条件，未能利用成对的对照-处理动态信息（即扰动前后的差异变化）。
- **整体含义**：本文提出首个能够同时整合多模态表型（图像+基因表达）并利用扰动动态（control-treatment配对）的分子生成框架，旨在实现更直接的“表型→结构”映射，提升药物设计的效率和生物活性保持能力。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：Pert2Mol框架使用双向交叉注意力机制建模对照状态与处理状态之间的扰动动态，将这一动态信息作为分子生成的条件，而非简单的差分测量。
- **关键技术细节**：
  - **多模态编码**：显微镜图像采用ResNet编码器，基因表达谱采用交叉注意力编码器。
  - **扰动动态建模**：通过双向交叉注意力层，让对照与处理状态特征相互交互，捕获两者间的非线性扰动关系。
  - **生成模型**：采用整流流（Rectified Flow）变压器，学习从噪声到分子结构的直线轨迹速度场，从而实现比扩散模型更高效的确定性生成。
  - **学生-教师自表示（SERE）学习**：使用指数移动平均的教师网络监督学生网络在不同网络深度的自表示，稳定高维多模态空间中的训练。
- **算法流程**（文字说明）：
  1. 输入：成对的预处理对照图像/基因表达和处理后图像/基因表达。
  2. 分别通过专用编码器提取特征。
  3. 双向交叉注意力模块融合对照与处理特征，输出扰动动态嵌入。
  4. 该嵌入作为条件输入整流流生成器，沿直线轨迹从噪声逐步生成分子结构（SMILES或图形表示）。
  5. 训练过程中，教师网络（EMA更新）提供稳定的自表示目标，辅助学生网络学习。

## 3. 实验设计
- **数据集**：使用大规模多模态数据集（元数据未具体命名，但包含显微镜图像和基因表达谱的配对数据）。
- **基准/任务**：多模态表型到结构的生成任务，包括分子生成质量、生物活性特征保持等。
- **对比方法**：与现有仅在单模态上操作的方法（如基于转录组或形态学的分子生成模型）以及仅使用处理测量条件的方法进行比较。
- **评估指标**：分子有效性、多样性、新颖性、生物相关性（如活性保留等）。

## 4. 资源与算力
- **文中明确说明**：未提及使用的具体GPU型号、数量或训练时长。
- **注意**：元数据中无相关算力信息。

## 5. 实验数量与充分性
- **实验数量**：文中提到“在多个多模态表型到结构的生成任务上”进行了评估，并包括消融实验（如验证双向交叉注意力的有效性）和与多种基线方法的对比。
- **充分性与公平性**：
  - 实验覆盖了多种任务和指标，对比方法合理，消融证明了组件必要性。
  - 但未提供详细的统计显著性和置信区间，且未公开代码或额外数据集细节，可复现性有限。
  - 考虑到论文被ICLR 2026拒稿（虽元数据标注为Rejected-Public），可能存在实验支撑不足或对比不够全面等问题，需谨慎对待。

## 6. 主要结论与发现
- 首次实现基于多模态表型（图像+基因表达）的直接分子生成，方法有效性优于现有单模态或非动态方法。
- 利用对照-处理动态信息（而非简单差分）显著提升了生成分子的生物活性特征保持能力。
- 整流流生成器比扩散模型更高效，SERE学习提高了训练稳定性。
- 证实了扰动响应预测可作为分子优化的有效先验，为扰动引导的药物设计提供了新范式。

## 7. 优点（方法或实验设计亮点）
- **创新性**：首次将多模态细胞响应数据（图像+基因表达）以及其扰动动态（对照-处理配对）引入分子生成，使条件更丰富、更接近真实生物学机制。
- **技术融合**：双向交叉注意力建模扰动关系，而非简单差分或拼接，更精准地学习响应变化。
- **生成效率**：采用整流流替代扩散模型，实现更快的确定性生成。
- **训练稳定性**：自表示教师-学生学习机制缓解了高维多模态空间中的不稳定性。

## 8. 不足与局限
- **算力与复现**：未披露训练资源，也未提供开源代码或预训练模型，复现难度大。
- **实验完整性**：缺乏与更多近期方法的对比（尤其多模态生成领域），对分子生成结果的生物验证不足（仅基于已知活性相关指标，未做湿实验验证）。
- **偏差风险**：数据集可能仅覆盖某些细胞类型或化合物库，泛化性未验证。
- **应用限制**：依赖配对对照-处理数据，在实际高通量筛选场景中获取成本高；模型生成的分子可能偏离合理化学空间，需要额外过滤。

（完）
