---
title: Identifying cancer cell-state transitions from multimodal single-cell data
title_zh: 从多模态单细胞数据中识别癌细胞状态转变
authors: "Baselli, G. A., Alekseenko, A., Liano-Pons, J., Sinanis, L., Rrapaj, E., Arsenian-Henriksson, M., Pelechano, V."
date: 2026-07-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.02.708945v2.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 利用多模态单细胞数据识别癌症细胞状态转变，与扰动响应动态相关
tldr: 癌症细胞表型可塑性导致治疗耐药，但状态转换的瞬时性使其难以研究。该研究提出一种单细胞框架，利用mRNA与表面蛋白间的时序差异直接捕获转换细胞。在K562白血病模型中识别出转换细胞，并推导出连接细胞周期与线粒体重塑的转录特征。通过全基因组CRISPR筛选验证了BCR-ABL1和线粒体稳态基因等关键调控因子。该特征可预测CML对伊马替尼的应答，在AML中分层生存，并在31种TCGA肿瘤类型中保留预后价值，空间转录组学进一步揭示了实体瘤中的可塑性热点。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-02-708945-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1714, \"height\": 1982, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-02-708945-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1775, \"height\": 2509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-02-708945-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1744, \"height\": 2380, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-02-708945-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1743, \"height\": 2207, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-03-02-708945-v2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1639, \"height\": 1932, \"label\": \"Figure\"}]"
motivation: 表型可塑性驱动癌症治疗耐药，但瞬时状态转换的分子驱动因子难以定义，需要新方法直接捕获并解析转换细胞。
method: 基于单细胞多模态数据中mRNA与蛋白积累的时间延迟，识别转换细胞；结合CRISPR筛选与空间转录组学验证其调控因子。
result: 在K562模型中定义转换相关转录特征，涉及细胞周期和线粒体稳态；CRISPR确认BCR-ABL1等关键调控因子；该特征在多种癌症中具有预后预测能力。
conclusion: 该框架揭示了癌症可塑性的分子基础，为跨肿瘤类型量化可塑性提供了通用工具。
---

## 摘要
表型可塑性使癌细胞能够逃逸治疗，然而状态转变的瞬时性质使其分子驱动因素难以界定。在这里，我们提出一个单细胞框架，利用mRNA与蛋白质积累之间的时间延迟，直接捕获经历表型转换的细胞。我们展示了在多模态单细胞数据中，分化相关的转录本与蛋白质积累之间的延迟可检测为mRNA与表面蛋白水平的不一致。将该策略应用于K562白血病模型（该模型在分化的CD24-和祖细胞样CD24+状态之间交替），我们识别了转换中的细胞，并推导出将细胞周期进展和线粒体重塑与可塑性关联的转录特征。全基因组CRISPR筛选确认了可塑性的关键调控因子，包括BCR-ABL1和线粒体稳态基因。我们将转变相关程序总结为一个评分，该评分可预测慢性髓系白血病中对伊马替尼的反应，对急性髓系白血病进行生存分层，并在31种TCGA肿瘤类型中保留预后价值。空间转录组学揭示了实体瘤中局部可塑性热点。综上所述，该框架揭示了癌症可塑性的分子基础，并使其在肿瘤中得以量化。

## Abstract
Phenotypic plasticity allows cancer cells to evade therapy, yet the transient nature of state transitions has made their molecular drivers difficult to define. Here, we present a single-cell framework that leverages the temporal delays between mRNA and protein accumulation to directly capture cells undergoing phenotypic switching. We show that differentiation-associated delays between transcript and protein accumulation are detectable in multimodal single-cell data as discordant mRNA and surface-protein levels. Applying this strategy to the K562 leukemia model, which alternates between differentiated CD24- and progenitor-like CD24+ states, we identify transitioning cells and derive a transcriptional signature linking cell-cycle progression and mitochondrial remodeling to plasticity. Genome-wide CRISPR screening confirms key regulators of plasticity, including BCR-ABL1 and mitochondrial homeostasis genes. We summarize the transition-associated program into a score that predicts imatinib response in chronic myeloid leukemia, stratifies survival in acute myeloid leukemia, and retains prognostic value across 31 TCGA tumor types. Spatial transcriptomics reveals localized plasticity hotspots in solid tumors. Together, this framework exposes the molecular basis of cancer plasticity and enables its quantification across tumors.