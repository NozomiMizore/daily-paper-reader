---
title: Transcriptomic data and biomedical literature synergize in finding pharmacologic gene regulators
title_zh: 转录组数据与生物医学文献协同发现药理基因调控因子
authors: "Deisseroth, C. A., Brazelton, B., Shaik, Z., Sandberg, B. S., Liu, Z., Zoghbi, H. Y."
date: 2026-07-15
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.13.708862v2.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 利用转录组数据预测能对抗基因敲低/敲除效应的药物，直接预测细胞扰动响应
tldr: 多数单基因疾病缺乏靶向治疗，药物重定位需要识别能逆转基因扰动效应的化合物。本文提出SNACKKSS，自动从GEO中挖掘RNA-Seq的基因敲除/敲低和药物处理研究，并联合统一计算的数据集直接预测调控关系。交叉验证表明其变体SA4在预测蛋白抑制化合物方面有独特贡献，且整合多个预测工具可提升性能。研究支持将自动挖掘的RNA-Seq特征与文献和共表达预测器结合，用于药物重定位优先排序。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-13-708862-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1963, \"height\": 990, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-13-708862-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1352, \"height\": 1333, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-13-708862-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1971, \"height\": 1983, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-13-708862-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1949, \"height\": 991, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-03-13-708862-v2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1704, \"height\": 400, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-03-13-708862-v2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1709, \"height\": 669, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-03-13-708862-v2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1973, \"height\": 563, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-03-13-708862-v2/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1897, \"height\": 887, \"label\": \"Table\"}]"
motivation: 单基因疾病缺乏靶向治疗，手动标注RNA-Seq研究标签耗时且需领域知识，亟需自动化方法挖掘转录组数据以辅助药物发现。
method: 提出SNACKKSS，自动从GEO中提取基因扰动和药物处理研究的RNA-Seq数据，并结合统一计算的数据集直接预测基因调控关系。
result: 交叉验证显示SNACKKSS的变体SA4在预测蛋白抑制化合物方面具有独特贡献，且与现有文献和共表达预测器集成后性能更优。
conclusion: 自动挖掘的RNA-Seq特征可与传统预测器互补，有效支持药物重定位，但需注意硬件架构对复杂模型输出的影响。
---

## 摘要
大多数由单个基因产物缺乏或过量引起的疾病缺乏靶向疗法。由于这些疾病可以通过基因过表达、敲除或敲低来建模，因此能够对抗此类扰动转录组效应的药物可能是有前途的治疗候选药物。RNA测序（RNA-Seq）研究可以推动这种药物优先排序，但其标签以自然语言编写，必须手动注释。因此，我们引入了基于自动筛选的敲除、敲低和小分子研究特征网络（SNACKKSS），该网络自动从基因表达综合数据库（Gene Expression Omnibus）中筛选基因破坏和药物治疗研究，并与统一计算的读数计数数据集协同工作，直接将标签和RNA-Seq数据输入调控关系预测。通过交叉验证，我们表明SNACKKSS的预测（具体来自名为“SA4”的变体）在寻找蛋白质抑制化合物方面做出了独特贡献，即使与现有预测工具一起使用也是如此。我们证明了聚合多个预测工具的优势，并提供了这个强大的集成模型以及SNACKKSS。重要的是，我们建议研究人员在多个设备上测试复杂的机器学习模型，因为硬件架构可能会影响其输出。尽管如此，下游预测能力令人瞩目，我们的发现支持将自动筛选的RNA-Seq特征与基于文献和共表达的预测工具整合用于药物重定位优先排序的价值。

