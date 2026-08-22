---
title: AlphaGenome deletion responses complement supervised enhancer-gene relation prediction in primary human astrocytes
title_zh: AlphaGenome缺失响应补充了原代人星形胶质细胞中受监督的增强子-基因关系预测
authors: "Huang, Z., Huang, R., Han, J."
date: 2026-08-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.14.744988v1.full.pdf"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 利用删除应答预测遗传扰动对增强子-基因关系的影响
tldr: 序列到功能模型可预测调控元件，但难以确定其调控的基因。本文评估AlphaGenome删除响应能否识别增强子-基因关系，采用冷冻K562分析和星形胶质细胞CRISPRi资源。结果AlphaGenome可区分功能关系，提升平均精度与对数损失，且与监督模型EGrf互补。研究支持其作为补充证据，而非替代监督模型或因果分配。
source: biorxiv
selection_source: fresh_fetch
motivation: 验证AlphaGenome删除响应是否蕴含增强子-基因关系，并衡量其对监督预测的增量价值。
method: 使用K562与星形胶质细胞CRISPRi数据，比较AlphaGenome与EGrf、距离等特征的预测性能。
result: AlphaGenome判别功能关系AP为0.479，加入基线特征后AP从0.396升至0.534，互补EGrf后AP从0.550升至0.619。
conclusion: AlphaGenome提供互补信号，但不支持其单独因果分配或优于监督模型。
---

## 摘要
序列到功能模型直接从DNA预测分子读数，但识别功能性调控元件并不等同于指定其所调控的基因。我们评估了AlphaGenome缺失响应是否能识别经实验支持的增强子-基因关系，使用了冻结的K562分析以及我们分析外部的一个原代人星形胶质细胞CRISPR干扰（CRISPRi）资源。K562平均对比度为正值但呈重尾分布，精确连接显示与已发布的Gasperini和ENCODE-rE2G资源直接冲突；因此我们将K562视为支持性证据。在对2307个AstroREG关系的冻结评估中，AlphaGenome缺失强度区分了133个功能关系与2174个功效充足的非功能关系（平均精确度0.479，增强子簇95%置信区间0.394-0.561，患病率0.058；受试者工作特征曲线下面积0.726，0.659-0.786）。将AlphaGenome添加到距离、ABC分数、增强子长度、测量表达和测定深度背景中，将增强子分组的折叠外平均精确度从0.396提高到0.534，并将对数损失从0.169改善到0.150。作者们的交叉拟合EGrf分数单独更强（平均精确度0.559）；在同时保留基因和增强子折叠的事后校准中，添加AlphaGenome将平均精确度从0.550提高到0.619（配对增强子簇增量0.068，区间0.023-0.115），并将对数损失从0.143改善到0.132。该比较具有不对称输入：EGrf在AstroREG标签上受监督，并使用局部表观基因组和背景特征，而AlphaGenome分数在本研究中未针对这些标签或该特征面板进行拟合，而是从预先存在的原代星形胶质细胞RNA-seq输出轨道读取。事后同增强子分析给出条件AUC 0.741（0.663-0.814）；较小的同基因分析（34个基因，155个关系）给出0.701（0.571-0.823）。AstroREG标签和EGrf输出在AlphaGenome公开发布之前是公开的，因此该评估是我们研究外部的，但不是发布后或经证明未见过的基准。结果支持互补的关系级效用，而非EGrf优越性、仅序列部署、任意位点的因果分配或序列缺失与CRISPRi之间的等价性。

