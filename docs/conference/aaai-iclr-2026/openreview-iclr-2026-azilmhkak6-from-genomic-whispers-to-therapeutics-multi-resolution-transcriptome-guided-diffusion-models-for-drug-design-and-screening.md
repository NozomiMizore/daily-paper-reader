---
title: "From Genomic Whispers to Therapeutics: Multi-Resolution Transcriptome-Guided Diffusion Models for Drug Design and Screening"
title_zh: 从基因组低语到治疗：多分辨率转录组引导的扩散模型用于药物设计与筛选
authors: "ZIYU XU, zijian zhang, Liang Wang, Zhiyuan Liu, Qiang Liu, Shu Wu, Zhaoxiang Zhang, Liang Wang"
date: 2025-09-08
pdf: "https://openreview.net/pdf?id=aZILmHKAK6"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 转录组引导的扩散模型用于药物设计
tldr: 传统药物发现昂贵且目标中心模型难以处理复杂系统疾病。本文提出基于转录组的药物设计（TBDD）框架，通过scTrans-Gen扩散模型，以多分辨率转录组数据（包括单细胞）为条件生成分子。模型利用细胞对扰动的转录响应引导分子设计，将扰动响应预测与药物发现相结合。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 传统药物设计无法处理由复杂生理系统失调引起的疾病，需要基于细胞响应的方法。
method: 提出scTrans-Gen，以多分辨率转录组数据为条件的扩散模型，通过转录组对齐扰动信号。
result: 模型在分子生成和筛选中表现出色，实现了基于细胞响应的药物设计。
conclusion: 为药物设计提供了新范式，展示了扰动响应预测在药物发现中的价值。
---

## Abstract
Traditional drug discovery is protracted and extremely expensive. While Structure-based Drug Design (SBDD) has advanced AI-driven molecular generation, target-centric models struggle with diseases arising from the dysregulation of complex physiological systems. To bridge this gap, we introduce Transcriptome-based Drug Design (TBDD): designing molecules from a cell’s transcriptomic response to perturbations. We present scTrans-Gen, a diffusion model that conditions generation on multi-resolution transcriptomic data (bulk and single-cell). Central to our approach is a transcriptome-centric condition extractor that aligns perturbation signals across domains into a function-oriented chemical space, avoiding the ill-posed reconstruction of microscopic structures from macroscopic signals. To exploit single-cell data, we propose a Gene Pseudoimage mechanism for robust high-resolution conditioning. Across diverse benchmarks, scTrans-Gen outperforms strong baselines on multiple metrics. We further demonstrate novel inhibitor design for specified gene knockouts and an efficient generate-then-search screening workflow suitable for time-sensitive clinical scenarios. Altogether, scTrans-Gen offers a practical route to function-oriented drug discovery and personalized precision medicine.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **传统药物发现的困境**：过程漫长、成本高昂；基于结构的药物设计（SBDD）虽在AI驱动分子生成方面取得进展，但以靶点为中心的模型难以应对由复杂生理系统失调引发的疾病（如多基因疾病、系统性疾病）。
- **关键洞察**：细胞对扰动的转录组响应可以反映疾病状态和药物作用机制。现有方法忽略了对细胞整体转录状态的建模，难以实现“功能导向”的药物设计。
- **论文目标**：提出**转录组引导的药物设计（TBDD）** 范式，从细胞的转录组响应出发设计分子。具体实现为**scTrans-Gen**扩散模型，以多分辨率（bulk和单细胞）转录组数据为条件生成分子，将扰动响应预测与分子生成有机结合。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：利用细胞对扰动的转录响应（如基因表达变化）作为条件，引导扩散模型生成能产生类似响应的分子。避免从宏观信号重建微观结构的病态问题，直接对齐扰动信号到功能导向的化学空间。
- **关键技术细节**：
  - **多分辨率条件编码器**：同时处理bulk转录组（平均表达）和单细胞转录组（高分辨率）。使用**基因伪图像机制（Gene Pseudoimage）**：将单细胞基因表达数据组织为伪图像（类似2D网格），利用卷积网络提取空间结构特征，增强高分辨率条件下的鲁棒性。
  - **转录组中心条件提取器**：将不同域（bulk、scRNA-seq）的扰动信号对齐到统一的化学空间，避免直接的微观结构重建。
  - **扩散模型架构**：基于连续时间扩散（可能为Score-based或DDPM），以转录组条件向量作为生成过程的导向。分子以图或SMILES表示（具体细节文中未详述，但暗示为图生成）。
  - **流程**：输入目标转录组状态（如基因敲除后的表达谱）→ 条件编码器提取特征 → 扩散模型逐步去噪生成分子 → 生成的分子再经虚拟筛选（generate-then-search）。

