---
title: Does ensembling improve feature attributions from sequence-to-activity models?
title_zh: 集成学习能否改善序列到活动模型的特征归因？
authors: "Maslova, A., Libbrecht, M."
date: 2026-07-13
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.08.737315v1.full.pdf"
tags: ["query:virtual-cell"]
score: 7.0
evidence: 序列到活性模型用于预测基因表达和遗传变异效应，直接与预测遗传扰动下的细胞响应相关
tldr: 序列到活动模型在基因组解释中广泛应用，但其特征归因的可靠性存疑。本研究探索模型集成能否提升归因质量，发现集成多个模型的归因能更好地识别转录因子基序和预测调控变异。蒙特卡洛Dropout集成以较低训练成本达到接近多模型集成的效果。这表明集成策略可有效增强可解释AI的置信度，为基因组研究提供更可靠的解释工具。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737315-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1706, \"height\": 947, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737315-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1704, \"height\": 1011, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737315-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1698, \"height\": 1526, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737315-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1703, \"height\": 1166, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-08-737315-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1395, \"height\": 314, \"label\": \"Table\"}]"
motivation: 现有序列到活动模型的可解释性存在不确定性，亟需提升归因可靠性以支持下游基因组分析。
method: 通过集成多个独立训练的S2A模型或采用蒙特卡洛Dropout的归因，并与单一模型对比，评估下游应用性能。
result: 集成归因显著提高了转录因子基序识别和调控变异预测的效果，MCDropout接近但未完全达到多模型集成性能。
conclusion: 模型集成能有效改善特征归因质量，蒙特卡洛Dropout以较低训练成本提供可行替代方案。
---

## 摘要
序列到活动模型以DNA序列为输入，预测转录因子结合和基因表达等基因组活动。将DeepLIFT等可解释人工智能（xAI）方法应用于这些模型，最近已在许多基因组问题（包括转录因子结合语法和预测遗传变异效应）上取得突破。然而，序列到活动解释的可靠性仍存在显著不确定性。因此，我们需要准确的置信度概率度量来区分可靠和不可靠的解释。为此，研究人员最近致力于描述序列到活动模型集成之间的变异性。然而，先前的工作集中在使用模型集成来改进模型预测本身。在此，我们旨在评估模型集成是否也可用于改进事后xAI方法的特征归因。我们发现，对多个模型的归因进行集成可改善下游应用，包括识别转录因子基序和预测调控性遗传变异。我们还表明，使用蒙特卡洛dropout（MCDropout）形成的集成性能接近但未达到训练多个模型的水平，且训练时间计算成本更低。

## Abstract
Sequence-to-activity models take as input DNA sequence and predict genomic activities such as transcription factor binding and gene expression. Applying explainable AI (xAI) methods such as DeepLIFT to these models has recently led to breakthroughs towards many genomic problems, including transcription factor binding grammar and predicting effects of genetic variants. However, there remains significant uncertainty about the reliability of sequence-to-activity interpretations. Thus, we need accurate probabilistic measures of confidence to distinguish reliable from unreliable interpretations. Towards this end, researchers have recently aimed to characterize variability across ensembles of S2A models. However, previous work has focused on using model ensembles to improve the model predictions themselves. Here, we aim to evaluate whether model ensembles can also be used to improve feature attributions from post-hoc xAI methods. We find that ensembling attributions from multiple models improves downstream applications, including identifying transcription factor motifs and predicting regulatory genetic variants. We show that forming an ensemble using Monte Carlo Dropout (MCDropout) gets near to, but does not match, the performance of training multiple models, at much less train-time computational cost.