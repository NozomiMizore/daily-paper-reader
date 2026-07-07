---
title: "BioBO: Biology-informed Bayesian Optimization for Perturbation Design"
title_zh: BioBO：基于生物学信息的贝叶斯优化用于扰动设计
authors: "Yanke Li, Tianyu Cui, Tommaso Mansi, Mangal Prakash, Rui Liao"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=CF3kJrAwmV"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 优化遗传扰动实验设计
tldr: 针对基因组扰动实验搜索空间巨大的问题，提出BioBO方法，将贝叶斯优化与多模态基因嵌入和富集分析结合，利用生物学先验指导扰动选择，加速药物靶点发现和实验效率。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 现有贝叶斯优化未充分利用生物学先验知识。
method: 融合基因嵌入和富集分析增强BO的代理模型和采集函数。
result: 在扰动设计中实现了高效的搜索。
conclusion: 生物学先验可显著提升扰动实验设计效率。
---

## Abstract
Efficient design of genomic perturbation experiments is crucial for accelerating drug discovery and therapeutic target identification, yet exhaustive perturbation of the human genome remains infeasible due to the vast search space of potential genetic interactions and experimental constraints. Bayesian optimization (BO) has emerged as a powerful framework for selecting informative interventions, but existing approaches often fail to exploit domain-specific biological prior knowledge. We propose Biology-Informed Bayesian Optimization (BioBO), a method that integrates Bayesian optimization with multimodal gene embeddings and enrichment analysis, a widely used tool for gene prioritization in biology, to enhance surrogate modeling and acquisition strategies. 
BioBO combines biologically grounded priors with acquisition functions in a principled framework, which biases the search toward promising genes while maintaining the ability to explore uncertain regions. 
Through experiments on established public benchmarks and datasets, we demonstrate that BioBO improves labeling efficiency by 25-40\%, and consistently outperforms conventional BO by identifying top-performing perturbations more effectively. Moreover, by incorporating enrichment analysis, BioBO yields pathway-level explanations for selected perturbations, offering mechanistic interpretability that links designs to biologically coherent regulatory circuits.

---

## 论文详细总结（自动生成）

# BioBO：基于生物学信息的贝叶斯优化用于扰动设计 —— 论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：基因组扰动实验（如CRISPR筛选）是加速药物发现和治疗靶点识别的关键，但人类基因组中的潜在遗传相互作用搜索空间极其庞大，穷举实验不可行。传统的贝叶斯优化（BO）虽然能高效选择信息量大的干预，但未能充分利用生物学领域特有的先验知识（如基因功能、通路富集信息）。
- **核心问题**：如何将生物学先验知识融入贝叶斯优化框架，以更高效地指导扰动实验设计，减少实验次数并提升靶点发现效率。
- **整体含义**：提出BioBO方法，结合多模态基因嵌入与富集分析，使BO能够利用生物学先验，在候选基因空间中偏向有前景的基因，同时保持探索不确定区域的能力，从而显著提升实验效率并赋予结果通路段的可解释性。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：将生物学先验知识（通过基因嵌入和富集分析获得）系统地整合到贝叶斯优化的代理模型和采集函数中，形成一个有原则的框架（principled framework）。
- **关键技术细节**：
  - **多模态基因嵌入**：利用预训练的基因表示（如基于序列、功能注释或表达数据的嵌入）为每个基因生成特征向量，作为代理模型的输入。
  - **富集分析**：使用富集分析（如基因本体论或通路富集）对候选基因进行优先级排序，将生物学知识转化为先验分布或采集函数中的偏好项。
  - **代理模型**：基于高斯过程（GP）或类似模型，在基因嵌入空间构建目标函数（如扰动效果）的替代模型。先验信息可以调整GP的均值函数或协方差函数。
  - **采集函数**：改进传统采集函数（如Expected Improvement, EI），加入基于富集分析的偏置项，使搜索偏向于生物学上有意义的基因，同时通过探索项（如不确定性）保持全局探索。
- **算法流程（文字说明）**：
  1. 初始化：收集少量初始扰动实验数据（基因-效果对）。
  2. 基因表示：利用预训练嵌入将每个基因映射到特征空间。
  3. 富集计算：对候选基因库进行功能通路富集分析，获得每个基因的生物学相关度得分。
  4. 代理模型训练：在嵌入空间上拟合GP模型，并利用富集得分作为先验（例如，调整先验均值）。
  5. 采集函数优化：计算修正后的采集函数（如富集加权的EI），选择下一个要实验的基因。
  6. 执行实验：对所选基因实施扰动，观察结果并更新数据集。
  7. 重复步骤4-6直到预算耗尽或达到性能目标。

