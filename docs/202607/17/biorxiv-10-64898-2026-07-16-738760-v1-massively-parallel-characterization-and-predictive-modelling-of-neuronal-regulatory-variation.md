---
title: Massively parallel characterization and predictive modelling of neuronal regulatory variation
title_zh: 神经元调控变异的超高通量表征与预测建模
authors: "Salomon, K., Deng, C., Dash, P. M., Chalkiadakis, T., Li, Q., Chen, Z., Page, N. F., Helal, M., Roener, S., Kundaje, A., Langenberg, C., Pietzner, M., Shendure, J., Schubach, M., Ahituv, N., Kircher, M."
date: 2026-07-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.16.738760v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 通过大规模lentiMPRA实验量化遗传变异效应，构建调控变异预测模型
tldr: "疾病相关变异常位于非编码顺式调控元件，但其功能影响难以阐明。本研究在人类兴奋性神经元中进行大规模lentiMPRA，量化了超过46,000个自然变异对27,000多个候选CRE的调控效应。结果发现群体频率与变异调控效应大小无关，效应可检测性取决于元件基线活性和局部序列上下文，且调控效应分布于多个转录因子而非主调节因子。该工作建立了大规模功能变异目录，为模型评估提供了基准。"
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-16-738760-v1/fig-001.webp\", \"caption\": \"\", \"page\": 37, \"index\": 1, \"width\": 1437, \"height\": 749}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-16-738760-v1/fig-002.webp\", \"caption\": \"\", \"page\": 38, \"index\": 2, \"width\": 1434, \"height\": 1052}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-16-738760-v1/fig-003.webp\", \"caption\": \"\", \"page\": 39, \"index\": 3, \"width\": 1173, \"height\": 1918}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-16-738760-v1/fig-004.webp\", \"caption\": \"\", \"page\": 41, \"index\": 4, \"width\": 1337, \"height\": 1760}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-16-738760-v1/fig-005.webp\", \"caption\": \"\", \"page\": 43, \"index\": 5, \"width\": 1437, \"height\": 1179}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-16-738760-v1/fig-006.webp\", \"caption\": \"\", \"page\": 44, \"index\": 6, \"width\": 758, \"height\": 932}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-16-738760-v1/fig-007.webp\", \"caption\": \"\", \"page\": 44, \"index\": 7, \"width\": 758, \"height\": 928}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-16-738760-v1/fig-008.webp\", \"caption\": \"\", \"page\": 45, \"index\": 8, \"width\": 390, \"height\": 390}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-16-738760-v1/fig-009.webp\", \"caption\": \"\", \"page\": 46, \"index\": 9, \"width\": 1439, \"height\": 1123}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-16-738760-v1/fig-010.webp\", \"caption\": \"\", \"page\": 47, \"index\": 10, \"width\": 1436, \"height\": 556}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-16-738760-v1/fig-011.webp\", \"caption\": \"\", \"page\": 48, \"index\": 11, \"width\": 790, \"height\": 590}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-16-738760-v1/fig-012.webp\", \"caption\": \"\", \"page\": 49, \"index\": 12, \"width\": 890, \"height\": 340}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-16-738760-v1/fig-013.webp\", \"caption\": \"\", \"page\": 50, \"index\": 13, \"width\": 572, \"height\": 384}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-16-738760-v1/fig-014.webp\", \"caption\": \"\", \"page\": 51, \"index\": 14, \"width\": 750, \"height\": 750}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-16-738760-v1/fig-015.webp\", \"caption\": \"\", \"page\": 52, \"index\": 15, \"width\": 995, \"height\": 1744}]"
motivation: 非编码调控变异的功能注释不足，需要大规模实验数据来改进预测模型和揭示变异影响规律。
method: "在人类兴奋性神经元中使用lentiMPRA高通量测定>46,000个自然变异对>27,000个候选CRE的等位基因调控效应。"
result: 变异效应率在常见、罕见和单例变异中相似；效应大小由元件活性和序列背景主导；转录因子效应分散而非集中。
conclusion: 提供了大规模功能变异目录和基准，揭示了调控变异的频率非依赖性及组合增强子架构，推动了非编码变异预测模型的发展。
---

## 摘要
疾病相关变异经常位于非编码顺式调控元件（CREs）中，但其功能后果仍知之甚少。我们在人类兴奋性神经元中进行了大规模lentiMPRA实验，量化了524个疾病相关基因附近超过27,000个候选CREs中超过46,000个自然发生变异的影响。这些数据改进了调控变异效应预测，优于最先进的模型。显著等位基因效应在常见、罕见和单例变异中的发生率相当，表明在MPRA可测量的效应范围内，群体频率对每个变异的调控影响信息有限。变异效应的可检测性和幅度主要由包含该变异的调控元件的基线活性和局部序列上下文决定。调控效应分布遍及多个转录因子，而非集中在主调控因子中，这与组合型增强子架构一致。我们建立了一个大规模功能变异目录，并为开发和评估非编码调控变异模型提供了互补的基准和资源。

