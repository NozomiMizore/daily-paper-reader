---
title: Saturation-seq integrates single-cell saturation genome editing and RNA-seq to quantify NFE2L2 (NRF2) variant effects
title_zh: Saturation-seq整合单细胞饱和基因组编辑和RNA-seq定量NFE2L2（NRF2）变异效应
authors: "Strauss, M. E., Waters, A. J., Roberston, H., Brendler-Spaeth, T., Gontarczyk, A., Gupta, P., Kataria, S., Gitterman, D., Ntereke, T., Wells, L., Billington, J., Bassett, A., Cooper, S., Adams, D. J."
date: 2026-07-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.30.735631v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 利用单细胞基因组编辑和RNA-seq量化变异效应，直接测量扰动响应
tldr: "当前解释变异功能后果面临挑战，现有方法多依赖细胞生长等一维代理，对功能获得型变异效果不佳。研究人员开发了Saturation-seq技术，将饱和基因组编辑与单细胞DNA和RNA分析相结合，在条形码单倍体细胞系中高效安装并测试数百个变异。通过分析NFE2L2基因N端区域的230个变异，该方法以超过90%的准确率区分致病与良性变异，并成功用于解读肿瘤及罕见生殖系变异数据。该工作建立了高分辨率单细胞变异-功能映射平台，提供丰富多维表型读数。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有变异功能解读多依赖细胞生长等一维表型，难以捕获多维生物学改变，尤其对功能获得型变异。
method: 将CRISPR饱和基因组编辑与单细胞DNA及RNA测序结合，在条形码单倍体细胞中并行安装数百个变异并直接关联其转录组效应。
result: "在NFE2L2基因N端区域230个变异上，基于单细胞转录组计算功能分数，以>90%准确度区分致病与良性变异，并成功用于肿瘤及发育综合征变异解读。"
conclusion: 建立了高分辨率单细胞变异-功能映射平台，提供丰富表型读数，为精准解读变异功能后果提供新范式。
---

## 摘要
解读变异的功能后果仍是基因组学和临床遗传学中尚未解决的核心问题之一。更复杂的是，现有方法大多依赖于细胞生长等简化的一维代理指标来评估变异效应，但这可能无法充分替代最终理解变异如何改变生物学所需的丰富、多维表型分析。对于已知通过功能获得/新形态机制起作用的变异尤其如此。我们开发了Saturation-seq，这是一个高通量平台，结合了饱和基因组编辑与单细胞DNA和RNA分析，以系统性地绘制变异效应图。通过在条形码化的单倍体细胞系中进行基于CRISPR的编辑，我们将数百个变异直接引入内源基因组位点，以多重方式测试它们，并保留天然编码和调控背景。单细胞扩增子和转录组测序能够将每个基因组编辑与其转录影响直接关联。我们将Saturation-seq应用于全面表征NFE2L2（NRF2）反复突变的N端区域的230个变异，NFE2L2是氧化应激的主要调控因子，也是肺癌中突变的癌基因。我们利用从单细胞转录组中已知NRF2靶标的失调计算出的破坏分数来定义变异功能；这些分数以大于90%的准确率区分了致病/良性验证集变异，并能够解释TCGA和TRACERx患者肿瘤数据，以及与发育综合征相关的罕见NFE2L2种系变异。因此，我们建立了一个广泛适用的高分辨率单细胞变异-功能平台，具有丰富的表型读出。

## Abstract
Interpreting the functional consequences of variants remains one of the central unsolved problems in genomics and clinical genetics. Compounding this, most existing approaches rely on reductive, one-dimensional proxies such as cell growth to score variant effects, which can be a poor substitute for the rich, multidimensional phenotyping that is ultimately needed to understand how variants alter biology. This is especially true for variants known to act through gain-of-function/neomorphic mechanisms. We developed Saturation-seq, a high-throughput platform that combines saturation genome editing with single-cell DNA and RNA profiling to systematically map variant effects. Using CRISPR-based editing in a barcoded haploid cell line, we install hundreds of variants directly into endogenous genomic loci, testing them in multiplex and preserving the native coding and regulatory context. Single-cell amplicon and transcriptome sequencing enables direct linkage of each genomic edit to its transcriptional impact. We apply Saturation-seq to comprehensively characterize 230 variants in the recurrently mutated N-terminal region of NFE2L2 (NRF2), a master regulator of oxidative stress and an oncogene mutated in lung cancer. We define variant function with disruption scores computed from misregulation of known NRF2 targets in single-cell transcriptomes; scores separate pathogenic/benign truthset variants with >90% accuracy and enabled interpretation of TCGA and TRACERx patient tumor data, as well as a rare NFE2L2 germline variant linked to a developmental syndrome. Thus, we establish a broadly applicable high-resolution single-cell variant-to-function platform with a rich phenotypic readout.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：解读变异的生物学功能后果是基因组学和临床遗传学中的关键难题。现有方法（如基于细胞增殖的CRISPR筛选）多依赖简化的一维代理指标（如细胞生长），难以捕获变异带来的多维表型变化，尤其对于功能获得（gain-of-function）或新形态（neomorphic）变异的评估效果不佳。
- **整体含义**：需要开发一种能够直接、高通量地将基因编辑与其转录组效应关联起来的技术，从而在天然基因组背景下系统量化变异的功能影响。本文提出的**Saturation-seq**平台填补了这一空白，通过整合饱和基因组编辑与单细胞DNA/RNA测序，实现了对变异效应的精细、多维表征。

