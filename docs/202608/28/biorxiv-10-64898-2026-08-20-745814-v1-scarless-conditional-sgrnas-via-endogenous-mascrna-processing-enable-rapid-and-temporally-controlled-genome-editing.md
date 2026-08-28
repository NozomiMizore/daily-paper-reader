---
title: Scarless conditional sgRNAs via endogenous mascRNA processing enable rapid and temporally controlled genome editing
title_zh: 通过内源性mascRNA加工实现无疤痕条件性sgRNA，从而快速且时间可控地进行基因组编辑
authors: "Hart, C., Devakumar, L. P. S., Saeed, K., Spruce, A., Mastrokalou, C., Lukasiak, S., Ross-Thriepland, D., Walter, D., Gupta, N."
date: 2026-08-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.20.745814v1.full.pdf"
tags: ["query:virtual-cell"]
score: 7.0
evidence: 时间可控sgRNA扰动工具，改进混合扰动筛选以生成响应数据
tldr: "时间精准的基因编辑对研究动态过程和必需基因功能至关重要。现有Cre依赖的sgRNA开关会在成熟sgRNA上残留loxP来源的5'序列疤痕，损害引导功能。本文开发无疤痕条件sgRNA平台，将MALAT1相关mascRNA模块置于向导序列上游，经Cre重组后由RNase P/Z切除残余序列，恢复天然5'端。相比传统开关，该设计保持严格关闭态，同时提升开启态编辑效率、动力学和穿透性，可用于时序功能基因组学与混合筛选。"
source: biorxiv
selection_source: fresh_fetch
motivation: "现有Cre-loxP条件sgRNA开关会在成熟sgRNA上留下5'序列疤痕，损伤引导功能，需开发无疤痕设计。"
method: "将mascRNA模块置于sgRNA上游，经Cre重组后利用内源RNase P和RNase Z去除loxP残余，恢复天然5'末端。"
result: 针对内源表面标记基因，无疤痕开关在保持关闭态的同时，比传统设计编辑更快、穿透性更强、效率更一致。
conclusion: 该模块化策略实现条件CRISPR编辑且保持引导RNA完整性，适用于时序功能基因组学和混合筛选。
---

## 摘要
基因编辑的精确时间控制对于研究动态生物学过程、探究必需基因功能以及提高混合扰动筛选的可解释性至关重要。Cre依赖性单向导RNA（sgRNA）开关通过将引导激活与位点特异性重组偶联来提供时间调控，但现有设计在成熟sgRNA上保留了一个源自loxP的5'序列（疤痕），这可能损害引导功能。我们开发了一种无疤痕条件性sgRNA平台，该平台将Cre-loxP重组与内源性RNA加工相结合，在诱导后恢复天然sgRNA结构。一个MALAT1相关小胞质RNA（mascRNA）模块被定位在引导序列上游，使得在Cre介导的重组后，细胞RNase P和RNase Z能够去除残留的loxP衍生突出端，生成具有真实5'末端的成熟sgRNA。使用靶向内源性细胞表面标记基因的引导序列，与常规Cre激活的sgRNA开关相比，该无疤痕设计保持了严格的OFF状态控制，同时提高了ON状态编辑性能，从而实现了更快的编辑动力学、更大的扰动外显率和更一致的编辑效率。这种模块化策略为条件性CRISPR基因组编辑提供了一种简单方法，可保留引导完整性，并应易于适用于时间分辨功能基因组学和混合筛选应用。

## Abstract
Precise temporal control of gene editing is essential for studying dynamic biological processes, interrogating essential gene function, and improving the interpretability of pooled perturbation screens. Cre-dependent single guide RNA (sgRNA) switches provide temporal regulation by coupling guide activation to site-specific recombination, but existing designs retain a loxP-derived 5' sequence (scar) on the mature sgRNA that can impair guide function. We developed a scarless conditional sgRNA platform that combines Cre-loxP recombination with endogenous RNA processing to restore the native sgRNA architecture following induction. A MALAT1-associated small cytoplasmic RNA (mascRNA) module was positioned upstream of the guide sequence such that, after Cre-mediated recombination, cellular RNase P and RNase Z remove the residual loxP-derived overhang, generating a mature sgRNA with an authentic 5' terminus. Using guides targeting endogenous cell-surface marker genes, the scarless design maintained stringent OFF-state control while improving ON-state editing performance compared with a conventional Cre-activated sgRNA switch, resulting in faster editing kinetics, greater perturbation penetrance, and more consistent editing efficiency. This modular strategy provides a simple approach for conditional CRISPR genome editing that preserves guide integrity and should be readily adaptable to time-resolved functional genomics and pooled screening applications.