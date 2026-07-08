---
title: "CyStainer: A transformer-based variational autoencoder for robust marker imputation in high-parameter cytometry"
title_zh: CyStainer：一种基于Transformer的变分自编码器，用于高参数细胞计数中的稳健标记插补
authors: "Ivanov, K., Moussawy, M. A., Kirk, F., Samuli, R., Lohi, O., Olsen, L., Modvig, S., Hautamäki, V., Heinäniemi, M."
date: 2026-06-30
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.30.735235v1.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 高参数流式细胞术的标记物插补
tldr: 随着高参数细胞术数据快速增长，合并不同数据集进行统一分析成为迫切需求。现有标记插补方法通常需要共享骨干标记，限制了应用场景。CyStainer提出基于Transformer的变分自编码器架构，能够在没有共享骨干标记的情况下进行稳健的标记预测。在FACS、CyTOF、InfinityFlow和CITE-seq等真实数据集上，CyStainer在多项基准测试中表现出竞争性或优越性能。该工具为面板合并、标记插补、数据集集成和虚拟染色提供了灵活且稳健的解决方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有标记插补方法依赖共享骨干标记，难以处理无重叠标记的数据集合并，限制高参数细胞术数据整合。
method: 采用Transformer变分自编码器，无需共享标记即可学习细胞谱系特征，实现稳健标记预测。
result: 在四个公开数据集上，CyStainer在标记预测任务中均达到或超越现有方法，表现稳健。
conclusion: CyStainer为高参数细胞术提供了无需共享标记的稳健数据集成与虚拟染色工具。
---

## 摘要
高参数细胞计数通过精确的免疫细胞分析、改善患者分层和监测，对临床诊断至关重要，同时增强了对疾病和治疗背景下细胞反应的理解。细胞计数数据量增长迅速，因此需要合并不同数据集进行统一分析。在此，我们提出CyStainer，一种基于Transformer的变分自编码器，在标记预测相关的多个关键任务上表现出与现有方法竞争或更优的性能。作为关键创新，我们证明CyStainer可以在没有共享基础标记集的情况下插补标记。我们使用真实的FACS、CyTOF、InfinityFlow和CITE-seq数据集进行了多项基准测试，表明CyStainer是一种稳健且灵活的工具，可用于面板合并、标记插补、数据集整合以及未见样本的虚拟染色。

图形摘要

O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=43 SRC="FIGDIR/small/735235v1_ufig1.gif" ALT="Figure 1">
查看大图（15K）：
org.highwire.dtl.DTLVardef@1e76266org.highwire.dtl.DTLVardef@1ed5303org.highwire.dtl.DTLVardef@1e4ff76org.highwire.dtl.DTLVardef@13faa48_HPS_FORMAT_FIGEXP  M_FIG C_FIG

## Abstract
High parameter cytometry is essential for clinical diagnostics through precise immune cell profiling, improved patient stratification, and monitoring, while also enhancing the understanding of cellular responses in disease and therapeutic contexts. The amount of cytometry data is growing fast, and with that, the need to merge different datasets for unified analysis. Here, we present CyStainer, a transformer-based variational autoencoder that demonstrates competitive or superior performance to existing methods on several key tasks related to marker prediction. As a key novelty, we demonstrate that CyStainer can impute markers without having a set of shared backbone markers. We performed several benchmarks using real-world FACS, CyTOF, InfinityFlow and CITE-seq datasets to show that CyStainer is a robust and flexible tool for panel merging, marker imputation, dataset integration and virtual staining of unseen samples.

Graphical Abstract

O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=43 SRC="FIGDIR/small/735235v1_ufig1.gif" ALT="Figure 1">
View larger version (15K):
org.highwire.dtl.DTLVardef@1e76266org.highwire.dtl.DTLVardef@1ed5303org.highwire.dtl.DTLVardef@1e4ff76org.highwire.dtl.DTLVardef@13faa48_HPS_FORMAT_FIGEXP  M_FIG C_FIG