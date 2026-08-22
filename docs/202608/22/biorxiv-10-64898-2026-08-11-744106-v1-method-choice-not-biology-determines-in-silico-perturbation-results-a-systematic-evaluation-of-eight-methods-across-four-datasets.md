---
title: "Method Choice, Not Biology, Determines In Silico Perturbation Results: A Systematic Evaluation of Eight Methods Across Four Datasets"
title_zh: 方法选择而非生物学决定计算机模拟扰动结果：对四个数据集中八种方法的系统评估
authors: "Wenjie, G., Wu, S., Hu, G., Yang, Z., Wang, Z., Cai, J., Mao, J."
date: 2026-08-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.11.744106v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 对八种单细胞扰动预测方法在四个数据集上进行了系统基准评估
tldr: 目前大多数单细胞转录组扰动预测方法仅在单一数据集上验证，可靠性未知。本研究系统评估了8种方法在4个数据集上的表现，发现仅CellOracle和DDIM能稳定检测TF-通路信号，且方法选择可逆转生物学结论。通过CRISPRi验证，预测方向与实验存在根本差距。研究揭示了多种失败模式，并提出方法选择指南，强调交叉验证和方向感知基准的重要性。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有扰动预测方法缺乏跨数据集系统验证，可靠性和泛化性未知，导致方法选择无依据。
method: 对8种方法在4个数据集上交叉评测，结合CRISPRi验证、潜伏空间诊断和消融实验分析失败模式。
result: 6/8方法无法检测TF-通路信号，仅CellOracle和DDIM有效但方向预测与实验不符，方法间排名显著负相关。
conclusion: 方法选择可逆转结论，需采用交叉验证、方向感知基准和最小数据量要求指导选型。
---

## 摘要
大多数用于单细胞转录组学的计算机模拟扰动方法仅在单个数据集上进行了验证，其可靠性和泛化性未知。通过对跨越四种数据集的六种数学框架中的八种方法进行系统的跨方法、跨数据集基准测试，我们发现八种方法中有六种（包括广泛使用的基于VAE和张量分解的方法）未能产生可检测的转录因子（TF）到通路信号。只有CellOracle和DDIM一致地检测到TF到糖酵解的定向调控。PBMC单核细胞中的跨通路分析揭示了超出糖酵解的生物学上连贯的TF-通路关联（SPI1[->]糖酵解4.4倍富集，FOS[->]AP-1靶点4.4倍），其中SOX9作为生物学特异性对照（无通路富集）。仅方法选择就能逆转生物学结论：DDIM和scTenifoldKnk的排名显著反相关（ρ=-0.811，p=0.027）。K562细胞中的CRISPRi Perturb-seq验证确认TF敲低抑制糖酵解基因表达（JUN δ=-1.72，CEBPB δ=-1.59，SPI1 δ=-1.57，FOS δ=-0.70），但CellOracle预测的扰动方向与实验方向不匹配（一致性40.9%，与随机无差异），揭示了稳态相关性与因果扰动之间的根本差距。使用VAE潜在空间分析、相关性分布比较和基因-基因图分析的诊断性分析识别了不成功方法的不同失败模式：VAE潜在空间竞争（STAT3信噪比0.44 vs. SPI1 4.25）、相关性噪声（TF-糖酵解|r|=0.038与背景|r|=0.047无法区分）和图非特异性（0.84倍富集）。一项受控消融实验表明，向DDIM添加GRN先验并未提高目标召回率（所有TF的delta=0），证实性能差异是多因素的。这些发现为方法选择提供了初步指导，包括跨通路验证、方向感知基准测试以及最小数据要求（≥500个细胞，≥1,000个HVG）。

