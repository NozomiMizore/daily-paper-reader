---
title: Isoform-level resolution in single-cell CRISPR screens reveals hidden functional consequences of gene perturbation
title_zh: 单细胞CRISPR筛选中的异构体水平分辨率揭示基因扰动的隐藏功能后果
authors: "Andrews, N., Gleeson, J., Panten, J., Oling, S., Lundqvist, S., Lappalainen, T."
date: 2026-07-10
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.09.737410v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 单细胞CRISPR扰动筛选的异构体水平分析
tldr: 传统单细胞CRISPR筛选仅关注基因水平，忽略异构体变化。本研究比较两种建库方法与三种测序平台，发现长读长测序可有效捕获异构体水平改变，而短读长和Parse方法存在局限。通过CRISPRi敲低DDX6、GEMIN5、GFI1B，发现GEMIN5敲低引发广泛剪接变化，基因水平分析无法察觉。研究提供异构体水平筛选的实用框架，指出长读长测序是全面解读基因功能的关键。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737410-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1675, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737410-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1655, \"height\": 1704, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737410-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1625, \"height\": 1512, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737410-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1600, \"height\": 1132, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737410-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1637, \"height\": 1587, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737410-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1325, \"height\": 1199, \"label\": \"Figure\"}]"
motivation: 现有单细胞CRISPR筛选方法忽略异构体水平的功能后果，需评估不同建库和测序方法对异构体捕获的能力。
method: 比较10x Genomics和Parse Biosciences建库结合Illumina短读长、Oxford Nanopore和PacBio长读长测序，对K562细胞进行CRISPRi敲低DDX6、GEMIN5、GFI1B。
result: "长读长测序一致检测异构体变化，需约2100万reads达80%饱和；GEMIN5敲低导致最显著剪接变化，基因水平无差异。"
conclusion: 异构体水平分析揭示基因水平忽视的功能后果，长读长测序是大规模筛选的必需工具。
---

## 摘要
单细胞CRISPR筛选使得对基因功能的系统性研究成为可能，但研究主要关注基因层面的效应，忽视了转录复杂性和异构体使用。能够捕获剪接和异构体使用的方法已经出现，包括长读长测序和替代文库制备策略，但它们在大规模扰动筛选中的适用性尚未得到评估。我们比较了两种文库制备方法（10x Genomics和Parse Biosciences），结合Illumina短读长、Oxford Nanopore和PacBio长读长测序，应用CRISPRi沉默K562细胞中三个具有不同调控作用的基因（DDX6、GEMIN5、GFI1B）。虽然短读长方法检测到一些剪接事件，但只有长读长测序一致地捕获了异构体水平的变化。尽管Parse提供了均匀的转录本覆盖，但我们观察到强烈的内含子读段富集，限制了其在剪接分析中的效用。长读长方法的主要限制是测序深度：单次扰动中需要约2100万读段才能达到剪接事件80%的饱和度。值得注意的是，GEMIN5敲低仅产生适度的差异表达，但引起了最广泛的剪接变化，这种效应在基因水平分析中不可见，突显了异构体水平筛选的价值。我们为单细胞CRISPR筛选中的异构体水平分析提供了一个实用框架，指出了当前的能力和局限性。随着扰动研究规模的扩大，长读长测序对于全面的功能解释、捕获基因水平分析遗漏的生物学信息将至关重要。

## Abstract
Single-cell CRISPR screens have enabled systematic investigation of gene function, but studies have largely focused on gene-level effects, overlooking transcriptional complexity and isoform usage. Methods capable of capturing splicing and isoform usage have emerged, including long-read sequencing and alternative library preparation strategies, but their suitability for large-scale perturbation screens remains unevaluated. We compare two library preparation methods (10x Genomics and Parse Biosciences) across Illumina short-read, Oxford Nanopore, and PacBio long-read sequencing, applying CRISPRi to silence three genes with distinct regulatory roles (DDX6, GEMIN5, GFI1B) in K562 cells. While short-read methods detected some splicing events, only long-read sequencing consistently captured isoform-level changes. Although Parse provided even transcript coverage, we observed strong intronic read enrichment, limiting its utility for splicing analysis. The primary constraint of long-read approaches was sequencing depth: ~21 million reads are needed for 80% saturation of splicing events in a single perturbation. Notably, GEMIN5 knockdown produced only modest differential expression but the most extensive splicing changes, an effect invisible to gene-level analysis, underscoring the value of isoform-level screens. We provide a practical framework for isoform-level analysis in single-cell CRISPR screens, identifying current capabilities and limitations. As perturbation studies scale, long-read sequencing will be essential for comprehensive functional interpretation, capturing biology missed by gene-level analysis.

---

## 论文详细总结（自动生成）