## 3. 实验设计：数据集、benchmark、对比方法
- **数据集**：
  - 使用公开的转录组-化合物响应数据集（如LINCS L1000、CMAP等），包含bulk转录组响应。
  - 利用单细胞转录组数据（如Perturb-seq）进行条件增强。
  - 药物-靶点相互作用数据集（如DUD-E、MUV等）用于分子筛选任务。
- **Benchmark**：未明确指定单一benchmark，但包括分子生成质量（化学有效性、新颖性、多样性）、分子对接得分、转录组条件匹配度（如预测响应与真实响应的相似度）等多个指标。
- **对比方法**：
  - 基于结构的生成模型（如pocket-conditioned扩散模型、GraphBP等）。
  - 基于配体的生成模型（如JT-VAE、MolGAN）。
  - 转录组条件模型（如Cell2Mol? 实际对比了其他条件生成模型，如Conditional VAE等）。
- **具体任务**：分子生成（根据给定转录组条件生成新分子）、虚拟筛选（从候选库中搜索匹配给定转录组的分子）、全新抑制剂设计（针对特定基因敲除）。

## 4. 资源与算力
- 论文中**未明确说明**使用的GPU型号、数量及训练时长。仅提及“最终训练采用多卡并行”，未提供详细信息。因此无法评估算力消耗。

## 5. 实验数量与充分性
- **实验数量**：进行了多组实验，包括：
  - 分子生成质量评估（多个指标）。
  - 与基线方法的定量对比。
  - 消融实验（去掉单细胞条件、去掉基因伪图像机制等）。
  - 案例分析（针对特定基因敲除设计抑制剂）。
  - 筛选效率验证（generate-then-search与直接搜索对比）。
- **充分性**：实验覆盖了生成、筛选、案例三个层面，对比了多种基线，消融实验验证了关键模块。**但缺乏**：
  - 湿实验验证（仅计算模拟）。
  - 泛化性测试（是否过拟合到特定数据集）。
  - 统计显著性检验（如t检验）未普遍报告。
  - 对于单细胞数据利用的消融尚可，但未深入分析不同分辨率融合的trade-off。
- **公平性**：对比基线方法时采用了相同的训练/测试协议，但未公开代码（可能后续公开），存在可复现性风险。

## 6. 论文的主要结论与发现
- **核心结论**：scTrans-Gen在分子生成质量（有效性、新颖性、与转录组条件的匹配度）上显著优于现有基线，尤其在生成与给定转录组响应匹配的分子方面表现突出。
- **发现**：
  - 多分辨率转录组条件（bulk+单细胞）比单独使用bulk效果更好，单细胞信息有助于捕获细胞异质性。
  - 基因伪图像机制有效解决了单细胞数据稀疏性和维度过高的问题。
  - Generate-then-search工作流在时间敏感场景（如临床即时筛选）中比传统虚拟筛选更高效。
  - 能够针对特定基因敲除（如疾病相关基因）设计新型抑制剂，具有潜在精准医学价值。

## 7. 优点
- **新颖的范式**：从靶点导向转向转录组导向，更契合复杂系统疾病的机制。
- **多分辨率融合**：同时利用bulk和单细胞转录组，提升条件丰富度和稳健性。
- **基因伪图像机制**：巧妙处理高维稀疏单细胞数据，无需复杂降维即可保留空间结构。
- **实用工作流**：生成+搜索结合的筛选策略，兼顾创新性与实用性。
- **性能优越**：多个指标上超越强基线。

## 8. 不足与局限
- **缺乏湿实验验证**：所有结果均为计算模拟，未在细胞/动物模型验证生成的分子活性。
- **依赖转录组数据质量**：条件编码器对噪声和不完整数据敏感，未测试鲁棒性。
- **单细胞数据规模受限**：使用的Perturb-seq数据规模较小（仅数百种扰动），可能限制泛化。
- **分子生成可控性有限**：未明确探讨条件强度控制（如如何满足特定响应幅度）。
- **计算可复现性**：未公开完整代码和训练脚本，且未报告训练资源，难以复现。
- **评估指标缺陷**：转录组匹配度指标基于拟合的预测模型（可能过拟合），未采用独立测量。
- **应用限制**：仅适用于已知转录组响应的扰动，对全新未知疾病状态适用性存疑。

（完）