## Abstract
Most in silico perturbation methods for single-cell transcriptomics have been validated only on individual datasets, leaving their reliability and generalizability unknown. Through systematic cross-method, cross-dataset benchmarking of eight methods spanning six mathematical frameworks across four datasets, we find that six of eight methods--including widely used VAE-based and tensor decomposition approaches--fail to produce detectable transcription factor (TF)-to-pathway signals. Only CellOracle and DDIM consistently detected TF-to-glycolysis directional regulation. Cross-pathway analysis in PBMC monocytes revealed biologically coherent TF-pathway associations beyond glycolysis (SPI1[-&gt;]glycolysis 4.4x enrichment, FOS[-&gt;]AP-1 targets 4.4x), with SOX9 serving as a biological specificity control (no pathway enrichment). Method choice alone could reverse biological conclusions: DDIM and scTenifoldKnk rankings were significantly anti-correlated ({rho}=-0.811, p=0.027). CRISPRi Perturb-seq validation in K562 cells confirmed TF knockdown suppresses glycolysis gene expression (JUN {delta}=-1.72, CEBPB {delta}=-1.59, SPI1 {delta}=-1.57, FOS {delta}=-0.70), but CellOracle-predicted perturbation directions did not match experimental directions (40.9% agreement, not different from chance), revealing a fundamental gap between steady-state correlation and causal perturbation. Diagnostic analyses using VAE latent space profiling, correlation distribution comparison, and gene-gene graph analysis identified distinct failure modes in unsuccessful methods: VAE latent space competition (STAT3 signal-to-noise 0.44 vs. SPI1 4.25), correlation noise (TF-glycolysis |r|=0.038 indistinguishable from background |r|=0.047), and graph non-specificity (0.84x enrichment). A controlled ablation experiment showed that adding a GRN prior to DDIM did not improve target recall (delta=0 for all TFs), confirming that performance differences are multi-factorial. These findings establish preliminary guidance for method selection, including cross-pathway validation, direction-aware benchmarking, and minimum data requirements ([&ge;]500 cells, [&ge;]1,000 HVGs).

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **背景**：单细胞转录组学中，计算机模拟扰动（in silico perturbation）方法被广泛用于预测基因调控扰动后的细胞状态变化，然而绝大多数方法仅在单一数据集上验证，泛化性和可靠性均处于未知状态。
- **核心问题**：八种方法跨四种数据集的系统基准测试揭示了什么？这些方法是否真的能捕捉到生物学信号？方法选择的差异是否会改变结论？
- **整体含义**：论文的根本关切是：**方法选择本身可能掩盖或扭曲生物学结论**，即"方法选择而非生物学决定了扰动预测结果"。这意味着需要对现有方法进行大规模、跨数据集的系统验证，以便为社区提供方法选择的可靠依据。

## 2. 论文提出的方法论

- **基准框架**：作者构建了一个跨方法、跨数据集的系统评估流程，涵盖六种数学框架下的八种单细胞扰动预测方法（包括基于VAE的方法、张量分解方法、CellOracle、DDIM、scTenifoldKnk等）。
- **评估流程**：
  - 输入单细胞转录组数据（如PBMC单核细胞、K562细胞系等）。
  - 对每种方法进行TF到通路（TF-to-pathway）信号的检测，以富集倍数（enrichment）为度量。
  - 使用CRISPRi Perturb-seq作为独立实验验证手段，比较TF敲低后糖酵解基因表达的实际变化与CellOracle预测的扰动方向。
  - 通过诊断性分析（VAE潜在空间分析、相关性分布比较、基因-基因图分析）识别不成功方法的具体失败模式。
  - 进行受控消融实验：向DDIM添加GRN（基因调控网络）先验，检验目标召回率是否变化。
- **关键评估指标**：信号-噪声比（如STAT3 0.44 vs. SPI1 4.25）、富集倍数（如0.84x vs. 4.4x）、方向一致性（40.9%）、排名相关性（ρ=-0.811）等。

## 3. 实验设计

- **数据集**：
  1. PBMC单核细胞（跨通路分析，如糖酵解、AP-1靶点）；
  2. K562细胞系（CRISPRi Perturb-seq验证）；
  3-4. 另外两个数据集（摘要中未明确列出名称，但总量为四个数据集）。
- **Benchmark**：以TF到通路信号的可检测性为核心基准，辅以方向预测准确性、TF-糖酵解相关性（|r|）与背景（|r|=0.047）的可区分性等。生物学特异性对照采用SOX9（预期无通路富集）。
- **对比方法**：共八种，包括CellOracle、DDIM、scTenifoldKnk，以及基于VAE和张量分解的方法（具体名称摘要未全列出）。涵盖连接组学、生成模型、矩阵分解等多种数学框架。

## 4. 资源与算力

- **文中未明确说明**：摘要中未提及GPU型号、数量、训练时长或任何计算资源的具体信息。该论文为预印本，可能在全文中包含这些内容，但基于现有文本无法提供算力细节。如需精确信息，需查阅全文或补充材料。

## 5. 实验数量与充分性

