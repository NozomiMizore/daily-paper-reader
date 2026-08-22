---
title: Decoding Tumour-Specific Rewiring and Synthetic Lethality Through Genome-Scale Metabolic Models
title_zh: 解码肿瘤特异性代谢重连与合成致死性：基于全基因组尺度代谢模型
authors: "Ibrahim, M., Bhoite, R., Lakshmanan, M., Raman, K."
date: 2026-08-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.21.746174v1.full.pdf"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 通过代谢模型预测基因扰动的细胞响应
tldr: 癌症细胞通过代谢重编程支持失控增殖，但不同肿瘤的代谢改变及可用药靶点尚待系统解析。本文利用TCGA基因表达数据构建八种组织的上下文特异基因组规模代谢模型，通过通量富集分析揭示组织特异代谢通路改变，如乳腺癌中支链氨基酸代谢受抑。进一步提出模型驱动流程，预测正常组织的合成致死反应与癌症的单致死对应物，识别代谢‘附带致死’反应对，并用DepMap数据验证多个基因对。该框架为解码肿瘤代谢重编程和合成致死脆弱性提供系统方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法难以系统刻画不同癌症类型的代谢重编程及其治疗靶点，需要基于代谢模型的框架来发现组织特异的代谢脆弱性。
method: 构建八种组织的基因组规模代谢模型，结合TCGA表达数据，用通量富集分析识别差异通路，并通过合成致死反应配对寻找代谢附带致死靶点。
result: 发现多种组织特异代谢通路变化，预测CMPK1-AK、ALDOA-PGD等附带致死基因对，并经DepMap数据验证。
conclusion: 该框架可解码肿瘤代谢重编程并揭示可靶向的合成致死脆弱性，为精准治疗提供新策略。
---

## 摘要
癌细胞迅速重新布线其代谢，从高效的能量产生转向合成代谢过程，以支持不受控制的生长。解码这种代谢转变对于发现新的治疗靶点至关重要。为了绘制不同类型癌症的系统级代谢变化，我们使用来自癌症基因组图谱（TCGA）的基因表达数据，为八种组织（肺、甲状腺、胃、前列腺、肝、肾、结肠和乳腺）构建了情境特异性的全基因组尺度代谢模型。应用基于约束的建模，我们随后通过通量富集分析鉴定了差异调控的通路，揭示了组织特异性的重连：支链氨基酸代谢在乳腺癌中受到抑制；鞘脂代谢在结肠癌、肾癌和甲状腺癌中下调，但在乳腺癌中上调。我们进一步提出了一个模型驱动的管道来识别和表征代谢脆弱性。我们首先鉴定正常组织中的合成致死反应及其在癌症中对应的单一致死对应物，从而能够为每种癌症识别代谢“附带致死”反应对。模型预测的附带致死基因对，包括结肠模型中的CMPK1-AK、前列腺模型中的ALDOA-PGD和肝脏模型中的SLC25A26-UQCRB，通过使用DepMap基因必需性数据的计算验证得到了支持。随后，我们展示了如何在考虑任何附带致死对的同时解释癌症组织中的代谢重连。总之，我们的结果为解码癌症中的代谢重连和合成致死脆弱性建立了一个系统性框架。

## Abstract
Cancer cells rapidly rewire their metabolism, from efficient energy production toward anabolic processes, to sustain uncontrolled growth. Decoding such metabolic shifts is essential for uncovering novel therapeutic targets. To map systems-level metabolic changes across cancer types, we built context-specific genome-scale metabolic models for eight tissues (lung, thyroid, stomach, prostate, liver, kidney, colon, and breast) using gene expression data from The Cancer Genome Atlas (TCGA). Applying constraint-based modelling, we then identified differentially regulated pathways through flux enrichment analysis, revealing tissue-specific rewiring: branched chain amino acid metabolism was suppressed in breast cancer; sphingolipid metabolism was downregulated in colon, kidney, and thyroid but upregulated in breast. We further propose a model-driven pipeline to identify and characterise metabolic vulnerabilities. We first identify synthetic lethal reactions in normal tissues and their corresponding single lethal counterparts in cancers, thereby enabling the identification of metabolic "collateral lethal" reaction pairs for each cancer. Model-predicted collateral lethal gene pairs, including CMPK1-AK in colon, ALDOA-PGD in prostate, and SLC25A26-UQCRB in liver models, were supported through computational validation using DepMap data on gene essentiality. Subsequently, we show how to interpret metabolic rewiring in cancer tissues while accounting for any collateral lethal pairs. In summary, our results establish a systemic framework for decoding metabolic rewiring and synthetic lethal vulnerabilities in cancer.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义

