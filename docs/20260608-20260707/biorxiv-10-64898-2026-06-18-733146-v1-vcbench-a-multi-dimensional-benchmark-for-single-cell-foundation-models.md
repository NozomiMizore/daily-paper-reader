---
title: "VCBench: A Multi-Dimensional Benchmark for Single-Cell Foundation Models"
title_zh: VCBench：单细胞基础模型的多维基准
authors: "Weidener, L. S., Brkic, M., Jovanovic, M., Ulgac, E., Meduri, A."
date: 2026-06-23
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.18.733146v1.full.pdf"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 包含扰动预测维度的虚拟细胞模型基准
tldr: "单细胞基础模型能力评估依赖碎片化单任务基准，VCBench合成四个虚拟细胞框架为七个能力维度，其中五个可测，评估五个模型与线性基线。结果发现，基线在四维匹配或超越所有模型；TranscriptFormer跨模态预测优于基线53%但导致时序性能崩溃，且模型缺乏完整训练清单。贡献包括基准、污染报告模式、通用标签集协议和校准探针。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有单细胞基础模型评估碎片化，单任务基准掩盖模型真实能力，需统一多维度基准。
method: 合成四个虚拟细胞框架为七个能力维度，对五个可测维度评估五个模型与预注册线性基线。
result: 线性基线在四维匹配或超越所有模型；TranscriptFormer跨模态预测领先但存在污染，且导致时序性能崩溃。
conclusion: 发布VCBench基准、污染报告模式、通用标签集协议和校准探针，揭示模型与基线差距及内部权衡。
---

## 摘要
单细胞基础模型日益被视为虚拟细胞，但其能力评估依赖于碎片化、主要为单任务基准，这些基准掩盖了这些模型在简单基线上改进的方面。VCBench通过将四个独立的虚拟细胞框架综合为七个能力维度来解决这一问题：扰动响应预测、跨物种通用性、基因调控网络（GRN）推断、模态整合、时间动态、多尺度整合和计算机实验。每个维度在当前架构和数据集下评估操作可测试性：五个维度允许直接或代理评估，而多尺度整合和计算机实验在结构上无法作为端到端任务进行测试。我们在五个可测试维度上评估了五种基础模型（Geneformer、scGPT、UCE、TranscriptFormer、Arc State），与预先注册的线性基线和最近邻基线进行比较，并报告了三个发现。首先，在五个评分维度中的四个上，基线匹配或超过了每个基础模型，将线性基线在扰动预测上的竞争力复制并扩展到跨物种迁移、GRN推断和时间顺序。其次，TranscriptFormer在跨模态RNA到蛋白质预测上独自超过了最强基线（Pearson相关提高53%，并记录了污染警告），并且是唯一达到预先注册虚拟细胞（VC）级别量表中第2级的模型；这一优势背后的架构选择同时导致光谱坍塌，破坏了其时间顺序性能，这是单任务基准无法看到的权衡。第三，没有基础模型发布完整的细胞级训练清单，使用户无法检测数据污染。除基准外，VCBench还发布了污染报告模式，并贡献了另外两种方法论工具：一种通用标签集协议，用于控制跨物种迁移中的类别计数混淆，以及一种用于认知校准的传播误差相关探测方法。

## Abstract
Single-cell foundation models are increasingly positioned as virtual cells, yet their capabilities are assessed by fragmented, largely single-task benchmarks that obscure where these models improve on simple baselines. VCBench addresses this by synthesizing four independent virtual-cell frameworks into seven capability dimensions: perturbation response prediction, cross-species universality, gene regulatory network (GRN) inference, modality integration, temporal dynamics, multi-scale integration, and in silico experimentation. Each dimension is assessed for operational testability under current architectures and datasets: five admit direct or proxy evaluation, while multi-scale integration and in silico experimentation are structurally untestable as end-to-end tasks. We evaluate five foundation models (Geneformer, scGPT, UCE, TranscriptFormer, Arc State) against pre-registered linear and nearest-neighbor baselines across the five testable dimensions, and report three findings. First, the baselines match or exceed every foundation model on four of the five scored dimensions, replicating the reported competitiveness of linear baselines on perturbation prediction and extending it to cross-species transfer, GRN inference, and temporal ordering. Second, TranscriptFormer alone exceeds the strongest baseline on cross-modal RNA-to-protein prediction (53% Pearson improvement, with a documented contamination caveat) and is the only model to reach Level 2 in the pre-registered Virtual Cell (VC) Level rubric; the architectural choice behind this advantage simultaneously causes a spectral collapse that destroys its temporal-ordering performance, a tradeoff invisible to single-task benchmarks. Third, no foundation model publishes a complete cell-level training manifest, leaving data contamination undetectable to users. Alongside the benchmark, VCBench releases a Contamination Reporting Schema and contributes two further methodological tools: a common-label-set protocol that controls for class-count confounds in cross-species transfer, and a spread-error correlation probe for epistemic calibration.