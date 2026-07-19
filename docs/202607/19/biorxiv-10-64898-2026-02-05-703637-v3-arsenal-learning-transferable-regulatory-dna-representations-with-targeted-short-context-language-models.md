---
title: "ARSENAL: Learning Transferable Regulatory DNA Representations with Targeted Short-Context Language Models"
title_zh: ARSENAL：利用靶向短上下文语言模型学习可迁移的调控DNA表示
authors: "Patel, A., Kundaje, A."
date: 2026-07-12
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.05.703637v3.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 调控DNA表示学习用于变异效应预测，与遗传扰动相关
tldr: 现有DNA语言模型多基于全基因组长上下文训练，难以捕获短而稀疏的调控元件特征。针对这一问题，提出ARSENAL模型，利用ENCODE候选调控元件进行短上下文掩码预训练。ARSENAL能从头恢复多种转录因子结合基序，在零样本调控变异效应预测上超越现有基础模型，并显著改善染色质可及性预测与变异评分。结合下游监督模型，还可用于多目标调控序列设计。实验表明，聚焦调控区的定向自监督预训练即可学到生物上可解释且可迁移的表示，无需全基因组规模训练或长上下文。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1434, \"height\": 821, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1436, \"height\": 713, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1437, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 670, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 672, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1056, \"height\": 803, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1446, \"height\": 893, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1570, \"height\": 1198, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1593, \"height\": 455, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1442, \"height\": 470, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 741, \"label\": \"Table\"}]"
motivation: 现有DNA语言模型侧重全基因组长上下文，而调控DNA功能元件稀疏、依赖短序列上下文，需要针对性的预训练策略。
method: 基于ENCODE顺式调控元件数据集，构建短上下文（≤512 bp）掩码语言模型ARSENAL，通过掩码预测学习局部序列模式。
result: 无监督恢复转录因子motif；零样本变异预测优于其他基础模型；提升下游染色质可及性和变异评分预测并实现多目标序列生成。
conclusion: 针对调控区域的短上下文自监督预训练可高效学习可迁移的调控DNA表示，无需全基因组或任务标签。
---

## 摘要
DNA语言模型旨在学习基因组序列的表示，用于变异解读、调控预测和序列设计。大多数DNA语言模型是在整个基因组和长上下文中训练的，但调控DNA提出了一个独特的挑战：功能元件稀疏、上下文依赖，并且由嵌入在广泛背景序列中的短转录因子基序语法编码。我们提出了ARSENAL，这是一个在ENCODE候选顺式调控元件上预训练的短上下文掩码DNA语言模型。ARSENAL从头恢复多种转录因子基序，并相对于其他DNA语言模型基础模型改进了零样本调控变异效应预测。ARSENAL嵌入还改进了预测染色质可及性和调控变异评分的监督调控序列模型。最后，ARSENAL作为有效的生成先验，通过监督预言机实现多目标调控序列设计。ARSENAL表明，针对调控区域的目标自监督预训练可以在没有基因组规模训练、长上下文或任务特定标签的情况下学习具有生物学意义的可迁移调控表示。

代码可在https://github.com/kundajelab/regulatory_lm获取。模型和数据可在https://sageb.io/ydjhqM共享。

## Abstract
DNA language models (DNALMs) aim to learn representations of genomic sequence for variant interpretation, regulatory prediction, and sequence design. Most DNALMs are trained on whole genomes and long contexts, but regulatory DNA poses a distinct challenge: functional elements are sparse, context dependent, and encoded by short transcription factor motif syntax embedded in extensive background sequence. We introduce ARSENAL, a short-context masked DNA language model pretrained on ENCODE candidate cis-regulatory elements. ARSENAL recovers diverse transcription factor motifs de novo and improves zero-shot regulatory variant effect prediction relative to other DNALM foundation models. ARSENAL embeddings also improve supervised regulatory sequence models at predicting chromatin accessibility and regulatory variant scoring. Finally, ARSENAL serves as an efficient generative prior, enabling multi-objective regulatory sequence design with supervised oracles. ARSENAL shows that targeted self-supervised pretraining on regulatory regions can learn biologically meaningful and transferable regulatory representations without genome-scale training, long contexts or task-specific labels.

Code is available at https://github.com/kundajelab/regulatory_lm. Models and data are shared at https://sageb.io/ydjhqM