**研究动机与背景**

- 癌细胞会将代谢从高效能量生产转向合成代谢过程，以支持不受控制的增殖。这种代谢重编程是癌症的核心特征之一，也是潜在治疗靶点的重要来源。
- 然而，不同癌种、不同组织来源的肿瘤，其代谢改变模式高度异质，目前缺乏系统级方法对跨癌种的代谢重连进行刻画和比较。
- 现有研究多聚焦单一癌种或少数代谢通路，难以解析肿瘤类型特异的代谢脆弱性，也难以系统地发现可靶向的合成致死（synthetic lethality）关系。
- 因此，作者提出利用全基因组尺度代谢模型（genome-scale metabolic models, GSMMs）对八种组织的癌症代谢重编程进行系统解码，并在此基础上识别潜在的代谢脆弱性靶点。

## 2. 方法论

**核心思想**

- 构建组织特异性的全基因组尺度代谢模型，借助约束性建模（constraint-based modelling）将TCGA转录组数据转化为功能层面的代谢通路活性差异，从而在系统水平识别肿瘤代谢重连。
- 进一步提出一个模型驱动的“附带致死”（collateral lethality）识别流程：先在正常组织中寻找合成致死反应对，再检验癌症中是否有对应的单一致死反应，据此推断可靶向的代谢脆弱性。

**关键技术细节与流程**

1. **模型构建**

   - 使用TCGA基因表达数据，针对八种组织——肺、甲状腺、胃、前列腺、肝、肾、结肠和乳腺，分别构建组织特异性的全基因组尺度代谢模型。
   - 主要依赖基于约束的建模框架将表达数据映射到代谢反应上，生成每种组织（正常/癌）的情境特异模型。

2. **通量富集分析（Flux Enrichment Analysis）**

   - 对构建的模型执行通量变异性分析或类似通量采样方法后，对差异调控的通路进行系统性富集分析，识别出癌症中相对于正常组织显著上调或下调的代谢通路。

3. **附带致死反应对的识别管道**

   - 第一步：在正常组织模型中识别合成致死反应对——即两个反应单独被干扰时不致死、同时被干扰时致死的反应组合。
   - 第二步：确认在对应癌症模型中，每个合成致死对的其中一个成员是否变为单一致死（single lethal）。
   - 第三步：将满足条件的反应对归类为“附带致死”对，即在癌症中已有一个成员因代谢重连而受损时，抑制另一成员即可选择性杀伤癌细胞，同时不伤害正常细胞。
   - 第四步：将反应级结果映射到编码对应酶的基因上，形成附带致死基因对预测。

4. **验证整合**

   - 对模型预测的附带致死基因对，利用DepMap（DepMap Portal）的基因必需性数据从计算层面验证其合理性。

## 3. 实验设计

**数据集**

- **TCGA（The Cancer Genome Atlas）**：用于获取八种组织的癌症和正常样本的基因表达数据，驱动模型构建。
- **DepMap 基因必需性数据**：用于独立验证模型预测的附带致死基因对是否在真实功能基因组学筛选中表现出依赖性。

**研究覆盖场景**

- 涉及八种组织类型：肺、甲状腺、胃、前列腺、肝、肾、结肠、乳腺。
- 比较维度：每种组织内的癌 vs. 正常（癌旁），跨组织的通路差异比较。

**Benchmark / 对比方法**

- 论文未明确以其他已有算法为基准进行对比，核心是通过DepMap数据对模型预测进行独立计算验证，本质上是“模型预测 vs. 实验筛选数据”的验证式评估，而非传统意义上的方法A vs. 方法B基准测试。

## 4. 资源与算力

- 论文原文中没有明确提及使用的GPU型号、数量、训练时长或计算集群规模等算力信息。
- 由于所用方法主要是基于约束的建模、通量采样和富集分析，属于计算密集但并非深度学习训练类任务，推测以CPU集群运行为主，但原文并未披露具体计算资源。

