---
title: Predictive control of human pancreatic cell fate using a digital model of in vitro differentiation
title_zh: 使用体外分化的数字模型对人类胰腺细胞命运进行预测控制
authors: "Sanchez-Castro, E. E., Ishahak, M., Le, T., Maestas, M. M., Hernandez-Rincon, D. C., Mukherjee, N., Bradley, K., Lu, J., Gale, S. E., Millman, J. R."
date: 2026-07-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.27.721124v2.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 数字分化模型支持原位扰动和虚拟细胞模拟
tldr: "针对干细胞分化为成熟胰岛细胞的瓶颈，本研究整合400,603个细胞的多组学数据，构建了预测性数字模型，解析了从内胚层到胰腺谱系的转录与染色质动态。通过模拟识别出STAT1和ZEB1等新调控因子，并实验验证其功能。该框架提供1,116个模拟结果，可优先选择转录因子和干预窗口，优化体外分化方案。"
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-27-721124-v2/fig-001.webp\", \"caption\": \"\", \"page\": 8, \"index\": 1, \"width\": 1259, \"height\": 183}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-27-721124-v2/fig-002.webp\", \"caption\": \"\", \"page\": 8, \"index\": 2, \"width\": 1259, \"height\": 204}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-27-721124-v2/fig-003.webp\", \"caption\": \"\", \"page\": 8, \"index\": 3, \"width\": 1235, \"height\": 491}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-27-721124-v2/fig-004.webp\", \"caption\": \"\", \"page\": 12, \"index\": 4, \"width\": 1270, \"height\": 1409}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-27-721124-v2/fig-005.webp\", \"caption\": \"\", \"page\": 17, \"index\": 5, \"width\": 1268, \"height\": 880}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-27-721124-v2/fig-006.webp\", \"caption\": \"\", \"page\": 22, \"index\": 6, \"width\": 1282, \"height\": 1249}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-04-27-721124-v2/fig-007.webp\", \"caption\": \"\", \"page\": 27, \"index\": 7, \"width\": 1276, \"height\": 735}]"
motivation: 现有方法难以可控生成成熟干细胞来源胰岛细胞，亟需预测模型指导命运决定。
method: 整合9个原始单细胞多组学及52个公共RNA-seq和ATAC-seq数据集，构建细胞状态特异性基因调控网络数字模型。
result: 发现STAT1驱动外分泌命运，ZEB1动态调控早期内分泌指定及后期血清素能细胞命运。
conclusion: 该预测框架为改进干细胞分化提供实验支持的调控因子和干预时窗优先策略。
---

## 摘要
成熟干细胞衍生胰岛（SC-islets）的可控生成仍然是糖尿病可扩展细胞疗法的障碍。在这里，我们开发了一个预测性数字模型，定义了调控人类SC-islet分化过程中细胞状态特异性调控逻辑。我们整合了来自9个原始单细胞多组学数据集和52个公共单细胞RNA-seq和ATAC-seq数据集的400,603个细胞，涵盖4个细胞系和7种分化方案。该模型解析了转录和染色质可及性动态，同时实现了时间分辨推断和细胞状态特异性基因调控网络的计算扰动。我们识别了从内胚层祖细胞到胰腺外分泌和内分泌谱系轨迹中的调控因子，并提名了新的候选调控因子。在这些候选因子中，我们验证了STAT1作为外分泌驱动因子和ZEB1作为早期内分泌特化及后期脱靶血清素能胰岛细胞命运动态调控因子的先前未报道的作用。这项工作提供了一个经实验支持的预测框架，并包含1,116次模拟的交互式资源，以优先考虑转录因子和干预窗口，从而改进SC-islet分化。

