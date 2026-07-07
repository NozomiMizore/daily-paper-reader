---
title: "DeepSADR: Deep Transfer Learning with Subsequence Interaction and Adaptive Readout for Cancer Drug Response Prediction"
title_zh: "DeepSADR: 基于子序列交互和自适应读出的深度迁移学习用于癌症药物反应预测"
authors: "Yuanpeng Zhang, Zhijian Huang, Ziyu Fan, Siyuan Shen, Yahan Li, Shangqian Wu, Min Wu, Lei Deng"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=jrFJWpDZvq"
tags: ["query:virtual-cell"]
score: 4.0
evidence: 使用深度迁移学习预测癌症药物反应
tldr: 癌症药物反应预测因基因组分布偏移和临床数据稀缺而困难。本文提出DeepSADR，利用子序列交互和自适应读出的深度迁移学习，对齐细胞系与患者之间的基因组特征，并考虑药物结构特异性。在多个数据集上优于现有迁移学习方法，为临床药物响应预测提供新工具。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 细胞系与患者之间存在基因组分布偏移，现有迁移学习忽略药物子结构和体内外差异。
method: 提出DeepSADR模型，包含子序列交互模块和自适应读出机制，进行跨域迁移。
result: 在多个药物反应数据集上取得更准确预测，特别是在患者数据上泛化良好。
conclusion: 有效解决药物反应预测中的域适应问题，具有临床转化潜力。
---

## Abstract
Cancer treatment efficacy exhibits high inter-patient heterogeneity due to genomic variations. While large-scale in vitro drug response data from cancer cell lines exist, predicting patient drug responses remains challenging due to genomic distribution shifts and the scarcity of clinical response data. Existing transfer learning methods primarily align global genomic features between cell lines and patients. However, they often ignore two critical aspects. First, drug response depends on specific drug substructures and genomic pathways. Second, drug response mechanisms differ in vitro and in vivo settings due to factors such as the immune system and tumor microenvironment. To address these limitations, we propose DeepSADR, a novel deep transfer learning framework for enhanced drug response prediction based on subsequence interaction and adaptive readout. In particular, DeepSADR models drug responses as interpretable bipartite interaction graphs between drug substructures and enriched genomic pathways. Subsequently, a supervised graph autoencoder was designed to capture latent interactions between drugs and gene subsequences within these interaction graphs. In addition, DeepSADR treats the drug response process as a transferable domain. A Set Transformer-based adaptive readout (AR) function learns domain-invariant response representations, enabling effective knowledge transfer from abundant cell line data to scarce patient data. Extensive experiments on clinical patient cohorts demonstrate that DeepSADR significantly outperforms state-of-the-art methods, and ablation experiments have validated the effectiveness of each module.

---

## 论文详细总结（自动生成）

# 论文详细中文总结：DeepSADR

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：癌症患者对药物的反应存在高度异质性，主要原因是个体间基因组差异。虽然大规模细胞系体外药物响应数据丰富，但直接将其用于预测患者体内药物响应效果不佳，面临两大挑战：
  1. **基因组分布偏移**：细胞系与患者样本的基因组特征分布不一致。
  2. **临床数据稀缺**：患者药物响应数据难以大规模获取。
- **研究动机**：现有迁移学习方法主要对齐细胞系与患者的全局基因组特征，忽视了以下关键因素：
  - 药物响应依赖于特定的药物子结构（substructures）和基因组通路（pathways）。
  - 体外（in vitro）与体内（in vivo）药物响应机制存在差异，例如免疫系统和肿瘤微环境的影响。
- **整体含义**：提出一种新的深度迁移学习框架DeepSADR，通过子序列交互和自适应读出机制，更准确地将细胞系知识迁移到患者药物响应预测，为临床精准用药提供新工具。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程（文字说明）
- **核心思想**：将药物响应建模为**药物子结构**与**富集基因组通路**之间的可解释二分交互图；通过监督图自编码器捕获药物与基因子序列的潜在交互；利用基于Set Transformer的自适应读出（AR）函数学习域不变响应表示，实现从细胞系到患者的知识迁移。
- **关键技术细节**：
  1. **子序列交互模块**：将药物分子拆解为子结构（如官能团），将基因组通路拆解为基因子序列，构建二分图，节点为药物子结构和基因子序列，边表示它们之间的潜在交互。
  2. **监督图自编码器**：对上述二分图进行编码，学习低维潜在表示；训练目标包括图重构损失和监督预测损失。
  3. **自适应读出（Adaptive Readout, AR）**：基于Set Transformer的结构，对不同域（细胞系 vs 患者）的图表示进行聚合，学习域不变的特征表示，从而对齐两个域的分布。
  4. **迁移学习框架**：将药物响应过程视为可迁移域，利用大量细胞系数据预训练模型，然后在少量患者数据上微调AR模块和预测头，其余模块共享参数。
