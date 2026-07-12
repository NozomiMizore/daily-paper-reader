---
title: "TMO: ASYMMETRIC CROSS-MODAL ATTENTION FOR LEARNING CELL-STATE-DEPENDENT REGULATORY LAGS FROM SINGLE-CELL MULTIOMIC DATA"
title_zh: TMO：利用不对称跨模态注意力从单细胞多组学数据中学习细胞状态依赖的调控时滞
authors: "Lopez-Delgado, P. A., Delgado-Carlo, M. M."
date: 2026-07-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.08.730880v2.full.pdf"
tags: ["query:virtual-cell"]
score: 7.0
evidence: 学习细胞状态依赖的调控动态，与虚拟细胞模型相关
tldr: 现有单细胞多组学模型对称处理染色质和转录，忽略方向性且仅估计全局时滞，无法捕捉细胞状态依赖的调控动态。本文提出TMO，通过非对称跨模态注意力和滑动窗口相关先验，学习有符号的细胞状态条件调控时滞。在四个10x Multiome数据集上，时滞一致性评分达0.988-0.999，远超对称基线（<0.11），且ChIP-seq和Perturb-seq验证了生物学有效性。TMO是首个将调控时滞作为可学习参数并编码方向的框架，为研究发育和疾病中的时序调控提供了可扩展、可解释的开源工具。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-08-730880-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1370, \"height\": 1004, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-08-730880-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 832, \"height\": 1020, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-08-730880-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1418, \"height\": 935, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-08-730880-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1334, \"height\": 934, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-08-730880-v2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1263, \"height\": 758, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-08-730880-v2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1391, \"height\": 1359, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-08-730880-v2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1285, \"height\": 327, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-08-730880-v2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1584, \"height\": 327, \"label\": \"Table\"}]"
motivation: 现有对称模型忽略染色质到转录的方向性，且仅估计全局时滞，无法捕捉细胞状态依赖的动态调控。
method: 提出TMO，使用非对称跨模态注意力将RNA和ATAC投影为50个潜在组件，通过两个Transformer通道学习有符号的细胞状态条件时序滞后。
result: 在4个数据集上LCS达0.988-0.999（对称基线<0.11），ChIP-seq验证目标基因显著分离，Perturb-seq验证因果性，揭示双相基因程序。
conclusion: TMO是首个可学习、细胞状态条件且架构编码的调控时滞方法，可扩展、可解释，为研究发育和疾病中的调控时序提供有力工具。
---

## 摘要
背景：单细胞多组学技术同时测量染色质可及性（ATAC）和基因表达（RNA），为研究分化过程中调控事件的时间顺序提供了独特视角。然而，大多数计算模型对称处理这两种模态，忽略了染色质与转录之间的方向性关系，且现有的时滞感知方法为每个基因估计单一的全局时滞，无法捕捉细胞状态依赖的动态变化。

方法与结果：我们提出了时间多组学（Temporal Multi-Omics, TMO）框架，通过不对称跨模态注意力学习带符号的、细胞状态条件的调控时滞（{Delta}{tau}）。TMO将RNA和ATAC分别投影到50个潜在成分，将每个细胞标记为100个令牌的序列，并使用双通道Transformer，其中数据驱动的时滞先验（基于滑动窗口互相关函数）直接不对称地偏置注意力。在四个独立的10x Multiome数据集（小鼠大脑、人类大脑、小鼠肾脏、人类PBMC）上，不对称模型的时滞一致性得分（LCS）达到0.988-0.999，而结构相同的对称基线仅为0.048-0.108。分层80/20留出实验表明，学习到的成分-时滞排序可泛化到未见细胞（留出LCS 0.85-0.99）。聚类后的{Delta}{tau}热图显示在早期假时间存在正{Delta}{tau}（ATAC主导的启动），在晚期假时间存在负{Delta}{tau}（RNA主导的活动依赖性调控）；ATAC-RNA相关性热图呈现U形模式，指示发育解耦。具有最正{Delta}{tau}的成分富集于染色质组织和干细胞分化（FDR < 0.05），而最负{Delta}{tau}的成分富集于突触信号和免疫激活。从时滞预测器中移除细胞状态信息会降低LCS并破坏每成分的时间动态（所有四个组织中KS检验p ≤ 0.039），证明TMO的动态时滞模式依赖于细胞状态条件。四个转录因子（PAX5、Pax6、ASCL1、Hnf4）的独立ChIP-seq验证确认了目标基因与表达匹配背景之间高度显著的分离（所有情况p < 10^-4）。两个Multiome Perturb-seq筛选提供了因果验证：SMARCB1敲除显示出方向性趋势（1.5倍目标偏移，p = 0.056，n = 147个扰动细胞），SMARCE1敲除达到统计学显著性（p = 0.0089，n = 3,394个扰动细胞）。基因水平互相关独立验证了原始数据中存在调控时滞信号，TMO还识别出罕见的、统计显著的双相基因程序，其调控方向在假时间上反转。