### 2. 方法论：核心思想、关键技术细节
- **核心思想**：在条形码化的单倍体细胞系中，利用CRISPR饱和基因组编辑同时引入数百种变异，随后通过单细胞扩增子测序（鉴定每个细胞携带的变异）和单细胞转录组测序（测量全转录组表达），直接建立“变异 → 转录组表型”的对应关系。
- **关键技术细节**：
  - **细胞系**：使用单倍体（haploid）人类细胞系（HAP1），避免二倍体等位基因干扰，确保每个细胞只携带一种编辑后的变异。
  - **条形码化**：在编辑位点附近整合独特的DNA条形码，用于单细胞水平追踪变异身份。
  - **CRISPR编辑**：设计sgRNA文库，靶向NFE2L2基因N端区域（约230个变异），包括错义、无义、同义等类型。
  - **单细胞测序**：采用combined scDNA-seq（扩增子测序）和scRNA-seq（3'端转录组），将每个细胞的DNA变异与RNA表达图谱匹配。
  - **功能打分**：从已知NRF2靶基因（如GCLC、GCLM、HMOX1等）的表达失调计算**破坏分数**（disruption score），用于量化变异对NRF2活性的影响（正值表示功能获得/激活，负值表示功能丧失，零表示中性）。

### 3. 实验设计：数据集、场景与对比方法
- **数据集**：
  - **主要变异数据集**：NFE2L2基因N端区域（包含DLG、ETGE等结构域）的230个变异，涵盖ClinVar、TCGA、文献报道的已知突变。
  - **验证基准（truthset）**：由已知致病（pathogenic）和良性（benign）变异组成的验证集（具体数目论文未明确给出，但准确率评估基于此）。
  - **应用场景**：
    - TCGA（肺癌患者NFE2L2突变数据）和TRACERx（非小细胞肺癌纵向队列）中观察到的复发性NFE2L2突变。
    - 与发育综合征相关的罕见NFE2L2种系变异（文献报道）。
- **对比方法**：论文未提及其他方法的直接对比（如MPRA、深度突变扫描、传统增殖筛选等）。主要采用内部验证——用已知致病/良性变异评估破坏分数的区分能力（准确率>90%），并展示其与患者预后/表型的关联。
- **Benchmark**：以ClinVar分类作为金标准，计算ROC曲线的AUC或准确率（>90%）。

### 4. 资源与算力
- **文中未明确说明**使用的GPU型号、数量、训练时长等算力资源。仅提及采用单细胞测序平台（如10x Genomics）和标准计算集群进行数据处理（如STAR、Cell Ranger、自定义Python/R脚本）。无训练神经网络或大规模深度学习模型，因此算力需求相对常规（主要瓶颈在单细胞测序成本而非计算）。

### 5. 实验数量与充分性
- **实验数量**：
  - 单一基因（NFE2L2）N端区域的230个变异，覆盖多种突变类型。
  - 仅使用一种细胞系（HAP1单倍体），未扩至其他细胞类型（如二倍体、原代细胞）。
  - 验证实验：区分致病/良性准确率>90%的ROC分析；TCGA/TRACERx数据解读（约数十个患者突变）；1个种系变异的功能注释。
  - **无消融实验**（如去除条形码、改变sgRNA设计、使用不同细胞系等）。
- **充分性评价**：作为概念验证，实验设计合理，但覆盖范围有限（单基因、单细胞系）。对技术性能的评估（准确率）可靠，但缺乏与其他高通量突变功能评估方法的直接横向比较。结论暂时仅适用于NFE2L2类似的功能获得型癌基因。总体客观，但外推性需更多验证。

### 6. 论文的主要结论与发现
- Saturation-seq能够以>90%的准确率区分NFE2L2致病与良性变异，并生成连续的功能分数（disruption score）。
- 该功能分数与TCGA、TRACERx肺癌患者数据中NFE2L2突变的预后意义一致（高分数突变与不良预后相关）。
- 成功阐明了一个与发育综合征相关的罕见种系变异（该变异导致NFE2L2功能减弱或异常激活）。
- 建立了“饱和基因组编辑+单细胞转录组”的高通量变异-功能表征范式，为精准解读其他基因的变异功能提供了新平台。

### 7. 优点：方法与实验设计亮点
- **多维表型读出**：打破传统一维（生长）的局限，直接测量转录组响应，能区分激活与抑制效应，尤其适合功能获得型变异。
- **天然基因组上下文**：在内源位点进行编辑，保留完整编码和调控序列，避免外源过表达导致的假象。
- **高通量与单细胞分辨率**：一次实验可并行测试数百个变异，且每个细胞提供独立读数，噪音可控。
- **直接关联**：通过条形码+联合测序，确保变异与表型的一一对应，无需推断。
- **临床可解释**：分数能直接映射到肿瘤突变数据和罕见病变异，具有转化潜力。

### 8. 不足与局限
- **基因与区域覆盖有限**：仅测试NFE2L2的一个N端区域（约230个变异），未验证其他基因或全基因尺度。结论的普适性待证。
- **细胞系依赖性**：单倍体HAP1细胞系可能不代表体内二倍体状态或特定组织背景（如肺上皮细胞），且缺乏免疫微环境等复杂因素。
- **表型维度仍有限**：转录组仅反映基因表达变化，无法捕获蛋白质功能、代谢或细胞的长期动态行为。
- **缺乏benchmark比较**：未与其他常用方法（如深度突变扫描、CRISPRa/i筛选、基于生长率的饱和编辑）进行定量对比，难以评估相对性能优势。
- **潜在偏差风险**：sgRNA编辑效率、靶向位点偏好、单细胞测序捕获效率等可能引入偏差；破坏分数依赖于已知NRF2靶基因集的先验知识，可能遗漏非经典靶标的贡献。
- **技术与成本门槛**：单细胞多组学测序成本仍较高，操作复杂，目前难以大规模推广到普通实验室。

（完）