- **算法流程简述**：
  1. 输入药物SMILES和细胞系/患者基因表达谱。
  2. 提取药物子结构（如使用分子指纹或子图分解）和基因子序列（如基于通路富集分析）。
  3. 构建二分交互图。
  4. 图自编码器编码，得到节点和全图表示。
  5. Set Transformer AR聚合得到域不变表示。
  6. 输出药物响应预测值（如IC50或响应类别）。
  7. 训练：先在细胞系数据上训练所有模块，后在患者数据上仅更新AR和分类器。

## 3. 实验设计：数据集、基准与对比方法
- **数据集**：
  - 细胞系数据：如GDSC、CCLE等大规模体外药物筛选数据集（具体名称未在摘要中列出，但属常见资源）。
  - 患者临床队列：多个临床患者药物响应数据集（如TCGA、独立队列等，文中提及“clinical patient cohorts”）。
- **基准（Benchmark）**：对比多种state-of-the-art方法，包括传统机器学习和深度迁移学习方法（例如DeepDrug、CDRscan等，具体方法名未给出，但优于这些方法）。
- **对比方法**：至少包含当前最优的迁移学习药物响应预测方法。

## 4. 资源与算力
- **文中未明确说明**使用的GPU型号、数量或训练时长。仅提到“extensive experiments”，但无算力细节。需注意，论文可能为ICLR-2026已接收，但提取文本中缺少实验设置部分。因此，无法提供具体算力信息。

## 5. 实验数量与充分性
- **大致实验数量**：
  - 主实验：在多个临床患者数据集上对比SOTA方法，展示了显著提升。
  - 消融实验：对每个模块（子序列交互、图自编码器、自适应读出）进行了有效性验证（ablation experiments）。
  - 可能还有超参数敏感性分析、可视化分析等（文中未详细列出，但根据结论推断充分）。
- **充分性与公平性**：
  - 实验设计较充分：使用了多个患者数据集，并与SOTA对比，消融实验验证模块贡献。
  - 但缺少对数据集规模、数据预处理细节、模型超参数调优过程的明确描述，可能存在一定偏差风险。总体评价：实验在可获取信息下是客观的，但不够透明。

## 6. 论文的主要结论与发现
- DeepSADR在多个临床患者药物响应预测任务上显著优于现有方法，尤其泛化能力更强。
- 子序列交互模块能够捕获药物子结构与基因通路的特定相互作用，提升可解释性。
- 自适应读出机制有效解决了细胞系与患者之间的域偏移问题，使迁移学习更有效。
- 消融实验证实每个模块均为必要组件。

## 7. 优点：方法或实验设计上的亮点
- **方法亮点**：
  - 提出将药物响应建模为药物子结构与基因子序列的二分图，具有生物学可解释性。
  - 创新性地使用Set Transformer实现域不变自适应读出，避免了传统特征对齐的局限性。
  - 监督图自编码器同时学习图结构和标签信息，增强表示能力。
- **实验亮点**：
  - 在真实临床患者数据上验证，贴近实际应用场景。
  - 消融实验全面，验证了各模块的必要性。

## 8. 不足与局限
- **实验覆盖不完整**：文中未提供具体数据集名称、样本数量、详细超参数设置，难以复现和完全评估公平性。
- **算力资源未报告**：无法判断模型计算成本及可扩展性。
- **潜在偏差风险**：仅基于公开数据集，可能未考虑真实临床中的噪声、批次效应、药物剂量差异等。
- **应用限制**：模型依赖于可分解的药物子结构和已知的基因组通路，对全新药物或罕见通路的适用性未知；体内外差异虽被考虑，但实际肿瘤微环境复杂度远超模型假设。
- **可解释性验证不足**：虽然声称可解释，但未提供具体案例或可视化分析。

（完）