## 5. 实验数量与充分性

**实验数量**

- 组织模型数量：8种组织，每种包含癌症与正常情境。
- 通量富集分析：覆盖8种组织，对差异通路进行了系统富集。
- 附带致死预测与验证：文中重点展示了三个模型预测的附带致死基因对经DepMap验证的案例：
  - 结肠模型中的 CMPK1-AK；
  - 前列腺模型中的 ALDOA-PGD；
  - 肝脏模型中的 SLC25A26-UQCRB。
- 此外还提出了在考虑附带致死对的同时解释癌症代谢重连的整合分析框架，但未给出全部基因对的完整列表或大型系统级汇总统计。

**充分性评估**

- 优点：跨8种组织构建模型，覆盖面广；通路富集分析和附带致死预测形成了从“描述性发现”到“可靶向预测”的完整链条；使用DepMap这一独立数据集进行验证，增加了结果可信度。
- 局限：验证部分仅明确列出少数几个代表性基因对，未展示全库预测基因对的整体验证率、灵敏度/特异性等统计指标；缺乏湿实验（如CRISPR或siRNA干扰实验）层面的功能性验证；没有与其他代谢模型或预测方法进行系统对比；不同癌种附带致死对数量分布、模型质量差异等细节未充分展开。因此，实验设计具备初步的系统性和合理性，但在统计全面性和外部验证深度上仍有不足。

## 6. 主要结论与发现

- 八种组织的癌症代谢重连具有明显的组织特异性，共享转运等基础代谢改变之外各有特征。

  - 乳腺癌中支链氨基酸（BCAA）代谢受抑制；
  - 鞘脂代谢在结肠癌、肾癌和甲状腺癌中下调，但在乳腺癌中上调。
- 成功提出并验证了模型驱动的附带致死识别管道，能够在正常组织的合成致死反应与癌症的单一致死反应的交集中定位癌症特异性代谢靶点。
- 模型预测的附带致死基因对（如CMPK1-AK、ALDOA-PGD、SLC25A26-UQCRB）在DepMap基因必需性数据中得到计算验证支持，证明该框架具有可操作性。
- 论文建立了一个通用的系统性框架，可同时解码肿瘤代谢重连与合成致死脆弱性，为精准癌症治疗提供新的靶点发现策略。

## 7. 优点

- **系统性 & 跨癌种视角**：将分析覆盖到八种组织类型，突破了既往单癌种研究的碎片化局限，利用同一框架进行跨组织可比分析。
- **从描述到预测的完整链条**：不仅识别代谢通路变化，还将其延伸至可操作的靶点预测，最终通过独立数据验证，形成了“发现—预测—验证”的科学闭环。
- **创新性概念引入**：将“附带致死”这一概念系统化地引入基于代谢模型的靶点发现流程，为利用肿瘤自身代谢重连选择性杀伤癌细胞提供了新的方法论思路。
- **生物学可解释性**：代谢模型本身自带生化反应与基因映射关系，预测结果可以直接解释为具体的代谢通路和酶靶点，便于实验验证。
- **数据驱动的客观性**：利用TCGA和DepMap公开权威数据集，分析流程可复现、可推广。

## 8. 不足与局限

- **验证深度有限**：目前主要依赖DepMap计算验证，缺乏CRISPR功能筛选或动物模型等湿实验验证来确证附带致死关系的实际作用。
- **统计全面性不足**：没有系统报告所有预测附带致死基因对的总体验证率、覆盖度以及DepMap验证结果在全部预测中的比例，代表性基因对的展示难以全面评估模型预测的整体性能。
- **未与其他方法对比**：没有与现有代谢模型工具（如传统通量平衡分析流程、基于回归的通路活性推断方法等）进行比较实验，难以判断该方法的相对优势。
- **表达数据驱动的固有局限**：基于转录组的模型构建忽略了翻译后调控、蛋白丰度与酶活性的偏差，可能引入系统性误差。
- **临床应用距离较远**：计算预测的靶点尚未经过药物抑制实验验证，距离临床转化仍有较大距离；附带致死的细胞特异性也需在更真实微环境条件下验证。
- **资源信息缺失**：未报告具体计算资源消耗和运行时间，不利于其他研究者评估可复现性与计算门槛。

（完）