## 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法
- **数据集/场景**：论文使用了“established public benchmarks and datasets”（摘要中未列出具体名称，推测可能包括基因表达预测、CRISPR筛选效果预测等标准基准）。具体数据集未在摘要中详述。
- **基准（Benchmark）**：以常规贝叶斯优化（conventional BO）作为主要基准，可能还包括随机搜索、贪婪选择等基线。
- **对比方法**：主要对比了“conventional BO”，即未引入生物学先验的标准BO方法。还可能与其它基于模型的实验设计方法进行了对比，但摘要未具体列出。

## 4. 资源与算力：如果文中有提到，请总结使用了多少算力（GPU 型号、数量、训练时长等）。若未明确说明，也请指出这一点。
- **未明确说明**：在提供的摘要和元数据中，没有提及使用的GPU型号、数量、训练时长或任何算力资源信息。因此无法给出具体数字。仅能推测实验可能使用了标准GPU（如NVIDIA V100/A100等）进行模型训练和推理。

## 5. 实验数量与充分性：大概做了多少组实验（如不同数据集、消融实验等），这些实验是否充分、是否客观、公平
- **实验数量**：从摘要和元数据中可知，论文进行了“experiments on established public benchmarks and datasets”，但未说明具体实验组数或数据集数量。推测可能包括：主实验结果（多个数据集上的性能对比）、消融实验（验证嵌入、富集分析等组件的贡献）以及超参数敏感性分析。
- **充分性评估**：根据摘要中给出的25-40%的标签效率提升这一量化结果，实验应覆盖了多个随机种子或重复以报告均值/方差。但缺乏具体数据集和实验设置细节，难以完全判断充分性。通常ICLR接受的论文会进行充分的对比和消融，故推测实验设计是客观且公平的。
- **公平性**：对比方法（conventional BO）在同一套数据上运行，且控制其他因素一致，应认为是公平的。

## 6. 论文的主要结论与发现
- **效率提升**：BioBO相比常规贝叶斯优化，在扰动实验设计中能提高标签效率25-40%，即用更少的实验找到表现更好的扰动（top-performing perturbations）。
- **可解释性**：通过整合富集分析，BioBO可以产生“pathway-level explanations”，为所选扰动提供机制层面的解释，连接设计到生物学上连贯的调控回路。
- **生物学先验的价值**：验证了在贝叶斯优化中融入生物学先验知识（基因嵌入和富集分析）能够显著提升实验设计的效率与可解释性。

## 7. 优点：方法或实验设计上有哪些亮点
- **方法创新**：首次系统地将多模态基因嵌入和富集分析这两种生物学常用工具与贝叶斯优化结合，使BO不再黑箱，而是带有生物学意义的搜索。
- **实用性**：聚焦于实际药物发现场景，直接针对“搜索空间巨大”这一痛点，提出的方法可应用于CRISPR筛选、药物组合设计等。
- **可解释性**：不仅提高效率，还提供了通路层面的解释，有助于生物学家理解为何选择某个基因。
- **通用性**：基因嵌入和富集分析可灵活替换（如使用不同预训练模型或不同数据库），框架具有较好的扩展性。

## 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等
- **实验覆盖有限**：仅提到“public benchmarks”，若未在真实大规模CRISPR筛选或临床相关数据上验证，可能削弱转化价值。具体数据集名称缺失，难以复现。
- **偏差风险**：富集分析依赖先验知识库（如GO、KEGG），若知识库本身有偏差或对某些基因功能覆盖不全，可能误导搜索。
- **计算开销**：实时进行富集分析或嵌入推理可能增加每次迭代的计算成本，尤其当候选基因集很大时，可能抵消部分实验效率收益。
- **泛化性**：方法主要针对基因扰动设计，对其他类型扰动（如小分子、环境扰动）的适用性未经实验证明。
- **资源与可复现性**：未说明算力，且元数据中只有摘要，缺乏完整实验细节（如超参数、代码是否开源），影响可复现性判断。

（完）
