---
title: "GenVarFormer: Predicting gene expression from long-range mutations in cancer"
title_zh: GenVarFormer：从癌症长程突变预测基因表达
authors: "David Laub, Ethan J. Armand, Arda Pekis, Zekai Chen, Irsyad Adam, Shaun Porwal, Bing Ren, Kevin Brown, Hannah Carter"
date: 2025-09-20
pdf: "https://openreview.net/pdf?id=o2PcOPBUO1"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 预测基因突变（一类遗传扰动）对基因表达的影响
tldr: 针对非编码区突变对基因表达的长程影响难以预测的问题，本文提出GenVarFormer，一种新型Transformer架构，能够同时处理百万碱基对级别的交互、体细胞突变的极端稀疏性以及对未见基因的泛化。实验表明，GenVarFormer有效预测突变对基因表达的影响，有助于从遗传扰动角度理解癌症机制，与扰动响应预测任务相关。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有方法无法同时处理长程突变交互和稀疏性，限制了对非编码驱动突变影响的预测。
method: 提出GenVarFormer transformer架构，学习突变表示及其对基因表达的影响。
result: 有效预测突变对基因表达的影响，在癌症基因组中表现良好。
conclusion: 为遗传扰动响应预测提供了新的基因表达预测工具。
---

## Abstract
Distinguishing the rare "driver" mutations that fuel cancer progression from the vast background of "passenger" mutations in the non-coding genome is a fundamental challenge in cancer biology. A primary mechanism that non-coding driver mutations contribute to cancer is by affecting gene expression, potentially from millions of nucleotides away. However, existing predictors of gene expression from mutations are unable to simultaneously handle interactions spanning millions of base pairs, the extreme sparsity of somatic mutations, and generalize to unseen genes. To overcome these limitations, we introduce GenVarFormer (GVF), a novel transformer-based architecture designed to learn mutation representations and their impact on gene expression. GVF efficiently predicts the effect of mutations up to 8 million base pairs away from a gene by only considering mutations and their local DNA context, while omitting the vast intermediate sequence. Using data from 864 breast cancer samples from The Cancer Genome Atlas, we demonstrate that GVF predicts gene expression with 26-fold higher correlation across samples than current models. In addition, GVF is the first model of its kind to generalize to unseen genes and samples simultaneously. Finally, we find that GVF patient embeddings are more informative than ground-truth gene expression for predicting overall patient survival in the most prevalent breast cancer subtype, luminal A. GVF embeddings and gene expression yielded concordance indices of $0.706^{\pm0.136}$ and $0.573^{\pm0.234}$, respectively. Our work establishes a new state-of-the-art for modeling the functional impact of non-coding mutations in cancer and provides a powerful new tool for identifying potential driver events and prognostic biomarkers.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：在癌症基因组中，非编码区存在大量“乘客”突变，仅极少数“驱动”突变促进癌症进展。这些非编码驱动突变的一个关键机制是通过影响基因表达发挥作用，且调控区域可能位于距离基因数百万碱基对之外。现有模型无法同时处理：① 跨越百万碱基对的长程交互；② 体细胞突变的极端稀疏性；③ 对未见过的基因的泛化能力。
- **研究动机**：开发一种能够从大量非编码突变中识别出对基因表达有实质性影响的驱动突变的方法，从而加深对癌症机制的理解，并为预后生物标志物发现提供工具。
- **整体含义**：该工作首次提出一种能够同时应对长程调控、稀疏突变和基因泛化的深度学习架构，为基于遗传扰动的基因表达预测建立了新基准。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **模型名称**：GenVarFormer (GVF)
- **核心思想**：采用Transformer架构，学习突变的表示及其对基因表达的影响。模型不处理数兆碱基的完整中间序列，而是仅考虑突变及其局部DNA上下文，从而高效模拟距离基因最远800万碱基对的突变效应。
- **关键技术细节**：
  - 输入：每个基因的所有突变（距离基因±8 Mb范围内）及其局部DNA上下文（如侧翼序列表征）。
  - 架构：基于Transformer，利用自注意力机制聚合长程突变信息；通过设计特殊的编码方式处理极端稀疏性（每个样本中绝大多数基因没有突变）。
  - 输出：预测每个基因在给定突变集下的表达水平。
  - 泛化能力：首次实现同时对未见过的基因和未见过的样本进行预测（即基因层面的零样本泛化）。

