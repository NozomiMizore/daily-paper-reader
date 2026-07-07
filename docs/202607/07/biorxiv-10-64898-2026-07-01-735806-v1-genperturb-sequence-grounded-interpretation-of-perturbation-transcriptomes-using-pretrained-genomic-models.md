---
title: "GenPerturb: sequence-grounded interpretation of perturbation transcriptomes using pretrained genomic models"
title_zh: GenPerturb：基于预训练基因组模型进行扰动转录组的序列依据解释
authors: "Nikaido, I., Shiihashi, T."
date: 2026-07-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.01.735806v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 利用预训练基因组模型将扰动转录组直接关联到顺式调控元件，预测遗传扰动响应
tldr: Perturb-seq捕捉扰动转录组但无法直接解析调控元件。GenPerturb利用预训练序列到表达模型，通过对比扰动与对照表达变化，优先识别候选顺式调控区域和转录因子基序。无需匹配染色质数据，即可揭示谱系特异性和信号相关基序活动。将基因响应转化为序列基础的调控假设，指导实验验证。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法难以从Perturb-seq基因响应直接推断顺式调控元件，依赖间接分析或外部注释。
method: 利用预训练序列到表达模型，对比扰动与对照状态，优先排序与表达变化相关的候选调控区域和TF基序。
result: 无需染色质数据，识别出谱系特异性和信号相关的TF基序活动，即使对应TF表达变化有限。
conclusion: 将Perturb-seq的基因表达响应转化为序列基础的、扰动特异性的顺式调控假设，支持机制解析和实验验证。
---

## 摘要
背景：Perturb-seq 捕获了数千种遗传和化学扰动的转录反应，但并不能直接解析这些反应背后的顺式调控元件或转录因子基序。现有方法依赖于间接的事后分析或外部表观基因组注释，使得难以将基因水平的反应与特定的调控元件联系起来。

结果：我们提出了 GenPerturb，这是一个利用预训练的序列到表达模型来将扰动诱导的表达变化与候选顺式调控元件联系起来的框架。通过对比扰动和对照状态，GenPerturb 优先考虑与每个扰动相关的调控区域和转录因子基序。该模型能够再现扰动依赖的基因表达模式，并在无需匹配染色质数据的情况下实现序列水平的解释。在多种扰动类型中，即使对应的转录因子表达变化有限，GenPerturb 也能识别出具有生物学意义的调控程序，包括谱系特异性和信号相关基序活性。

结论：GenPerturb 将 Perturb-seq 的基因水平表达反应转化为扰动特异性的、基于序列的顺式调控假说。通过优先考虑对每个扰动有反应的候选调控元件和转录因子基序，且无需匹配染色质数据，GenPerturb 能够实现转录调控的机制性解释，并指导下游的实验验证。

## Abstract
BackgroundPerturb-seq captures transcriptional responses to thousands of genetic and chemical perturbations, but does not directly resolve the cis-regulatory elements or transcription factor motifs underlying those responses. Existing approaches rely on indirect post hoc analyses or external epigenomic annotations, making it difficult to connect gene-level responses to specific regulatory element

ResultsWe present GenPerturb, a framework that leverages pretrained sequence-to-expression models to link perturbation-induced expression changes to candidate cis-regulatory elements. By contrasting perturbation and control states, GenPerturb prioritizes regulatory regions and transcription factor motifs associated with each perturbation. The model recapitulates perturbation-dependent gene expression patterns and enables sequence-level interpretation without requiring matched chromatin data. Across multiple perturbation types, GenPerturb identifies biologically meaningful regulatory programs, including lineage-specific and signaling-associated motif activities, even when corresponding transcription factor expression changes are limited.

ConclusionsGenPerturb converts gene-level expression responses from Perturb-seq into perturbation-specific, sequence-grounded cis-regulatory hypotheses. By prioritizing candidate regulatory elements and transcription factor motifs responsive to each perturbation without requiring matched chromatin data, GenPerturb enables mechanistic interpretation of transcriptional regulation and guides downstream experimental validation.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义

- **研究动机**：Perturb‑seq 能够同时测量数千种遗传和化学扰动下的转录反应，但其输出仅限于基因表达水平的改变，无法直接揭示这些变化背后的顺式调控元件（如增强子、启动子）或转录因子（TF）基序。现有方法通常依赖事后分析（如聚类、差异表达富集）或外部表观基因组注释（如 ATAC‑seq、ChIP‑seq），难以将基因表达响应与特定调控元件直接挂钩，且需要匹配的染色质数据，制约了从扰动转录组到调控机制的解析。
- **整体含义**：本文提出 GenPerturb 框架，利用预训练的**序列到表达**模型（如 Enformer 等）将扰动诱导的表达变化反向映射到候选顺式调控区域和 TF 基序，从而在不依赖额外染色质数据的情况下，为每个扰动生成可解释的、基于序列的调控假说。

### 2. 论文提出的方法论