## Abstract
The controlled generation of mature stem cell-derived islets (SC-islets) remains a barrier to scalable cell therapy for diabetes. Here, we develop a predictive digital model defining the cell-state-specific regulatory logic governing fate specification during human SC-islet differentiation. We integrate 400,603 cells from 9 original single-cell multiomic datasets and 52 public single-cell RNA-seq and ATAC-seq datasets across 4 cell lines and 7 differentiation protocols. This model resolves transcriptional and chromatin accessibility dynamics while enabling time-resolved inference and in silico perturbation of cell-state-specific gene regulatory networks. We identify regulators across trajectories from endoderm progenitors to pancreatic exocrine and endocrine lineages, nominating new candidate regulators. Among these candidates, we validate previously unreported roles for STAT1 as an exocrine driver and ZEB1 as a dynamic regulator of early endocrine specification and later off-target serotonergic islet cell fate. This work provides an experimentally supported predictive framework and an interactive resource comprising 1,116 simulations to prioritize transcription factors and intervention windows for refining SC-islet differentiation.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：干细胞衍生胰岛（SC-islets）是糖尿病细胞疗法的重要方向，但现有方案生成的SC-islets不成熟、异质性高，含有未完全特化的内分泌细胞和脱靶细胞群（如血清素能胰岛细胞，SIC）。当前单细胞图谱多为描述性，难以转化为可操作的干预策略。核心瓶颈在于：**无法预测哪些调控因子、在何种细胞状态、于哪个发育窗口进行扰动，能够有效重定向细胞命运**。
- **整体含义**：构建一个整合转录组和染色质可及性的预测性数字模型，能够识别细胞状态特异性的基因调控网络（GRN），并通过计算模拟和实验验证，为优化SC-islet分化提供可测试的假设和优先干预靶点。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：利用时间分辨率的多组学单细胞数据（snMulti-seq）构建分化轨迹，整合公共scRNA-seq和snATAC-seq数据形成大规模数字模型，推断细胞状态特异性GRN，并通过计算模拟转录因子（TF）敲除（KO）预测命运变化，最后用实验验证关键候选因子。
- **关键技术细节**：
  - **数据生成与整合**：使用10x Multiome ATAC+GEX对9个时间点（共33天）的69,535个细胞核进行snMulti-seq测序；整合52个公共数据集，共计400,603个细胞，覆盖4个细胞系和7种分化方案。
  - **多模态整合**：基于MultiVI（深度生成模型）将scRNA-seq、snRNA-seq、snATAC-seq、snMulti-seq数据嵌入共享潜空间，以snMulti-seq数据作为锚点。
  - **轨迹重建**：采用Monocle3计算基因表达伪时间；使用MultiVelo联合建模染色质可及性、未剪接RNA和剪接RNA动力学，定义四种基因状态（primed, coupled-on, decoupled, coupled-off）；利用MOSCOT和CellRank进行概率性细胞命运映射和马尔可夫链随机游走。
  - **GRN推断与计算扰动**：使用CellOracle基于染色质可及性和基序信息构建基础GRN，结合伪时间梯度向量场计算扰动得分（PS，内积），模拟TF KO后对细胞状态转变的影响。
  - **实验验证**：通过CRISPRi（dCas9-KRAB）和药物抑制（ruxolitinib）进行TF敲低，结合qPCR、流式细胞术、激素含量测定和葡萄糖刺激胰岛素分泌（GSIS）评估命运变化。

## 3. 实验设计：数据集、基准、对比方法
- **数据集**：
  - 自产数据：9个时间点的snMulti-seq，共69,535个细胞核。
  - 公共数据：52个scRNA-seq/snRNA-seq/snATAC-seq/snMulti-seq数据集，来自Balboa、Hua、Hogrebe、Rezania、Veres、Weng、Zhu等7种分化方案，共4个细胞系（HUES8等）。
  - 体内对比数据：5个独立scRNA-seq数据集，涵盖人类胎儿胰腺发育第4-19周（共30,084个细胞）。
- **基准（对照）**：已知的胰腺发育调控因子（如GATA4、SOX9、PDX1、NEUROG3、NKX6-1等）作为正对照，验证模型是否恢复已知调控因子。
- **对比方法**：未明确与其他数字模型或GRN推断方法进行系统对比。论文重点在于模型构建和实验验证，而非方法学基准测试。但在snMulti-seq整合时评估了四种整合方法（merge、CCA、RPCA、Harmony），选用基于Seurat v5的流线型整合。

## 4. 资源与算力
- 论文未明确说明使用的GPU型号、数量、训练时长等算力信息。仅提到使用自定义容器化Linux环境（JupyterLab、R、Python）运行分析，代码和容器镜像已公开。分析涉及大规模单细胞数据处理和深度学习模型（MultiVI、CellOracle、MultiVelo），预计需要GPU支持，但未量化。

