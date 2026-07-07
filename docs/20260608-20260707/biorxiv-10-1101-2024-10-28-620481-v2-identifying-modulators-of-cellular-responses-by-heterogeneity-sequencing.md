---
title: Identifying Modulators of Cellular Responses by Heterogeneity-sequencing
title_zh: 通过异质性测序鉴定细胞反应的调节因子
authors: "Berg, K., Sakellaridi, L., Rummel, T., Hennig, T., Whisnant, A., Lodha, M., Krammer, T., Toussaint, C., Szymanska-De Wijs, K., Zheng, Y., Prusty, B. K., Doelken, L., Saliba, A.-E., Erhard, F."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.1101/2024.10.28.620481v2.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 利用代谢标记进行单细胞扰动响应预测
tldr: 单细胞对刺激的响应高度异质性，但传统方法只能关联无法确定因果。本研究提出Heterogeneity-seq，结合单细胞RNA-seq与代谢RNA标记(scSLAM-seq)及双机器学习，同时测量未标记和标记RNA，追踪细胞从初始状态到刺激结果的变化。在药物处理和巨细胞病毒感染中，成功鉴定了已知和新基因，包括促病毒和抗病毒宿主因子。该方法可因果揭示异质性响应的驱动因子。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法无法直接比较细胞初始状态与刺激结果，只能发现关联而无法识别因果驱动因子。
method: 结合单细胞RNA-seq与代谢RNA标记(scSLAM-seq)及双机器学习，同时测量未标记和标记RNA以追踪细胞状态转变。
result: 鉴定了药物响应和巨细胞病毒感染中的已知和新基因，包括促病毒和抗病毒宿主因子。
conclusion: Heterogeneity-seq能够因果揭示异质性细胞响应的驱动因子，为研究细胞命运决定提供新方法。
---

## 摘要
单个细胞对药物处理、病毒感染或其他分子刺激的反应高度异质，且取决于细胞的初始状态。单细胞转录组学的文库制备具有破坏性，无法直接比较初始状态与刺激结果。因此，当前方法仅限于识别相关关联，而非解析异质性结果的因果驱动因素。我们开发了异质性测序（Heterogeneity-seq），该方法结合单细胞RNA测序与代谢RNA标记（scSLAM-seq）及双重机器学习，以克服这一限制。通过利用单个细胞中未标记和标记RNA的同时测量，Heterogeneity-seq揭示了从刺激前细胞状态到数千个细胞中不同刺激结果的转变。这些联系使得识别因果控制异质性细胞反应的因子成为可能。我们使用Heterogeneity-seq鉴定了已知和新的驱动药物反应基因，以及控制巨细胞病毒感染的前病毒和抗病毒宿主因子。

## Abstract
The response of individual cells to drug treatment, virus infections or other molecular stimuli is highly heterogeneous and depends on the cells initial state. Library preparation for single-cell transcriptomics is destructive, precluding a direct comparison between the initial state and the stimulus outcome. Consequently, current methods are restricted to identifying correlative associations rather than resolving causal drivers of heterogeneous outcomes. We developed Heterogeneity-seq, which combines single-cell RNA-seq with metabolic RNA labeling (scSLAM-seq) and double machine learning to overcome this limitation. By leveraging simultaneous measurements of unlabeled and labeled RNA in individual cells, Heterogeneity-seq uncovers the transition from pre-stimulated cell states to distinct stimulation outcomes across thousands of cells. These links enable the identification of factors that causally govern heterogeneous cellular responses. We used Heterogeneity-seq to identify both known and novel genes that drive responses to drug treatment, as well as pro- and antiviral host factors governing cytomegalovirus infection.