# 论文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：单细胞CRISPR筛选已广泛应用于基因功能研究，但现有方法主要聚焦于**基因表达水平**的变化，忽视了**转录本异构体（isoform）的使用**和**可变剪接**的调控。许多基因（如剪接调控因子）的功能后果可能主要体现在异构体水平，而非基因总量变化。
- **背景**：目前已有长读长测序（ONT、PacBio）和替代文库制备方法（如Parse Biosciences的随机六聚体引物）能够捕获剪接和异构体信息，但这些方法在大规模扰动筛选中的适用性尚未系统评估。
- **整体含义**：本研究系统比较了两种单细胞建库方法（10x Genomics 5'端法、Parse Biosciences Evercode）结合三种测序技术（Illumina短读长、Oxford Nanopore长读长、PacBio长读长）在CRISPRi扰动筛选中检测异构体变化的能力，揭示了**基因水平分析会遗漏重要的功能后果**，并提出了异构体水平筛选的实用框架。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过对比不同建库和测序平台在CRISPRi扰动下的基因表达与异构体使用检测性能，评估它们对剪接和异构体变化的捕获能力，并利用长读长数据结合蛋白结构预测模型分析异构体转换的功能影响。
- **关键技术细节**：
  - **CRISPRi系统**：使用表达dCas9-KRAB-MeCP2的K562细胞，通过慢病毒转导sgRNA敲低三个靶基因（DDX6、GEMIN5、GFI1B）。
  - **10x Genomics文库**：采用5'端捕获，逆转录和cDNA扩增步骤延长以增强全长转录本扩增。测序分为三路：Illumina短读长（SR-10x）、PacBio长读长（LR-PB）、Oxford Nanopore长读长（LR-ONT）。
  - **Parse Biosciences文库**：采用固定/透化后的组合条形码方法，使用随机六聚体引物和oligo-dT引物进行全转录组分析（WT Kit v3），同时使用CRISPR Detect试剂盒捕获gRNA。
  - **数据分析流程**：
    - 10x短读长数据：Cell Ranger v9.0.1比对至GRCh38.p14 + Gencode v48。
    - ONT数据：nf-core/scnanoseq v1.2.1处理，使用Cell Ranger识别的细胞条形码白名单。
    - PacBio数据：Iso-Seq单细胞工作流v4.3.0，skera分段，pigeon流程进行转录本映射、合并和分类。
    - Parse数据：split-pipe v1.6.4处理。
  - **异构体分析工具**：LeafCutter（短读长和长读长通用，检测剪接事件）、FLAIR v3（仅长读长，用于差异异构体表达、差异异构体使用DIU和可变剪接事件ASE）。
  - **功能影响预测**：通过BioGRID和STRING获取蛋白互作信息，使用Boltz-2（开源蛋白结构预测模型）预测不同异构体与其互作伙伴的复合物结构，计算界面预测TM分数（ipTM）变化，以评估异构体转换导致的互作增益或损失。

## 3. 实验设计：数据集、场景、基准和方法对比

- **细胞系与扰动**：K562细胞（人慢性髓系白血病），CRISPRi敲低三个基因：DDX6（mRNA降解调控）、GEMIN5（剪接调控）、GFI1B（转录抑制）。每个基因设计2-3个有效sgRNA，另加5个非靶向对照（NTC）sgRNA。
- **数据集**：
  - 同一批CRISPRi细胞分为两部分：
    - 10x Genomics建库 → 分别进行Illumina短读长（SR-10x）、PacBio长读长（LR-PB）、Oxford Nanopore长读长（LR-ONT）测序。
    - Parse Biosciences建库 → 仅进行Illumina短读长测序（SR-Parse）。
  - 最终分析细胞数：10x文库2491个细胞，Parse文库574个细胞（过滤后）。
- **基准（Benchmark）**：
  - **基因水平**：比较各平台基因检测灵敏度、基因体覆盖、转录本长度分布、差异表达（DESeq2）检测能力。
  - **异构体水平**：比较各平台测试性剪接事件数量、剪接事件沿基因体分布、差异剪接事件（LeafCutter/FLAIR）数量。
  - **统计功效**：使用powsimR比较短读长平台的差异表达检测功效；通过下采样估计长读长平台所需测序深度。
- **对比方法**：SR-10x vs SR-Parse vs LR-PB vs LR-ONT（10x同源细胞三技术 + Parse异源建库）。
- **消融/补充分析**：
  - 比较Parse中随机六聚体引物与oligo-dT引物对转录本覆盖的影响。
  - 比较核/胞浆RNA富集程度（利用ENCODE K562细胞分级数据）。
  - 分析GEMIN5敲低所需测序深度饱和曲线（使用两个ONT flow cell共232M reads）。
  - 对AK2基因的异构体转换进行AlphaFold3蛋白复合物结构预测。

## 4. 资源与算力

- **文中未明确提及**使用的GPU型号、数量或训练时长。对于蛋白结构预测部分（Boltz-2和AlphaFold3），提到了使用Boltz-2进行3,414个isoform-partner对的复合物结构预测（3次循环、30步扩散、每对1个扩散样本），以及AlphaFold3用于AK2-AIFM1建模，但未说明具体硬件配置或耗时。数据分析部分提到了使用UPPMAX（乌普萨拉多学科先进计算科学中心）计算基础设施，但无详细算力报告。