## Abstract
Sequence-to-function models predict molecular readouts directly from DNA, but recognizing a functional regulatory element is not equivalent to assigning the gene it regulates. We evaluated whether AlphaGenome deletion responses identify experimentally supported enhancer-gene relations, using a frozen K562 analysis and a primary-human-astrocyte CRISPR interference (CRISPRi) resource external to our analysis. The K562 mean contrast was positive but heavy-tailed, and exact joins showed direct collision with released Gasperini and ENCODE-rE2G resources; we therefore treated K562 as supporting evidence. In a frozen evaluation of 2,307 AstroREG relations, AlphaGenome deletion strength discriminated 133 functional relations from 2,174 well-powered nonfunctional relations (average precision 0.479, enhancer-cluster 95% confidence interval 0.394-0.561, prevalence 0.058; area under the receiver-operating-characteristic curve 0.726, 0.659-0.786). Adding AlphaGenome to distance, ABC score, enhancer length, measured expression and assay-depth context increased enhancer-grouped out-of-fold average precision from 0.396 to 0.534 and improved log loss from 0.169 to 0.150. The authors' cross-fitted EGrf score was stronger alone (average precision 0.559); in a post-hoc calibration that held out both gene and enhancer folds, adding AlphaGenome increased average precision from 0.550 to 0.619 (paired enhancer-cluster increment 0.068, interval 0.023-0.115) and improved log loss from 0.143 to 0.132. This comparison had asymmetric inputs: EGrf was supervised on AstroREG labels and used local epigenomic and context features, whereas the AlphaGenome score was not fitted in this study to those labels or that feature panel but was read from a pre-existing primary-astrocyte RNA-seq output track. A post-hoc same-enhancer analysis gave conditional AUC 0.741 (0.663-0.814); a smaller same-gene analysis (34 genes, 155 relations) gave 0.701 (0.571-0.823). AstroREG labels and EGrf outputs were public before AlphaGenome's public release, so this evaluation is external to our study but not a post-release or proven-unseen benchmark. The results support complementary relation-level utility, not EGrf superiority, sequence-only deployment, causal assignment at arbitrary loci or equivalence between sequence deletion and CRISPRi.

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 1. 核心问题与整体含义（研究动机与背景）

- **背景**：序列到功能（sequence-to-function）模型能够直接从DNA序列预测分子读数（如染色质可及性、转录等），近年来在调控基因组学中展现出强大能力。然而，识别一个“功能性调控元件”并不等同于确定它调控哪个基因——增强子-基因（enhancer-gene）关系的分配是调控基因组学中的关键难题。
- **核心问题**：本文旨在评估AlphaGenome（一种序列到功能模型）的**缺失响应（deletion response）** 是否能够有效识别经实验支持的增强子-基因关系。具体来说，就是检查模型的序列删除预测信号是否蕴含了"哪个增强子调控哪个基因"这一关系级信息。
- **整体含义**：该研究探讨了基础模型（AlphaGenome）在关系级任务上的**零样本/未微调**能力，以及与监督模型（EGrf）的**互补性**，而不是替代性。研究结论对"仅靠序列模型部署"的可行性持谨慎态度，明确不支持将序列缺失预测等同于CRISPRi实验证据。

---

### 2. 方法论：核心思想、技术细节与流程

- **核心思想**：利用AlphaGenome在给定增强子区域发生序列删除时对目标基因表达变化的预测强度（即"缺失响应"）作为增强子-基因关系的证据信号。若某增强子的删除导致某基因的预测表达显著下降，则二者可能存在调控关系。
- **工作流程**：
  1. **K562分析（支持性证据）**：在K562细胞系中计算AlphaGenome缺失响应的平均对比度，观察其分布特征；将精确连接（exact joins）与已发布的Gasperini和ENCODE-rE2G增强子-基因资源进行直接比对，发现存在冲突，因此仅将其视为支持性证据而非主要基准。
  2. **AstroREG主评估（冻结评估）**：从预先存在的原代星形胶质细胞RNA-seq输出轨道中读取AlphaGenome缺失响应分数（未在本研究中对AstroREG标签或特征面板进行任何拟合），与2307个AstroREG增强子-基因关系进行匹配，评估其区分功能关系与非功能关系的能力。
  3. **特征增强与模型比较**：将AlphaGenome作为附加特征，加入包含距离、ABC分数、增强子长度、测量表达和测定深度上下文的基线模型，对比加入前后的性能；再将AlphaGenome与EGrf（监督模型）结合，检验互补增益。
  4. **事后分析**：进行同增强子（same-enhancer）条件分析和同基因（same-gene）分析，进一步检验信号的稳健性。
- **评价指标**：平均精确度（Average Precision, AP）、受试者工作特征曲线下面积（AUC）、对数损失（log loss），并使用增强子分组的置信区间（95% CI）进行统计评估。

---

### 3. 实验设计：数据集、基准与对比方法

- **数据集/场景**：
  - **K562场景**（支持性证据）：使用Gasperini和ENCODE-rE2G已发布的增强子-基因关系资源，对AlphaGenome缺失响应进行冻结分析。
  - **AstroREG场景**（主要评估）：使用2307条原代人星形胶质细胞增强子-基因关系，其中133条为功能关系（经CRISPRi实验验证），2174条为功效充足的非功能关系（患病率0.058）。