- **主要实验组**：
  - 跨数据集基准测试：8种方法 × 4个数据集（共32组方法-数据组合）；
  - 跨通路验证（PBMC单核细胞）；
  - CRISPRi Perturb-seq方向验证（K562细胞）；
  - 三种诊断性分析（VAE潜在空间、相关性分布、图分析）；
  - GRN先验消融实验；
  - 排名相关性分析（DDIM vs. scTenifoldKnk）。
- **充分性评价**：实验设计较为充分且合理。跨数据集、跨方法的设计避免了单一数据集上的偶然性；CRISPRi验证提供了因果层面的实验参考；消融实验检验了特定因素（GRN先验）的贡献。但也存在局限：CRISPRi验证仅针对K562细胞和糖酵解通路，未覆盖所有方法和所有生物学场景；部分方法的详细配置和参数调优过程在摘要中不可见，公平性需在全文层面进一步评估。

## 6. 论文的主要结论与发现

- **六/八的方法无法产生可检测的TF-通路信号**，包括广泛使用的基于VAE和张量分解的方法，说明这些方法的生物学信号提取能力存在系统性不足。
- **仅CellOracle和DDIM能一致检测TF到糖酵解的定向调控**，并通过PBMC跨通路分析发现SPI1→糖酵解（4.4x富集）和FOS→AP-1靶点（4.4x富集）等生物学上连贯的关联，SOX9阴性对照无富集，验证了信号的特异性。
- **方法选择可以逆转生物学结论**：DDIM和scTenifoldKnk的排名显著负相关（ρ=-0.811，p=0.027），即同一个生物学问题，选择不同方法可能得出截然相反的结论。
- **CellOracle的预测方向与实验不符**：CRISPRi确认TF敲低抑制糖酵解基因（JUN δ=-1.72，CEBPB δ=-1.59，SPI1 δ=-1.57，FOS δ=-0.70），但CellOracle预测方向一致性仅40.9%（与随机无差异）——稳态相关性与因果扰动之间存在根本性差距。
- **失败模式各不相同**：VAE潜在空间竞争、相关性噪声淹没信号、图分析非特异性（0.84x），每种方法有独特的病因。
- **性能差异是多因素的**：向DDIM添加GRN先验后目标召回率无变化（delta=0），说明模型性能差异不能归结为单一设计因素。
- **提供初步方法选择指南**：要求跨通路验证、方向感知基准、最小数据量（≥500细胞，≥1000 HVGs）。

## 7. 优点

- **系统性和广度**：首个同时对8种方法跨4数据集进行系统评估的工作，覆盖多种数学框架，填补了该领域缺乏跨数据集验证的空白。
- **因果验证**：引入CRISPRi Perturb-seq作为独立实验验证，揭示了计算预测与真实扰动在方向性上的根本差距，具有重要警示意义。
- **诊断性分析**：不满足于"好/坏"的简单排名，而是深入识别每种失败方法的不同机制（潜在空间竞争、噪声、图非特异性），为后续方法改进提供了具体线索。
- **方法选择指导**：提出了实际可操作的建议（最小数据量要求、方向感知基准等），对社区具有直接参考价值。
- **生物学特异性对照**：精心设计了SOX9等阴性对照和SPI1/FOS等阳性对照，增强结论的生物学可信度。

## 8. 不足与局限

- **实验覆盖范围**：CRISPRi验证仅限K562细胞和糖酵解通路，其他通路和方法组合的验证不足；四个数据集的细胞类型和扰动类型覆盖面有限。
- **方向预测的根本性缺陷**：CellOracle方向一致性仅40.9%，表明"稳态相关性→因果扰动"的映射是不可靠的，这一问题的普适性需进一步检验。
- **方法公平性风险**：每种方法预训练配置、超参数、输入特征是否做了等价的调优，在摘要中不可见；不同类型的数学框架适合的数据分布不同，可能存在隐性偏差。
- **消融实验的解释局限**：单一消融实验（DDIM + GRN）只证明该维度不是性能差距主因，不代表其他可解释性因素不重要。
- **最小数据要求等指南的普适性**：≥500细胞、≥1,000 HVG的阈值可能依赖数据集特性，在更复杂组织或更高dropout的场景下不一定适用。
- **预印本限制**：原文为bioRxiv预印本（2026年8月），尚未经过完整同行评审，其统计检验的严谨性和结论的可复现性仍需进一步确认。

（完）