## 5. 实验数量与充分性

- **数量**：
  - 主要比较4个数据集（SR-10x、SR-Parse、LR-PB、LR-ONT-1个flow cell），另对ONT增加了第二个flow cell用于深度分析。
  - 基因表达分析：DESeq2 + TRADE用于3个扰动（每扰动3个伪重复）。
  - 剪接分析：LeafCutter（4个数据集），FLAIR（仅限于长读长数据）。
  - 蛋白互作分析：116个基因的蛋白质编码异构体切换，预测3,414对isoform-partner，获得1,650个完整配对比较。
  - 深度饱和曲线：对GEMIN5进行下采样（5个随机种子，1M至最大深度）。
- **充分性**：
  - **实验覆盖较全面**：涵盖了主流单细胞建库方法和三种测序技术，直接比较了同一10x细胞样本在不同测序平台的表现，排除了生物学变异。
  - **公平性**：长读长测序深度明显低于短读长（约119M vs 312M reads），但作者通过下采样分析控制了深度影响。
  - **局限性**：仅测试了K562细胞系和三个基因的CRISPRi扰动，结论的泛化性有限。Parse仅在短读长中测试（未做长读长测序），无法评估Parse长读长的表现。

## 6. 论文的主要结论与发现

1. **文库制备是比测序技术更强的转录组变异驱动因素**：10x来源的三个数据集（SR-10x、LR-PB、LR-ONT）之间基因表达高度一致（r>0.88），而Parse（SR-Parse）与所有10x数据集的相关性较弱（r=0.52-0.62）。
2. **Parse的细胞透化导致核RNA富集**：Parse文库中50%以上蛋白编码读段来自内含子，lncRNA读段中>60%为内含子，严重限制了剪接连接检测（<25%读段含剪接连接，而10x长读长>80%）。
3. **长读长测序是捕获异构体变化的关键**：尽管短读长方法可检测一些剪接事件（LeafCutter），只有长读长方法（PacBio和ONT）能一致地捕获差异异构体使用（FLAIR）。PacBio的检测敏感性高于ONT（同一flow cell下）。
4. **GEMIN5敲低的效应在基因水平几乎不可见**：GEMIN5的差异表达最弱，但剪接变化最广泛（主要外显子跳跃），体现了异构体水平分析的必要性。
5. **实用深度估计**：对GEMIN5扰动，约需2100万读段（ΔIF>0.05）或1200万读段（ΔIF>0.1）才能达到80%的差异异构体使用检测饱和度。
6. **异构体转换导致蛋白互作变化**：通过Boltz-2预测，116个基因中391对isoform-partner出现显著的互作增益（197对）或丧失（194对）。AK2典型案例表明：GEMIN5敲低导致AK2从全长异构体（与AIFM1结合）切换至缺失外显子6的异构体（无法结合AIFM1），从而改变线粒体功能。

## 7. 优点：方法或实验设计上的亮点

- **系统性的多平台比较**：在同一扰动实验中比较两种建库方法和三种测序平台，控制了大量干扰变量。
- **直接评估生物学相关变化**：不同于单纯的技术指标比较，本研究直接评估各平台检测CRISPRi扰动后果的能力，更具实际指导意义。
- **深度与饱和度的量化**：通过下采样实验给出了具体深度要求，为研究设计提供了实用性建议。
- **从异构体到蛋白质功能的完整分析流程**：将差异异构体使用与蛋白结构预测相结合（Boltz-2 + AlphaFold3），使扰动后果的解释从转录水平延伸至功能后果。
- **揭示“基因水平盲点”**：通过GEMIN5案例，清晰展示了基因水平分析会遗漏的剪接调控效应，对领域有警示作用。

## 8. 不足与局限

- **泛化性有限**：仅使用K562细胞系和三个基因的CRISPRi扰动，结果可能不适用于其他细胞类型、其他扰动方式（如CRISPRa、CRISPRko）或更复杂的扰动。
- **Parse未作长读长测序**：由于只测试了Parse+短读长，无法评估Parse+长读长的可能表现。
- **测序深度不对称**：短读长深度远高于长读长，虽然通过下采样控制，但长读长的潜在更高深度可能进一步提升表现。
- **长读长错误率影响**：ONT的错误率可能影响剪接连接检测，作者通过LeafCutter和FLAIR两种工具部分缓解，但未进行系统性校正。
- **蛋白互作预测存在不确定性**：Boltz-2和AlphaFold3预测结果未通过实验验证，仅提供假设。
- **未评估gRNA脱靶效应**：CRISPRi的脱靶可能性未被讨论或控制。
- **读长限制**：长读长测序的通量仍显著低于短读长，限制了大规模筛选的可行性。

（完）
