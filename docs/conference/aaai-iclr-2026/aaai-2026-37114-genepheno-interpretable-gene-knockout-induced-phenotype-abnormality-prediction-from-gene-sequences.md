---
title: "GenePheno: Interpretable Gene Knockout-Induced Phenotype Abnormality Prediction from Gene Sequences"
title_zh: GenePheno：从基因序列预测基因敲除诱导的表型异常的可解释方法
authors: "Jingquan Yan, Yuwei Miao, Lei Yu, Yuzhi Guo, Xue Xiao, Lin Xu, Junzhou Huang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37114/41076"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 基因敲除诱导表型预测
tldr: 现有方法依赖人工筛选的基因信息，可扩展性差。本文提出GenePheno，直接从基因序列预测敲除后多表型异常，弥合了序列与表型之间的模态鸿沟。该方法直接针对遗传扰动响应预测，为虚拟细胞中的扰动建模提供了可解释的序列到表型映射。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37114/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1837, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37114/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1832, \"height\": 453, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37114/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1840, \"height\": 473, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37114/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1810, \"height\": 1599, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37114/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1771, \"height\": 386, \"label\": \"Table\"}]"
motivation: 从基因序列到表型的预测受限于模态鸿沟和多效性，现有方法依赖人工特征。
method: 提出端到端模型，直接从基因序列预测敲除后多个表型是否异常。
result: 在多个物种上取得准确预测，并提供了可解释的序列-表型关联。
conclusion: 为遗传扰动响应预测提供了可扩展、可解释的新途径。
---

## Abstract
Exploring how genetic sequences shape phenotypes is a fundamental challenge in biology and a key step toward scalable, hypothesis-driven experimentation. The task is complicated by the large modality gap between sequences and phenotypes, as well as the pleiotropic nature of gene–phenotype relationships. Existing sequence-based efforts focus on the degree to which variants of specific genes alter a limited set of phenotypes, while general gene knockout-induced phenotype abnormality prediction methods heavily rely on curated genetic information as inputs, which limits scalability and generalizability. As a result, the task of broadly predicting the presence of multiple phenotype abnormalities under gene knockout directly from gene sequences remains underexplored. We introduce GenePheno, the first interpretable multi-label prediction framework that predicts knockout-induced phenotypic abnormalities from gene sequences. GenePheno employs a contrastive multi-label learning objective that captures inter-phenotype correlations, complemented by an exclusive regularization that enforces biological consistency. It further incorporates a gene function bottleneck layer, offering human-interpretable concepts that reflect functional mechanisms behind phenotype formation. To support progress in this area, we curate four datasets with canonical gene sequences as input and multi-label phenotypic abnormalities induced by gene knockouts as targets. Across these datasets, GenePheno achieves state-of-the-art gene-centric Fmax and phenotype-centric AUC, and case studies demonstrate its ability to reveal gene functional mechanisms.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：直接从基因序列（DNA）预测基因敲除后引起的多表型异常，同时要求模型可解释。现有方法要么局限于预测有限表型的变异效应，要么依赖人工整理的蛋白-蛋白互作（PPI）或基因本体（GO）等注释信息，导致对新基因或注释不全的基因适用性差。此外，多表型之间存在强相关性和互斥约束，现有方法常忽略这些关系，产生生物上不一致的预测。
- **背景意义**：理解基因序列如何决定表型是生物学的基础问题，对药物发现、功能基因组学和系统生物学至关重要。该工作首次正式定义了“从基因序列直接预测基因敲除诱导的多标签表型异常”这一深度学习任务。

## 2. 论文提出的方法论

- **核心思想**：提出 GenePheno 框架，融合基因序列与 GO 功能信息，通过对比多标签学习捕获表型间的相关性，并引入互斥正则化强制生物逻辑一致性。网络中含有一个 GO 瓶颈层，提供可解释的“概念”来反映表型形成的功能机制。
- **关键技术细节**：
  - 使用 GENERator（长上下文基因组基础模型）编码基因序列，得到 token 级嵌入。
  - 使用 GoBERT 编码细粒度 GO 注释（深度 >2 的节点），并通过交叉注意力与序列嵌入融合。
  - 将粗粒度 GO 类别（深度 =2 的节点）作为瓶颈层的监督目标，瓶颈层输出为预测的粗粒度 GO 向量，同时其权重矩阵可解释。
  - 多标签预测损失：基于 InfoNCE 推导出对比多标签损失 L_MLC，由正类和负类两部分组成，鼓励同类聚集、异类分离。
  - 互斥正则化：利用大语言模型（LLM）从表型本体（HPO/MPO）中自动发现互斥表型对，并用 Softplus 惩罚同时出现高 logit 的情况，理论上保证了任意稳定点下互斥对不会同时为正。
  - 总损失：L = L_MLC + λ1·Lex + λ2·L_GO_MLC。