- **Benchmark**：AstroREG标签（CRISPRi实验支持的功能关系）作为金标准；评估采用增强子分组的折叠外（out-of-fold）预测方式，保证评估的客观性。
- **对比方法**：
  - **基线特征组合**：距离、ABC分数、增强子长度、测量表达、测定深度。
  - **EGrf**：作者此前发布的监督模型，在AstroREG标签上训练，使用局部表观基因组和背景特征。
  - **AlphaGenome单独** vs **AlphaGenome + 基线特征** vs **EGrf单独** vs **EGrf + AlphaGenome**。

---

### 4. 资源与算力

- **论文中未明确提及**具体的GPU型号、数量、训练时长或任何硬件资源配置信息。
- 值得注意的是，本研究未对AlphaGenome进行微调或训练，只是读取其预生成的输出轨道，因此**计算开销主要在于推理和特征评估**，而非训练；但论文对此也未给出量化细节。

---

### 5. 实验数量与充分性

- **实验数量**：
  - 1个K562支持性分析；
  - 1个AstroREG主评估（2307条关系）；
  - 4种模型配置对比（基线、基线+AlphaGenome、EGrf、 EGrf+AlphaGenome）；
  - 2个事后分析（同增强子分析、同基因分析，后者仅34个基因、155条关系）。
- **充分性评价**：
  - **优点**：实验设计包含多个层面的对比和消融，统计推断使用置信区间，并特别强调了"增强子分组"策略以避免膨胀的伪复现。
  - **不足**：事后同基因分析样本量极小（34个基因）；K562分析因与已发布资源冲突而仅作为辅助证据，降低了整体证据的覆盖面。总体而言，实验数量不算多，但针对问题聚焦性较好；**公平性**上论文做了细致讨论（见下一节）。

---

### 6. 主要结论与发现

- **AlphaGenome缺失响应包含关系级信号**：在AstroREG冻结评估中，AlphaGenome缺失强度能够区分功能与非功能关系（AP=0.479，AUC=0.726），表明其信号蕴含部分增强子-基因关系信息。
- **对基线模型具有增量价值**：加入AlphaGenome后，基线模型的AP从0.396提升至0.534，对数损失从0.169改善至0.150。
- **与EGrf互补而非替代**：单独EGrf更强（AP=0.559），但在事后校准（同时留出基因和增强子折叠）中，加入AlphaGenome将AP从0.550提升至0.619（配对增强子簇增量0.068），对数损失从0.143改善至0.132。
- **信号具有条件特异性**：同增强子条件分析AUC=0.741，同基因分析AUC=0.701（但样本量小），说明AlphaGenome提供了部分独立于基因/增强子身份的信息。
- **明确的边界声明**：结果支持**互补的关系级效用**，但**不支持**以下主张：EGrf优于AlphaGenome、仅序列部署可行、任意位点的因果分配、或序列删除预测等价于CRISPRi实验。

---

### 7. 优点

- **评估的外部性设计**：AstroREG标签和EGrf输出在AlphaGenome公开发布前就已公开，且AlphaGenome分数未针对这些标签或特征面板进行拟合，避免了直接过拟合嫌疑。
- **诚实的偏差披露**：论文明确指出评估虽外在于研究，但并非"发布后未见"基准，不夸大其独立验证性质。
- **统计严谨**：采用增强子分组的置信区间、冻结评估、折叠外预测，并使用多种互补指标（AP、AUC、log loss）。
- **对称性反思**：明确讨论了比较的不对称输入（EGrf有监督和局部特征 vs AlphaGenome零样本通用模型），有利于读者正确解读结果。
- **结论克制**：未过度宣称AlphaGenome的因果推断能力，清晰划定了结论边界。

---

### 8. 不足与局限

- **K562证据薄弱**：AlphaGenome的K562预测与已发布的Gasperini和ENCODE-rE2G资源存在直接冲突，导致主要结论只能依赖单一细胞类型（星形胶质细胞）的AstroREG数据。
- **评估非完全独立**：虽然标签早于AlphaGenome公开发布，但作者无法证明AlphaGenome的训练数据中未包含这些区域或相关特征，因此不能视为严格意义上的"盲测"。
- **样本量局限**：功能关系仅133条（患病率仅5.8%），同基因分析更是只有34个基因，统计功效有限，细分分析结果稳健性不足。
- **不能证明因果性**：缺失响应预测与CRISPRi实验之间存在本质差异（计算预测≠真实扰动），论文也明确承认二者不可等价。
- **应用限制**：结果不支持仅凭AlphaGenome进行任意位点的因果分配；在序列缺失预测与真实实验证据融合方面，仍需监督模型或实验验证配合。
- **算力/可复现性细节缺失**：未报告推理所需的硬件资源和时间，增加了复现成本的不确定性。

---

（完）
