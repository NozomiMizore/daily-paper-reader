---
title: CAR T cell foundation model predicts immunotherapy response
title_zh: CAR T细胞基础模型预测免疫治疗反应
authors: "Li, Y., Fang, D., Mao, C., Wu, X., Luo, Y."
date: 2026-07-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.11.737994v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 利用T细胞基础模型从单细胞转录组预测CAR T免疫治疗响应，直接对应扰动响应预测
tldr: 单细胞转录组学可解析CAR T细胞状态，但将细胞信号转化为患者治疗响应预测仍具挑战。现有方法多识别关联基因或细胞群，缺乏预测框架。本文提出gANCHOR，一个基于层次超图注意力框架的T细胞基础模型，整合基因-通路关系与患者级响应预测。在5项CAR T研究的161名患者中，gANCHOR取得F1=0.87，优于现有模型，并揭示了响应/非响应相关的可解释基因程序。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737994-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1463, \"height\": 1455, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737994-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1520, \"height\": 1832, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737994-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1517, \"height\": 1331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737994-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1515, \"height\": 1315, \"label\": \"Figure\"}]"
motivation: 现有单细胞分析方法难以从异质性细胞信号泛化预测患者对CAR T治疗的响应。
method: gANCHOR采用层次超图注意力，编码基因-通路关系学习通路感知细胞嵌入，并通过细胞到患者注意力模块聚合预测。
result: 在161名CAR T患者中，gANCHOR的F1达0.87，优于基准模型，并识别出可重复的响应与非响应基因程序。
conclusion: gANCHOR有效预测CAR T免疫治疗响应，提供生物学可解释性，有助于理解疗效与耐药机制。
---

## 摘要
单细胞转录组学解析CAR T细胞状态，然而将异质性细胞信号转化为患者层面的治疗反应仍具挑战。现有研究主要通过实验和统计分析识别反应相关基因或细胞群，但很少有预测框架将基因水平结构与临床结局整合。这里，我们提出gANCHOR，一个基于层次超图注意力框架构建的T细胞基础模型，结合了生物学信息表示学习与患者层面反应预测。通过编码基因-通路关系，gANCHOR学习通路感知的细胞嵌入，改善了生物学保存性和批次鲁棒性。细胞-患者注意力模块随后聚合细胞信息以推断治疗反应。在基准数据集上，gANCHOR在生物学保存性和批次校正评估中取得了最强的整体性能。在来自五项CAR T细胞研究的161名患者的反应预测中，gANCHOR达到了0.87的F1分数，优于基准的单细胞基础模型。gANCHOR还识别了可重复的反应相关和非反应相关基因程序，为CAR T细胞疗效和耐药性提供了可解释的生物学见解。

## Abstract
Single-cell transcriptomics resolves CAR T-cell states, yet translating heterogeneous cellular signals into patient-level therapeutic response remains challenging. Existing studies primarily identify response-associated genes or cell populations through experimental and statistical analyses, but few predictive frameworks integrate gene-level structure with clinical outcomes. Here, we present gANCHOR, a T-cell foundation model built on a hierarchical hypergraph attention framework combining biologically informed representation learning with patient-level response prediction. By encoding gene-pathway relationships, gANCHOR learns pathway-aware cell embeddings that improve biological conservation and batch robustness. A cell-to-patient attention module then aggregates cellular information to infer therapeutic response. Across benchmark datasets, gANCHOR achieved the strongest overall performance in biological conservation and batch-correction assessments. In response prediction across 161 patients from five CAR T-cell studies, gANCHOR achieved an F1 score of 0.87, outperforming benchmarked single-cell foundation models. gANCHOR also identified reproducible response- and non-response-associated gene programs, providing interpretable biological insights into CAR T-cell efficacy and resistance.

---

## 论文详细总结（自动生成）