## Abstract
Disease-associated variants reside frequently in noncoding cis-regulatory elements (CREs), yet their functional consequences remain poorly understood. We performed a large-scale lentiMPRA in human excitatory neurons, quantifying the impact of >46,000 naturally occurring variants across >27,000 candidate CREs near 524 disease-associated genes. These data improved regulatory variant effect predictions beyond state-of-the-art models. Significant allelic effects occurred at comparable rates across common, rare, and singleton variants, demonstrating that, within MPRA-measurable effects, population frequency carries limited information about per-variant regulatory impact. Variant effect detectability and magnitude were governed primarily by baseline activity of the enclosing regulatory element and local sequence context. Regulatory effects were distributed across numerous transcription factors rather than concentrated in master regulators, consistent with a combinatorial enhancer architecture. We establish a large-scale functional variant catalog and provide a complementary benchmark and resource for developing and evaluating models of noncoding regulatory variation.

---

## 论文详细总结（自动生成）

好的，以下是对论文《Massively parallel characterization and predictive modelling of neuronal regulatory variation》的详细中文总结。

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：疾病相关变异大多位于非编码区的顺式调控元件（CREs）中，但我们对这些变异的功能后果知之甚少。具体来说，论文试图回答以下几个关键问题：
    1.  当前的表观基因组注释（如ENCODE SCREEN）在定义细胞类型特异性调控活性方面有多准确？
    2.  等位基因的调控效应与等位基因频率（AF）有何关系？群体频率能否作为调控DNA功能影响的代理指标？
    3.  当前的计算模型（如Enformer、AlphaGenome）在单核苷酸分辨率下捕捉这些效应的效果如何？
    4.  调控环境（如转录因子结合、基线活性、突变类型）如何影响变异效应？
- **整体含义**：通过大规模实验，系统性地揭示神经元中非编码调控变异的分布规律、与群体遗传学的关系以及背后的序列逻辑，并为开发和评估计算模型提供宝贵的基准数据集和资源，从而推动对非编码遗传变异功能注释的进展。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：采用大规模并行报告基因分析（Mega-Parallel Reporter Assay, MPRA）技术，在NGN2诱导的人类兴奋性神经元中，对与疾病相关基因邻近的cCREs及其内自然发生的变异进行高通量功能表征。
- **关键技术细节**：
    1.  **lentiMPRA设计**：
        - **基因选择**：选取了525个与神经、心脏、临床可操作等疾病相关的基因，以及随机基因。
        - **cCRE选择**：从ENCODE SCREEN v3中选取这些基因转录起始位点（TSS）±50kb内的cCREs，共27,209个。
        - **变异选择**：测试了46,374个来自gnomAD v3.1.2的单核苷酸变异（SNVs），覆盖整个等位基因频率谱（从常见到单例）。对于罕见和单例变异，采用了基于Enformer的优先化策略，富集预测有调控影响的变异（70%预测激活，15%预测抑制，15%随机）。
        - **构建体**：将270bp的合成寡核苷酸（包含cCRE序列）克隆到慢病毒报告基因构建体中（带随机条形码）。
    2.  **细胞模型与实验流程**：
        - 将文库转导至NGN2诱导的人类iPSC衍生的兴奋性神经元中（三个生物学重复）。
        - 通过高通量测序定量RNA和DNA中的条形码，计算RNA/DNA比率来衡量调控活性。
        - 使用BCalm软件进行活性量化和等位基因效应（log2FC）的统计检验。
    3.  **计算与建模**：
        - **特征建模**：使用弹性网络（Elastic Net）模型，结合转录因子结合位点（TFBS）、表观基因组注释（如脑cCRE）、进化保守性（phastCons）等特征，预测cCRE活性。
        - **变异效应预测**：
            - 使用预训练模型：Enformer、AlphaGenome、CADD和基于NGN2 ATAC-seq训练的NGN2 chromBPNet。
            - 模型微调：将AlphaGenome的编码器在MPRA数据上进行微调（AlphaGenome Encoder*）。
            - 性能评估：通过ROC-AUC和PR-AUC区分显著与非显著等位基因效应。

## 3. 实验设计：使用的数据集 / 场景、基准、对比方法

- **数据集**：
    - **测试对象**：人类NGN2诱导的兴奋性神经元。
    - **序列来源**：ENCODE SCREEN v3的cCREs。
    - **变异来源**：gnomAD v3.1.2的SNVs。
    - **基因集**：神经、心脏、临床可操作（CAVA）、随机基因。
- **基准（Benchmark）**：
    - **cCRE活性**：与随机化对照序列相比，差异显著的cCREs（dCREs）。
    - **变异效应**：BCalm统计检验FDR < 0.1的等位基因效应（log2FC）。