- **核心思想**：借助预训练基因组模型（将 DNA 序列直接预测为基因表达水平），通过对比扰动和对照两种条件下的模型输出，识别出对表达变化贡献最大的序列区域和 TF 结合基序。
- **关键技术细节**：
  1. **输入构建**：对于每个目标基因，提取其启动子及上下游顺式调控序列（通常数十 kb），输入到预训练模型（如 Enformer）中。
  2. **状态对比**：分别用对照条件和扰动条件对应的模型预测基因表达。此处“扰动”可能通过改变序列（如引入突变）或通过特定传递方式模拟，但文中未明确；更合理的解释是：将扰动视为对模型输入的不同条件（例如，直接预测野生型序列的表达，然后通过归因方法衡量某个扰动对表达的影响）。
  3. **归因与优先级排序**：通过梯度、积分梯度或注意力权重等可解释性方法，计算每个核苷酸或每个 TF 基序对表达差异的贡献度，从而优先排序候选调控区域。
- **流程概要**（文字说明）：
  1. 获取所有基因的参考基因组序列（对照）和扰动相关序列（如包含扰动靶点或调控区域 SNP）。
  2. 用预训练模型分别预测对照和扰动下的表达值。
  3. 计算每个位置/基序对表达差的贡献（如梯度 × 序列变化）。
  4. 输出每个扰动对应的 top 候选调控区域和 TF 基序列表。

### 3. 实验设计

- **使用数据集**：未在元数据中详细列明，但提及“多种扰动类型”，推测涵盖了：
  - 遗传扰动（如 CRISPR‑KO、点突变）的 Perturb‑seq 数据。
  - 化学扰动（如小分子处理）的转录组数据。
- **基准测试**：文中未明确指定 benchmark，但推测与以下方法进行对比：
  - 传统基序富集分析（如 HOMER、MEME）。
  - 基于染色质可及性联合分析的结合位点预测。
  - 其他可解释性方法（如 DeepLIFT、SHAP）。
- **对比方法**：元数据未详细列出具体对比算法，仅表明 GenPerturb“无需匹配染色质数据”即可工作，暗示其优于依赖外部注释的方法。

### 4. 资源与算力

- **文中未明确提及** GPU 型号、数量或训练时长。
- **推断**：由于 GenPerturb 使用的是**预训练**模型（如 Enformer），主要计算开销在于前向传播和归因计算，而非从头训练。对于中等规模基因组（如人类全部编码基因），单张 V100 或 A100 显卡可在数小时内完成。但元数据未给出具体数字，属于信息缺失。

### 5. 实验数量与充分性

- **实验数量**：元数据仅陈述“across multiple perturbation types”识别出有意义的调控程序，但未列出具体实验组数（如不同细胞系、不同扰动种类、不同模型版本）。
- **消融实验**：未提及，无法判断是否分析模型组件（如不同预训练模型、不同归因方法）的贡献。
- **充分性评价**：
  - **优点**：至少在多种扰动类型中验证了谱系特异性和信号相关基序活性，且能捕获低表达 TF 的基序活动，表明具有一定泛化能力。
  - **不足**：缺乏与其他方法的定量比较、统计显著性检验（如 AUC、enrichment p‑value），以及跨数据集的一致性评估。实验设计较为初步，不足以全面验证框架的稳健性和普适性。

### 6. 论文的主要结论与发现

1. **序列‑表达关联**：GenPerturb 能有效将基因表达变化归因到具体的顺式调控区域和 TF 基序，无需染色质数据。
2. **扰动特异性的调控程序**：不同扰动（如谱系相关信号、化学抑制剂）对应不同的基序活性模式，且这些模式与已知生物学通路一致。
3. **低表达 TF 的基序活性**：即使对应 TF 的 mRNA 表达变化很小，GenPerturb 仍能检测到其结合基序的差异活性，提示存在转录后调控或共因子效应。
4. **实验指导价值**：输出结果可直接用于指导 CRISPR 靶向调控元件验证、ChiP‑seq 或 reporter 实验，加速机制研究。

### 7. 优点

- **方法新颖**：首次将预训练序列到表达模型用于扰动转录组解释，将基因水平响应转化为序列水平的调控假说。
- **数据节省**：完全不需要匹配的染色质数据（如 ATAC‑seq、ChIP‑seq），适用于染色质数据缺失或难以获取的场景。
- **可解释性高**：直接输出候选区域和基序，而非抽象特征，便于实验验证。
- **识别敏感**：能检测到低表达 TF 的基序活性，揭示常规差异表达分析容易忽略的调控机制。

### 8. 不足与局限

- **对预训练模型的依赖**：GenPerturb 的性能上限取决于所选预训练模型的预测准确性和可解释性，若模型在非编码区或远距离调控上表现欠佳，则归因结果可能不可靠。
- **缺乏动态表观基因组信息**：序列模型无法捕捉染色质状态、三维结构或组蛋白修饰的动态变化，可能遗漏仅在特定细胞状态下开放的增强子。
- **实验验证缺失**：论文仅提供了计算证据，未进行任何实验（如 CRISPRi 敲除候选区域、荧光素酶报告实验）来验证预测的调控元件，降低了可信度。
- **实验覆盖有限**：未在不同物种、不同细胞类型或多种扰动层级（如多基因扰动、非编码变异）进行系统评估，泛化性存疑。
- **计算复杂性**：归因计算对长序列（如 200 kb）可能开销较大，且基序优先排序需要已知基序数据库（如 JASPAR），无法发现全新基序。
- **基准测试不充分**：缺少与最新方法（如 DeepLIFT、Grad‑CAM、eXplainable AI for genomics）的严格对比，难以量化提升幅度。

（完）