# CAR T细胞基础模型预测免疫治疗反应 - 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：尽管CAR T细胞疗法在血液肿瘤中取得了显著疗效，但患者反应存在巨大异质性。现有的单细胞RNA测序研究多集中于描述反应相关的细胞状态或基因，但缺乏一个能够将单细胞转录组异质性直接用于患者层面治疗反应预测的深度学习框架。
- **核心挑战**：如何从大量单细胞的基因表达数据中提取可泛化的信号，并跨越不同研究间的批次效应，准确预测患者是否对CAR T治疗产生反应。
- **整体目标**：开发一个名为gANCHOR的T细胞基础模型，它通过整合基因-通路先验知识与层次注意力机制，实现从单细胞转录组到患者反应的可解释预测，同时提供生物学洞察。

## 2. 论文提出的方法论
### 2.1 核心思想
- 采用**层次超图注意力框架**，包含两个模块：
  - **模块I（基础模型）**：学习生物学信息丰富的细胞嵌入。
  - **模块II（预测模块）**：通过细胞-患者注意力聚合细胞嵌入，进行患者反应分类。
- 利用**基因-通路关系的超图**（基于MSigDB C2集合）作为结构先验，使模型学习通路感知的基因表示。
- 通过**对抗性批次校正**（梯度反转层）减少技术变异，同时通过多任务目标（细胞类型分类、基因表达重建）保留生物信号。

### 2.2 关键技术细节
- **超图注意力**：在基因-通路二部图（基因 = 节点，通路 = 超边）上进行双向消息传递：
  - 基因 → 通路：聚合基因信息更新通路嵌入。
  - 通路 → 基因：将通路上下文信息分配回基因。
  - 经过两层这样的双重注意力后，得到最终的结构化基因嵌入。
- **表达融合与编码**：将归一化表达值与基因嵌入通过MLP和逐元素相乘融合，输入6层超图注意力编码器。
- **细胞级池化**：通过表达感知的注意力池化（只聚合表达基因）得到细胞嵌入。
- **模块II**：使用固定的细胞嵌入，通过细胞-患者注意力权重加权求和得到患者嵌入，再通过MLP分类器预测反应（加权交叉熵损失，非反应:反应 = 3:1）。
- **训练策略**：模块I先预训练（10个epoch, Adam优化器, lr=1e-5, 权重衰减1e-4, 批次大小64, 嵌入维度128）然后冻结；模块II独立训练（网格搜索lr和权重衰减，早停）。

### 2.3 公式或算法流程（文字说明）
- 流程：基因-通路超图 → 双注意力生成基因嵌入 → 与表达值融合 → 6层超图注意力块 → 细胞级池化 → 多任务解码（分类+重建+对抗） → 得到细胞嵌入 → 模块II中细胞-患者注意力聚合 → 患者嵌入 → MLP分类器 → 反应预测。

## 3. 实验设计
### 3.1 使用数据集
- **预训练数据**：约180万个T细胞和CAR T细胞，来源于12个已发表研究（包括7个参考T细胞数据集和5个CAR T数据集）。
- **反应预测数据**：来自5个独立CAR T研究的161名患者（120名反应，41名非反应）。临床标签统一为二分类（反应/非反应）。
- **数据划分**：参考T细胞按细胞随机划分（5万测试）；CAR T细胞按患者划分（约20%患者作为测试，共34名患者）。

### 3.2 Benchmark和对比方法
- **嵌入质量对比**：与4种批次校正方法（Combat、MNN、scVI、Scanorama）和5种单细胞基础模型（Geneformer、scGPT、scMulan、scFoundation、GenePT）。
- **反应预测对比**：相同的下游架构，使用各模型的预训练嵌入输入；还包括原始基因表达和基因表达均值聚合+逻辑回归两个消融基线。
- **消融实验**：随机打乱通路-基因关系（验证通路先验重要性）；对比注意力衍生表示与原始表达。