结论：TMO是首个将调控时滞作为可学习、细胞状态条件且架构编码参数的方法。它具有可扩展性、可解释性且开源，为研究发育、疾病和扰动筛选中的调控时序提供了强大工具。

亮点：
- TMO从配对ATAC+RNA数据中学习带符号的、细胞状态条件的调控时滞（{Delta}{tau}）。
- 不对称跨模态注意力使模型偏向调控方向（ATAC领先RNA或RNA领先ATAC）。
- 不对称模型的时滞一致性得分>0.98，远优于对称基线（<0.11）。
- 所有四个组织的分层80/20留出实验表明，学习到的成分-时滞排序可迁移到未见细胞（留出LCS 0.85-0.99）。
- Perturb-seq筛选检测到扰动诱导的调控时序变化：SMARCB1敲除显示方向性趋势（p = 0.056），SMARCE1敲除达到显著性（p = 0.0089），证明因果相关性。
- 四个转录因子和组织的独立ChIP-seq验证确认TMO衍生的时滞可区分物理结合基因与表达匹配背景（所有情况p < 10^-4）。
- 从LagMLP中移除细胞嵌入会导致LCS大幅下降并破坏每成分时间动态，证明TMO的细胞状态条件化至关重要。
- TMO开源、可扩展，可直接应用于任何10x Multiome数据集。
- 基因水平互相关确认时滞信号是数据固有的，且其变异性是TMO去噪成分谱的3.7-4.7倍。
- TMO识别出统计显著的双相基因程序，其调控方向在假时间上反转，这是现有标量方法无法触及的新动态。

1. 图1：图形摘要

O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=141 SRC="FIGDIR/small/730880v2_fig1.gif" ALT="图1">
查看大图（38K）：
org.highwire.dtl.DTLVardef@23fe6dorg.highwire.dtl.DTLVardef@114d55dorg.highwire.dtl.DTLVardef@c3ed05org.highwire.dtl.DTLVardef@fe1d19_HPS_FORMAT_FIGEXP  M_FIG O_FLOATNO图1:C_FLOATNO 图形摘要 | TMO - 时间多组学。

TMO在双通道Transformer中使用不对称跨模态注意力，从配对单细胞多组学数据中学习染色质可及性（ATAC）与基因表达（RNA）之间的带符号、细胞状态条件的调控时滞（{Delta}{tau}）。源自滑动窗口互相关函数的数据驱动时滞先验偏置ATAC到RNA的注意力，使模型能够捕捉分化早期的ATAC主导启动（正{Delta}{tau}，红色）和分化晚期的RNA主导活动依赖性调控（负{Delta}{tau}，蓝色）。在四个组织中，不对称模型的时滞一致性得分（LCS）为0.988-0.999，而对称基线降至<0.11。独立ChIP-seq和Perturb-seq验证确认学习到的时滞反映真实的转录因子结合并对遗传扰动做出响应。TMO开源、可扩展，可作为类似Scanpy的Python包（tmopy）使用。使用BioRender制作。

C_FIG

## Abstract
BackgroundSingle-cell multi-omics technologies simultaneously measure chromatin accessibility (ATAC) and gene expression (RNA), providing a unique window into the temporal ordering of regulatory events during differentiation. However, most computational models treat the two modalities symmetrically, ignoring the directional relationship between chromatin and transcription, and existing lag-aware methods estimate a single global lag per gene, failing to capture cell-state-dependent dynamics.