- **算法流程**：输入基因序列 + 细粒度 GO 注释 → 分别编码 → 交叉注意力融合 → 注意力池化并拼接 → MLP + GO 瓶颈层 → 输出多标签表型预测，同时瓶颈层输出粗粒度 GO 预测。

## 3. 实验设计

- **使用数据集**：共四个基准数据集。
  - MPO（小鼠表型本体）
  - HPO（人类表型本体）
  - GWAS（来自GWAS Catalog 的基因-表型关联）
  - CAFA2 wPPI（取自 CAFA2 挑战，并确保基因有 PPI 和 GO 信息，以便与依赖人工特征的方法公平比较）
  - 所有数据集均以基因序列为输入，多标签表型异常为输出。
- **Benchmark 与对比方法**：
  - 序列方法：max-BLAST、w-BLAST、kmer2vec+LR、DeepGoPlus、SPROF-GO、InterLabelGO（均改编为序列到表型）。
  - 依赖人工特征的方法（仅在 CAFA2 wPPI 上比较）：DeepPheno、GraphPheno、HPOFiller、HPODNets、SSLPheno。
- **评价指标**：基因中心 Fmax 和表型中心 AUC，按表型频率分层报告（11-30、31-100、101-300、≥301 以及全体）。

## 4. 资源与算力

论文原文 **未明确说明** 所使用的 GPU 型号、数量、训练时长等资源信息。仅在附录中可能提及，但提供的文本中未包含详细计算资源。因此无法总结。

## 5. 实验数量与充分性

- **实验数量**：在四个数据集上进行了主实验（表1），每个数据集报告了按频率分层的 Fmax 和 AUC；一个消融实验（表2），移除各组件（GO输入、序列输入、对比损失、互斥损失、瓶颈损失）后的性能；三个案例研究（图3）展示了瓶颈权重热图。
- **充分性与公平性**：
  - 覆盖了多个物种（人、小鼠）及不同规模的数据集，对比了多种类型基线（序列方法、依赖人工特征的方法）。
  - 按标签频率分层报告避免了因高频率标签主导而掩盖低频率表现。
  - 消融实验验证了每个模块的贡献。
  - 案例研究展示了可解释性。
  - 实验设计较为充分、客观。但缺少跨数据集泛化等额外分析。

## 6. 论文的主要结论与发现

- GenePheno 在所有四个数据集上均取得 **state-of-the-art** 性能，在 Fmax 和 AUC 上显著优于所有基线。例如在 HPO 上，Fmax 比第二名高 +2.72，AUC 高 +13.27。
- 对比多标签损失比传统 BCE 更能捕获表型相关性；互斥正则化有效防止矛盾预测；GO 瓶颈提供了可解释的机制关联（如“maintenance of location”与主动脉异常相关）。
- 即使在没有 PPI 等人工特征的情况下，仅凭基因序列和 GO 注释也能取得优异结果，表明该方法可应用于注释不全的基因。

## 7. 优点

- **首创性**：第一个从基因序列直接预测敲除后多表型异常的端到端可解释框架。
- **方法新颖**：结合对比多标签损失与互斥正则化，理论上保证了稳定性与通用性。
- **可解释性**：GO 瓶颈层直观显示基因功能与表型的关联，案例验证与生物学知识一致。
- **鲁棒性**：在稀疏数据（GWAS）上也保持较好性能，数据规模适应性强。
- **公平比较**：通过在 CAFA2 wPPI 上汇总有 PPI 的基因，与依赖人工特征的方法公平对比，并仍然胜出。

## 8. 不足与局限

- **依赖 GO 注释**：虽然仅需序列和 GO，但仍需细粒度 GO 作为额外输入；对于完全无 GO 注释的基因，模型无法直接应用（论文中只消融了 GO 输入，但未探索零 GO 情况）。
- **算力资源未披露**：无法评估方法的计算成本及可复现性。
- **实验局限**：
  - 仅分析了瓶颈层权重，未对交叉注意力权重等进行深入解释。
  - 互斥对的自动发现依赖 LLM，可能存在错误或遗漏，未系统评估其质量。
  - 未在更多样化的物种（如植物、酵母）上验证通用性。
  - 未与最新的长上下文基因组基础模型（如 Evo2）直接比较序列编码部分，只用了 GENERator。
- **风险偏差**：数据集来源于文献和已有资源，可能存在标注偏差（偏向常见表型）。按频率分层部分缓解但未完全消除。

（完）