### 3.3 评估指标
- **生物学保存**：NMI、ARI、隔离标签分数、细胞类型ASW、cLISI。
- **批次校正**：批次ASW、iLISI、kBET、图连通性、PCR比较。
- **反应预测**：F1分数（主要）、精确率、召回率、AUROC、AUPRC。

## 4. 资源与算力
- 论文提到：“All models were implemented in PyTorch and trained on NVIDIA GPUs”，但**未明确指定GPU型号、数量或训练时长**。这属于信息缺失，无法量化。

## 5. 实验数量与充分性
- **实验数量**：进行了大量的定量比较：
  - 嵌入质量：9种方法在5个生物学保存和5个批次校正指标上比较。
  - 反应预测：7种方法（含基线）在4次独立随机运行上的F1分布，并做了置换检验验证显著性。
  - 消融实验：随机通路打乱、均值聚合基线、注意力衍生表示分析。
  - 重复性验证：4次独立运行中识别DAEGs，仅保留全部一致的基因（59个响应相关、65个非响应相关）。
- **充分性与公平性**：
  - **充分**：覆盖了主流基础模型和传统方法，使用统一的下游架构和相同的训练/测试划分，消除结构偏差。
  - **客观**：超参数网格搜索，多次重复，统计检验。
  - 但**局限**：仅使用CAR T细胞预治疗样本，缺乏治疗后动态数据；没有在不同的肿瘤类型或更大规模队列上验证泛化性。

## 6. 论文的主要结论与发现
- **gANCHOR在嵌入质量上表现最佳**：同时最优地平衡了生物学保存和批次校正，UMAP显示聚类更整齐。
- **gANCHOR在患者反应预测上显著优于所有基准**：F1=0.87，比次优模型高约0.1，且统计显著（置换检验P<0.05）。
- **识别了可再现的响应/非响应基因程序**：
  - 响应组富集：SELL（CD62L）、IL7R、CD27（记忆/干细胞样标记）；XCL1、KLRK1、FGFBP2（细胞毒性）；PTPRC（信号传导）。
  - 非响应组富集：PDCD1、CTLA4、TIGIT（免疫检查点/衰竭）；JUN、JUNB、FOS（AP-1慢性激活）；FOXP3（调节T样）。
  - 这些基因与已发表文献高度一致，确认了记忆 vs. 衰竭轴。
- **模型学到的表示具有生物学可解释性**：基因嵌入按通路聚类，细胞类型分类准确（F1=0.758），注意力权重可识别亚型标志基因。
- **注意力机制优于传统差异表达分析**：在跨批次差异大的患者级分析中，DAEGs更富集功能相关基因，而DEGs被管家基因主导。

## 7. 优点
- **方法创新**：首次将超图注意力应用到CAR T细胞基础模型，整合先验通路知识，使学习到的表示更具生物学结构和可解释性。
- **性能领先**：在多个指标上超越现有单细胞基础模型，且泛化到不同CAR T研究。
- **可解释性**：层次注意力可追溯基因→细胞→患者的贡献，提供机制性洞察，比如识别响应相关的记忆/细胞毒性程序与衰竭程序。
- **理论合理**：双阶段训练避免了小样本预测中的过拟合，批次对抗有效整合异质性数据。

## 8. 不足与局限
- **依赖现有通路注释**：如MSigDB可能不完整或偏向已知功能，限制新通路发现。
- **注意力不是因果**：模型识别的基因仅供假设生成，需要实验验证。
- **分阶段训练**：非端到端，未来可探索联合微调。
- **数据局限**：
  - 仅使用预输注样本，缺乏治疗后动态或纵向数据。
  - 未纳入多组学（如蛋白质、染色质）、空间转录组或更大规模、更多样化的队列。
  - 反应分类为二值简化，忽略部分反应、毒性等其他临床终点。
- **计算资源未报告**：缺少GPU型号、数量、训练时间，无法评估可重复性和不同用户所需资源。
- **未与多模态方法比较**：如结合临床数据、影像等。
- **预印本**：论文未经同行评审，结论需谨慎对待。

（完）