## 5. 实验数量与充分性
- **实验数量**：
  - 数字模型整合：61个数据集，400,603个细胞。
  - 系统TF KO模拟：共1,116次模拟，覆盖早期分化（222个TF）、外分泌-内分泌分支点（226个TF）、α细胞（227个TF）、δ细胞（227个TF）、β-SIC分支点（214个TF）。
  - 实验验证：对STAT1和ZEB1进行了CRISPRi和药物抑制实验，多个时间点取样（如qPCR、流式细胞术、GSIS、激素含量），每组3-6个生物学重复。
  - 体内外对比：5个胎儿数据集与体外数据整合，差异表达分析。
- **充分性**：实验覆盖了主要分化阶段的关键分支点，验证了模型预测的两个核心候选因子，结果一致。但仅验证了两个TF，其他预测尚未测试。整体实验设计较为充分，但缺乏跨细胞系或跨方案的广泛验证，且未进行大规模CRISPR筛选。

## 6. 论文的主要结论与发现
- **多组学动态**：染色质可及性在分化前期上升（至内分泌诱导窗口），之后逐渐关闭。基因表达、染色质可及性和基序活性可呈现耦合或解耦动态。
- **数字模型恢复已知调控因子**：如GATA4、FOXA2、SOX9、NEUROG3、RFX6、PDX1、NKX6-1、ARX等。
- **新候选因子发现**：
  - **STAT1**：在体内外对比中过表达，计算预测为外分泌驱动因子。实验抑制STAT1（CRISPRi或ruxolitinib）降低外分泌标志物（CAII、CFTR），提高GSIS。
  - **ZEB1**：双重作用——早期（PP阶段）促进内分泌特化（敲低减少CHGA⁺/NKX6-1⁺细胞）；后期（β-SIC分支点）转向促进SIC命运（敲低减少5-HT含量，增加β细胞比例）。
- **体外与胎儿发育差异**：体外分化细胞普遍转录过度激活，尤其是GATA4持续高表达，可能抑制最优分化进程。
- **交互资源**：提供在线平台（islettwin）供用户探索预测结果。

## 7. 优点
- **方法整合度高**：首次将多时间点snMulti-seq与大规模公共数据整合为预测性数字模型，将描述性图谱转化为可测试的调控假设。
- **多模态GRN推断**：同时利用染色质可及性和转录组，推断细胞状态特异性GRN，比单模态方法更准确。
- **系统化计算扰动**：对数百个TF进行模拟KO，定量预测每类TF在特定分支点的影响，优先候选因子。
- **体内外对比**：将体外分化与胎儿发育数据整合，识别差异表达基因，为体外分化缺陷提供解释。
- **实验验证闭环**：两个新候选因子（STAT1、ZEB1）均经独立实验验证，机制合理（ZEB1的动态转换尤其新颖）。
- **全面公开与交互**：代码、数据、在线工具已发布，便于社区利用。

## 8. 不足与局限
- **实验验证覆盖面窄**：仅验证了两个TF（STAT1、ZEB1），其他数百个模拟预测的TF（如ID4、POU2F1、NR2C2、NR0B1等）未经验证，结论推广性受限。
- **缺乏跨细胞系一致性验证**：数字模型整合了多个细胞系，但实验验证仅在HUES8一个细胞系进行，可能无法代表其他干细胞系（如iPSC）的行为。
- **GRN推断的固有局限**：CellOracle等GRN推断方法基于相关性而非因果关系，可能包含假阳性边；模拟KO的扰动得分依赖于GRN质量，未进行大规模CRISPR筛选验证网络准确性。
- **体内外对比的偏差风险**：胎儿数据来自多个研究，可能存在batch效应；体外分化仅采用Hogrebe方案，未覆盖所有整合方案的代表性细胞。
- **未探讨性别/年龄/疾病背景**：未考虑供体性别、年龄或疾病类型对分化潜力的影响。
- **计算资源未说明**：不透明，可能影响可重复性。
- **未定量不同分支点的最优干预窗口分辨率**：仅给出了粗粒度的日期范围（如第9-13天），未进行更精细的时间梯度扰动实验。

（完）