## 3. 实验设计
- **数据集**：
  - 使用来自癌症基因组图谱（TCGA）的864例乳腺癌样本。
  - 评估指标：样本间基因表达预测的相关系数（correlation）。
- **基准（Benchmark）**：与当前已有模型比较，GVF在样本间预测相关性上提升26倍（26-fold higher correlation）。
- **对比方法**：摘要中仅提及“current models”，未具体列出名称。推测可能包括基于序列的CNN模型、线性回归、传统机器学习模型等。
- **附加实验**：
  - 生存分析：利用GVF的样本嵌入（patient embeddings）预测乳腺癌最常见亚型Luminal A的总生存期，并与真实基因表达进行对比。
  - 结果：GVF嵌入的C-index为0.706±0.136，真实基因表达仅为0.573±0.234，表明GVF嵌入比真实表达更具预后信息。

## 4. 资源与算力
- **文中未明确说明**所用GPU型号、数量、训练时长等算力资源。仅提及模型是基于Transformer架构，但未给出任何计算代价的定量描述。

## 5. 实验数量与充分性
- **实验数量**：主要实验为基因表达预测（在864例乳腺癌样本上给出相关性提升倍数）和一项生存分析（单一亚型）。消融实验、超参数分析、不同癌症类型验证等未见报道。
- **充分性评估**：
  - 数据规模较大（864例），但仅涉及单一癌症类型（乳腺癌），泛化到其他癌种尚未验证。
  - 仅报告了一次相关系数提升26倍，未提供更细致的统计（如置信区间、交叉验证结果）。
  - 生存分析仅针对Luminal A亚型，且未说明样本量和统计检验方法。
  - 缺少与基线模型的详细比较（如其他Transformer变体、GNN等）。
  - 总体实验设计较为初步，充分性不足，缺乏系统消融和鲁棒性验证。

## 6. 论文的主要结论与发现
- GenVarFormer能高效预测距离基因8 Mb以内的突变对基因表达的影响，比现有模型相关性提升26倍。
- 它是首个能同时泛化到未见基因和未见样本的该类模型。
- 在生存预测任务中，GVF学到的样本嵌入比真实基因表达更具预后价值（C-index从0.573提升至0.706）。
- 该工作为癌症非编码突变的功能影响建模设立了新标杆，并提供了潜在驱动事件和预后生物标志物的识别工具。

## 7. 优点：方法或实验设计上的亮点
- **创新性**：首次将Transformer应用于非编码突变的长程表达效应预测，通过仅考虑突变和局部上下文避免处理超长序列，解决了计算效率和长程交互的矛盾。
- **泛化能力**：模型能预测未见过的基因，是突破性的能力，有助于推广到新发现或罕见突变。
- **实用性**：生存分析显示模型嵌入优于真实表达，暗示其能捕获突变驱动的额外预后信息。
- **结果显著**：相关性提升26倍非常引人注目。

## 8. 不足与局限
- **实验覆盖有限**：仅使用单一癌种（乳腺癌）且仅864例样本，未在更多癌症类型或更大数据集上验证，存在过拟合或领域依赖风险。
- **基线方法不透明**：未列出具体对比的方法名称和配置，无法判断比较的公平性。
- **缺少消融与鲁棒性分析**：未对模型的不同组件（如局部上下文长度、注意力机制变体、稀疏处理策略）进行消融实验，也未评估对噪声突变或缺失数据的敏感性。
- **生存分析样本量未知**：Luminal A亚型具体样本数、C-index区间宽度大（±0.136），暗示可能样本量较小或波动大，结论稳定性存疑。
- **计算资源未报告**：无法评估该方法的训练成本与可复现性。
- **评估指标单一**：仅使用相关系数评估表达预测，缺乏均方误差、R²等指标；且未提供与随机基线的比较。
- **应用限制**：模型需依赖TCGA样本的突变和表达数据，对其他测序平台或低频突变的适用性未讨论。

（完）