## Abstract
Most disorders caused by a deficiency or excess of one gene product lack targeted therapies. Since these disorders can be modeled with a gene overexpression, knockout, or knockdown, drugs that oppose the transcriptomic effects of such perturbations may be promising therapeutic candidates. RNA-Sequencing (RNA-Seq) studies can fuel this drug-prioritization, but their labels, written in plain language, must be annotated manually. Hence, we introduce Signature-based Networks from Automatically Curated Knockout, Knockdown, and Small-molecule Studies (SNACKKSS), which automatically curates gene-disruption and drug-treatment studies from the Gene Expression Omnibus and, in partnership with uniformly computed read count datasets, feeds the labels and RNA-Seq data directly into regulatory relationship predictions. Through cross-validation, we show that SNACKKSS' predictions (specifically, from a variation called "SA4") make a unique contribution to finding protein-inhibiting compounds, even alongside existing predictors. We demonstrate the benefit of aggregating multiple predictive tools, and provide this powerful ensemble alongside SNACKKSS. Importantly, we advise researchers to test complex machine learning models on multiple devices, since the hardware architecture can affect their output. Nonetheless, the downstream predictive ability was striking, and our findings support the value of integrating automatically curated RNA-Seq signatures with literature- and co-expression-based predictors for drug-repurposing prioritization.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：多数单基因疾病（如孟德尔病）缺乏靶向疗法，而药物重定位（drug repurposing）有望快速找到安全有效的化合物。传统方法依赖手动标注转录组研究或基于文献的路径分析，难以规模化利用海量公共 RNA-Seq 数据（如 GEO 中的数百万样本）。
- **研究动机**：如果能自动从 RNA-Seq 研究中提取出基因敲除/敲低（KO/KD）和药物处理实验，并计算出可比的“基因表达特征”（signature），则可通过“特征逆转”原则（即药物特征与疾病相关基因扰动特征相反）来优先筛选候选药物。然而，GEO 中的研究描述为自然语言，缺乏统一、机器可读的标注。
- **整体含义**：本文提出 SNACKKSS（Signature-based Networks from Automatically Curated Knockout, Knockdown, and Small-molecule Studies）系统，自动解析 GEO 元数据，将标注结果与统一计算的读计数数据结合，直接预测药物-基因的调控关系，并通过与已有文献和共表达预测工具的集成，提升药物重定位的召回率，从而加速罕见病靶向疗法的发现。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：构建一个全自动化的流水线，将自然语言处理（NLP）模型与差异化表达分析、签名匹配及图链接方法结合，从 RNA-Seq 公共数据中识别能够调控特定基因产物的化合物。
- **关键技术细节**：
  1. **元数据自动标注**：使用微调的 BERT 模型（DistilBERT、BioBERT、BioMedBERT）执行四个分类任务：
     - 研究级分类（是否为基因扰动研究）、样本级分类（样本是否接受扰动）、目标识别（哪个基因被扰动）、对照鉴定（哪个未处理样本是对照）。药物处理研究使用类似流程。
     - 训练数据来自手动标注的随机 GEO 样本（SNACKKSS-MC，625 个系列）和已有数据库 CREEDS。
  2. **读计数整合与签名计算**：从三个统一计算数据库（ARCHS4、Recount3、DEE2）获取样本的 TPM 表达值，对每个扰动样本计算相对于其对照的 Z 分数，然后对所有同一种扰动（同一基因 KO 或同一药物）的 Z 分数再计算“嵌套 Z 分数”（nested z-score），作为该扰动的统一签名。
  3. **签名匹配算法**：提出 **Differential F1（DF1）** 度量，用于量化两个签名间的相似度。DF1 基于支持性（方向相同）和对抗性（方向相反）差异表达基因的数量，分别计算平滑的 F1 分数，并最终通过差值得到方向性分数（正值表示支持/抑制，负值表示拮抗/激活）。公式见论文第7页（省略具体代数）。
  4. **链接与集成预测**：将 SNACKKSS 的 DF1 分数（视为基因-基因或药物-基因关系得分）与 ARCHS4 的基因共表达 Pearson 相关系数通过间接预测公式（PARMESAN 的 I_CA 公式）结合，形成 **SA4** 预测器。类似地，还生成了 PA4、P3A4、CMA4 等变体。
  5. **集成决策**：通过留一法交叉验证（LOOCV）为每个预测器的得分映射到一个“置信度”（平滑精确率估计），最终选择置信度最高的预测器给出的方向作为集成输出。

### 3. 实验设计

- **数据集**：
  - **训练与验证**：手动标注的随机 GEO 样本（SNACKKSS-MC，625 个系列）和已有 CREEDS 数据集（微阵列研究）。
  - **读计数**：ARCHS4（v2.5）、Recount3、DEE2。
  - **金标准数据库**：Reactome（基因-基因关系）、DGIdb（药物-基因关系）。
  - **独立验证**：TRRUST v2、Drug Repurposing Hub、PharmGKB、Guide to Pharmacology、ChEMBL（排除 Reactome/DGIdb 中已有关系）。
- **Benchmark**：以金标准中的关系方向作为正确标签，计算预测器的精确率（precision）和召回率（recall），并使用对数秩检验（log-rank test）评估能否优先给出正确方向。
- **对比方法**：
  - 基于文献的工具：PARMESAN（共识/间接预测）、PubTator3（共识/间接预测）
  - 共表达工具：ARCHS4 人类/小鼠基因共表达矩阵（A4C）
  - 签名匹配工具：Connectivity Map（CMap，包括默认及四种修改：Inferred、shRNA only、MCF7、OE-corrected）
  - 链接工具：PA4、P3A4、CMA4、SA4
  - 集成模型：包含以上所有工具（除被移除的测试项外）。
- **消融实验**：
  - SNACKKSS 的三种修改：Target-down（仅接受靶基因表达下降的样本）、ARCHS4-only（仅用 ARCHS4 数据）、Mouse（使用小鼠数据）。
  - CMap 的四种修改。
  - 逐个移除预测器，观察集成性能变化。
  - 使用 Spearman 相关系数代替 DF1 进行签名匹配的比较。

### 4. 资源与算力