Methods and ResultsWe introduce Temporal Multi-Omics (TMO), a deep learning framework that learns signed, cell-state-conditional regulatory lags ({Delta}{tau}) using asymmetric cross-modal attention. TMO projects RNA and ATAC into 50 latent components each, tokenises each cell as a sequence of 100 tokens, and uses a two-pass transformer in which a data-driven lag prior - derived from a sliding-window cross-correlation function - directly biases attention asymmetrically. On four independent 10x Multiome datasets (mouse brain, human brain, mouse kidney, human PBMC), the asymmetric model achieves Lag Concordance Scores (LCS) of 0.988-0.999, compared to 0.048-0.108 for an architecturally identical symmetric baseline. A stratified 80/20 held-out experiment confirms that the learned component-lag ordering generalises to unseen cells (held-out LCS 0.85-0.99). Clustered {Delta}{tau} heatmaps show positive {Delta}{tau} (ATAC-led priming) in early pseudotime and negative {Delta}{tau} (RNA-led, activity-dependent regulation) in late pseudotime; the ATAC-RNA correlation heatmap exhibits a U-shaped pattern indicative of developmental decoupling. Components with the most positive {Delta}{tau} are enriched for chromatin organization and stem cell differentiation (FDR < 0.05), while those with the most negative {Delta}{tau} are enriched for synaptic signalling and immune activation. Ablating the cell-state information from the lag predictor reduces the LCS and collapses per-component temporal dynamics (KS p [&le;] 0.039 in all four tissues), proving that TMOs dynamic lag patterns depend on cell-state conditioning. Independent ChIP-seq validation for four transcription factors (PAX5, Pax6, ASCL1, Hnf4) confirms highly significant separation between target genes and expression-matched background (p < 10-4 in all cases). Two Multiome Perturb-seq screens provide causal validation: SMARCB1 knockout shows a directional trend (1.5-fold target shift, p = 0.056, n = 147 perturbed cells), and SMARCE1 knockout reaches statistical significance (p = 0.0089, n = 3,394 perturbed cells). Gene-level cross-correlation independently validates that the regulatory lag signal is present in the raw data, and TMO further identifies rare, statistically significant biphasic gene programs where the regulatory direction reverses across pseudotime.

ConclusionsTMO is the first method to make regulatory lag a learnable, cell-state-conditional, and architecturally encoded parameter. It is scalable, interpretable, and open-source, providing a powerful tool for studying regulatory timing in development, disease, and perturbation screens.

HighlightsO_LITMO learns signed, cell-state-conditional regulatory lags ({Delta}{tau}) from paired ATAC+RNA data.
C_LIO_LIAsymmetric cross-modal attention biases the model towards the direction of regulation (ATAC leads RNA or RNA leads ATAC).
C_LIO_LIThe asymmetric model achieves Lag Concordance Scores > 0.98, far outperforming a symmetric baseline (< 0.11).
C_LIO_LIStratified 80/20 held-out experiments across all four tissues show that the learned component-lag ordering transfers to unseen cells (held-out LCS 0.85-0.99).
C_LIO_LIPerturb-seq screening detects perturbation-induced shifts in regulatory timing: SMARCB1 knockout shows a directional trend (p = 0.056), and SMARCE1 knockout reaches significance (p = 0.0089), demonstrating causal relevance.
C_LIO_LIIndependent ChIP-seq validation across four transcription factors and tissues confirms that TMO-derived lags distinguish physically bound genes from expression-matched background (p < 10-4 in all cases).
C_LIO_LIRemoving the cell embedding from the LagMLP causes a substantial drop in LCS and collapses the per-component temporal dynamics, proving that TMOs cell-state conditioning is essential.
C_LIO_LITMO is open-source, scalable, and ready for application to any 10x Multiome dataset.
C_LIO_LIGene-level cross-correlation confirms the lag signal is intrinsic to the data and is 3.7-4.7x more variable than TMOs denoised component profiles.
C_LIO_LITMO identifies statistically significant biphasic gene programs whose regulatory direction reverses across pseudotime, a new dynamic inaccessible to existing scalar methods.
C_LI

1. Figure 1: Graphical Abstract

O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=141 SRC="FIGDIR/small/730880v2_fig1.gif" ALT="Figure 1">
View larger version (38K):
org.highwire.dtl.DTLVardef@23fe6dorg.highwire.dtl.DTLVardef@114d55dorg.highwire.dtl.DTLVardef@c3ed05org.highwire.dtl.DTLVardef@fe1d19_HPS_FORMAT_FIGEXP  M_FIG O_FLOATNOFigure 1:C_FLOATNO Graphical Abstract | TMO - Temporal Multi-Omics.

TMO uses asymmetric cross-modal attention in a two-pass transformer to learn signed, cell-state-conditional regulatory lags ({Delta}{tau}) between chromatin accessibility (ATAC) and gene expression (RNA) from paired single-cell multi-omic data. A data-driven lag prior derived from a sliding-window cross-correlation function biases ATAC-to-RNA attention, enabling the model to capture ATAC-led priming (positive {Delta}{tau}, red) early in differentiation and RNA-led, activity-dependent regulation (negative {Delta}{tau}, blue) late in differentiation. Across four tissues, the asymmetric model achieves Lag Concordance Scores (LCS) of 0.988-0.999, while a symmetric baseline collapses to <0.11. Independent ChIP-seq and Perturb-seq validations confirm that the learned lags reflect genuine transcription factor binding and respond to genetic perturbations. TMO is open-source, scalable, and available as a Scanpy-like Python package (tmopy). Made with BioRender.

C_FIG