- **对比方法**：
    - **对于变异效应预测**：
        - Enformer（最大绝对预测变化，平均绝对预测变化）
        - AlphaGenome（平均绝对预测变化）
        - CADD v1.7（PHRED分数）
        - NGN2 chromBPNet（对数倍数变化）
        - AlphaGenome Encoder*（微调后的模型）

## 4. 资源与算力

- 论文中**没有明确说明**所使用的具体GPU型号、数量和训练时长。仅提到计算在柏林卫生研究院（Berlin Institute of Health）的HPC for Research集群、HPC@Charité和吕贝克大学（University of Lübeck）的OMICS HPC集群上执行。

## 5. 实验数量与充分性

- **实验数量**：
    - 测试了**27,209个cCREs**（质量过滤后24,358个）。
    - 测试了**46,374个SNVs**（质量过滤后38,684个）。
    - 包括三组生物学重复，结果高度一致（Pearson r > 0.86）。
    - 包含正负对照（如已验证的脑增强子、随机序列）。
- **充分性评估**：
    - 实验设计**非常充分**。规模巨大，覆盖了广泛的等位基因频率和基因组背景，且包含了多种控制组（正负对照、随机选择vs优先化选择）。
    - 提供了足够的功效来检测等位基因效应，并评估了重复性。
    - 论文对不同分层（如cCRE活性、等位基因频率、突变类型）的分析极为详尽，实验设计严谨。
    - **公平性**：对模型比较做了诚实的限制性说明（如不同模型在训练目标、细胞类型特异性上的差异无法完全独立控制），结论较为客观。

## 6. 论文的主要结论与发现

1.  **调控活性稀疏性**：只有少数ENCODE SCREEN注释的cCREs在NGN2兴奋性神经元中显示出显著活性。脑注释的cCREs更可能具有活性，而非脑注释的cCREs则富集了抑制性活性。
2.  **等位基因频率与功能影响无关**：显著等位基因效应在常见、罕见和单例变异中出现率相当（2.6%）。效应大小与群体频率无显著关系。变异效应的可检测性主要由周围调控元件的基线活性决定，而非等位基因频率。
3.  **组合型转录因子架构**：调控效应分布广泛于多个转录因子，而非集中在少数主调控因子上。等位基因效应与TFBS重叠，但未发现单一TF家族主导。
4.  **模型性能**：
    - 预训练的序列模型（Enformer、AlphaGenome）和细胞类型匹配的chromBPNet在辨别显著等位基因效应方面的性能中等（ROC-AUC ~0.58）。
    - 在活性元件（dCREs）中，所有模型性能提升。
    - 通过将AlphaGenome编码器在MPRA数据上微调，性能显著提升（ROC-AUC ~0.78），表明序列表示可用于MPRA特异性变异效应预测。
5.  **调控上下文决定效应**：基线活性高的元件中，变异更易导致抑制效应；活性低的元件中，变异更易导致激活效应。

## 7. 优点：方法或实验设计上的亮点

- **大规模、系统性**：是目前在神经元中进行的最大的lentiMPRA实验之一，覆盖了广泛的疾病相关基因和等位基因频率。
- **设计新颖**：以疾病相关基因为中心，而非GWAS位点，避免了LD造成的因果模糊，能系统探索顺式调控空间。
- **控制组设置合理**：包含多种正负对照、随机选择与优先化选择，能够有效区分技术噪音和生物学信号。
- **多维度分析**：从元件活性、等位基因效应、TF结合、突变类型、群体频率等多个角度分析，提供了全面的见解。
- **模型比较与资源创建**：不仅比较了现有模型，还通过微调创建了新的模型，并生成了一个可用于基准测试的功能变异目录。
- **诚实的局限性讨论**：对模型比较的维度差异、实验设计偏差（如优先化策略）进行了清晰的限制性说明。

## 8. 不足与局限

- **实验环境**：MPRA在游离的背景下（而非内源性染色质环境）测量转录潜能，无法捕捉长程调控、染色质状态和三维结构对变异的完整影响。
- **设计窗口有限**：只考虑了TSS±50kb内的cCREs，遗漏了更远的调控元件。
- **细胞类型局限**：仅测试了NGN2诱导的兴奋性神经元，结果不能直接泛化到其他神经元类型或非神经元细胞。
- **优先化偏差**：对罕见/单例变异进行了Enformer优先化，虽然为模型评估提供了足够统计功效，但可能在分析频率-效应关系时引入偏差。作者已努力通过随机子集进行校正。
- **TFBS预测精度有限**：使用PWM进行TFBS预测具有较高的假阳性率，而ReMap的覆盖度又不完整。
- **算力信息缺失**：未报告详细的训练资源和能耗，不利于研究重复性和绿色计算评估。
- **数据可用性仍在进行中**：ATAC-seq数据“request available”，部分分析依赖外部资源。

（完）