- **计算资源**：论文未明确说明使用的 GPU 型号、数量或训练时长。仅在 NLP 部分提到使用了 40 核和 64 核 CPU 进行模型训练和推理，并指出不同 CPU 架构会导致 BERT 模型输出差异（由于浮点精度和并行顺序不同）。所有代码在 Docker 容器中运行，锁定随机种子。
- **其他**：签名匹配和集成预测在单机上运行，但未给出具体耗时估算，仅提到 DF1 比 Spearman 相关系数快得多（后者需对数千基因排序，计算量过大）。

### 5. 实验数量与充分性

- **实验数量**：相当丰富，包括：
  - BERT 模型 4 折交叉验证（8 个分类任务 × 4 种训练设置 × 3 个模型 × 2 个硬件配置）。
  - SNACKKSS 签名匹配：默认 + 3 种修改，分别在基因-基因和药物-基因上测试。
  - CMap 签名匹配：默认 + 4 种修改。
  - 与 6 个其他预测工具的比较（每个工具在 4 个关系类型上测试）。
  - 集成模型消融：逐个移除任一工具，共约 10 个移除实验，每个在 4 个关系类型上测试。
  - 在两个独立金标准（TRRUST/Repurposing Hub 等）上重复主分析。
  - Spearman 相关性对比。
- **充分性与公平性**：
  - **优点**：使用了交叉验证和留一法；测试了多种修改和消融；在独立金标准上验证，避免过度拟合；考虑了硬件差异对结果的影响。
  - **不足**：性能评估主要基于金标准数据库中的已知关系，未完全模拟实际药物筛选场景（如假阴性案例）；签名匹配方法 DF1 未经系统优化（作者自述并非最优，但足够用于验证概念）；手动标注数据集仅 625 个系列，且来自两位高中水平研究者，存在一定偏差；集成模型对抑制性基因-基因关系表现不佳，可能由于方向性偏见未有效处理。

### 6. 论文的主要结论与发现

- SNACKKSS 自动标注的基因扰动和药物处理研究具有较高的准确性（手动验证者间一致性 > 90%），且靶基因表达下降的比例显著（>70%）。
- 直接签名匹配（SNACKKSS 默认）在基因-基因关系上稍有表现，但在药物-基因关系上预测能力弱；但其链接到共表达矩阵后的变体 **SA4** 在预测抑制性药物-基因关系上表现出显著优先级（log-rank p 调整后 < 10⁻²⁷）。
- 将 SA4 加入集成模型后，可在不牺牲精确率的前提下大幅提升抑制性药物的召回率（例如在 95% 精确率下，可覆盖额外 40 个靶基因）。
- 没有任何单一预测器在所有任务上最优；集成模型（包括多种工具）在药物-基因关系预测上显著优于最佳单一工具。
- 硬件架构（CPU 核心数）会影响复杂深度学习模型的输出结果，建议在多个设备上验证可重复性。

### 7. 优点

- **自动化程度高**：从元数据标注到关系预测完全自动，无需手动干预，可扩展至整个 GEO。
- **数据源整合**：融合了三个统一计算数据库（ARCHS4、Recount3、DEE2），提升了覆盖率和稳健性。
- **集成策略**：基于置信度的最大投票机制，有效利用各预测器的互补性，并量化了每个工具的价值。
- **实际应用导向**：提供了公开的预测结果网站和代码仓库，便于其他研究人员使用。
- **深入分析硬件影响**：首次指出 CPU 核心数差异可导致 BERT 模型输出微小但不可忽略的变化，对可重复性提出警示。

### 8. 不足与局限

- **签名匹配方法并非最优**：DF1 是基于阈值的硬分类方法，可能丢失连续信息；作者承认 Spearman 或其他度量可能更好但计算成本高，未进行全面优化。
- **手动标注噪音**：自动标注基于相对小规模（625 个系列）的手动训练数据，且标注者经验有限，可能引入偏差；标注质量未必代表整个 GEO。
- **不考虑组织特异性**：SNACKKSS 未显式控制细胞类型或组织来源；尽管 CMap 实验考虑了细胞系，但集成模型并未利用此信息。
- **方向性偏见**：大多数预测器（包括 SA4）更倾向于预测“支持性”关系（对基因-基因）或“抑制性”关系（对药物-基因），导致对稀有方向（如抑制性基因-基因）的预测覆盖率低。
- **集成模型对某些关系无效**：对于抑制性基因-基因关系，集成模型反而比单独使用 PARMESAN 间接预测更差；对支持性药物-基因关系，集成无改进。
- **计算资源需求**：尽管签名匹配快，但 NLP 训练和多模型集成需要大量 CPU/内存，未提供详细时间评估，可能限制普通实验室复现。
- **应用限制**：药物预测基于转录组特征逆转原则，但疾病中有些特征可能是补偿性而非因果性的，工具无法区分；结果仅供假设生成，不可直接用于临床决策。

（完）
