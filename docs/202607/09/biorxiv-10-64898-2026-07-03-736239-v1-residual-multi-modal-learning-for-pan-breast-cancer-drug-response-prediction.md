---
title: Residual Multi-Modal Learning for Pan-Breast-Cancer Drug Response Prediction
title_zh: 残差多模态学习用于泛乳腺癌药物反应预测
authors: "Huang, B., Tasaka, L., Li, J., Islam, T., Zhang, S."
date: 2026-07-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.03.736239v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 预测癌细胞系的药物敏感性
tldr: 针对泛癌药物反应预测中细胞系数据稀缺、模型泛化性差的问题，提出DL4DR双塔残差融合深度学习模型。细胞系塔将基因表达、突变和拷贝数变异编码为类RGB基因组图像，避免身份依赖；化合物塔结合图神经网络、八度卷积和ECFP硬记忆。通过残差融合平衡泛化与活性悬崖分辨率。在51个乳腺癌细胞系中超越基线，留一细胞系验证平均ΔR²=0.016，外部601细胞系泛化中位R²达0.627。GradCAM解释性揭示TP53等已知驱动基因。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736239-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1320, \"height\": 1223, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736239-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 894, \"height\": 722, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736239-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1484, \"height\": 1120, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736239-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1533, \"height\": 613, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736239-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1536, \"height\": 623, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736239-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1535, \"height\": 625, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736239-v1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 853, \"height\": 1027, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736239-v1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1553, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736239-v1/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1554, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736239-v1/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1264, \"height\": 1083, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736239-v1/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1382, \"height\": 1500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-03-736239-v1/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1218, \"height\": 708, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-03-736239-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1349, \"height\": 385, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-03-736239-v1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1024, \"height\": 666, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-03-736239-v1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1329, \"height\": 506, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-03-736239-v1/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1391, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-03-736239-v1/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1207, \"height\": 345, \"label\": \"Table\"}]"
motivation: 现有方法对数据稀缺细胞系易过拟合，且无法泛化到未见生物学背景，需内容驱动、无身份标识的基因组条件化模型。
method: 双塔残差融合：细胞系塔用卷积编码3×139×139基因组图像；化合物塔融合D-MPNN、ORNN和ECFP；预测为ECFP基线加经门控λ调控的残差交互项。
result: 51个乳腺癌细胞系中48/51超越基线，留一线系泛化平均ΔR²=0.016，外部601细胞系中位R²=0.627（与随机划分相当）。
conclusion: 提出无身份标识的基因组图像编码和残差融合范式，实现泛癌药物反应泛化，并通过解释性部分验证生物学合理性。
---

## 摘要
预测不同癌细胞系的药物敏感性仍然是精准肿瘤学中的一个基本挑战，特别是对于数据稀缺的细胞系，每个细胞系的模型容易过拟合，而查找表方法无法泛化到未见过的生物学情境。我们提出了 DL4DR，一种双塔残差后期融合深度学习模型，通过基于内容的、无身份标识的基因组条件化来解决这一挑战。细胞系塔将每个细胞系编码为 3 x 139 x 139 的基因组图像——将基因表达、突变严重程度和拷贝数变异编码为 RGB 通道——使用一个直接从生物学内容映射的卷积编码器，从不使用细胞系 ID。化合物塔结合了三种互补的分子表征：D-MPNN 图消息传递、ORNN 八度卷积图像特征，以及一个保持活性悬崖分辨率的 ECFP 硬记忆头。预测被组成一个残差和：f = f_hard + λ(z_c)·f_residual，其中学习门 λ 调节有多少交互信号补充记忆基线。在 51 个乳腺癌细胞系（136,342 条记录）上的评估中，残差融合在 48/51 个细胞系（94.1%）上优于 ECFP 仅基线，其中 26/51 个细胞系（51.0%）的 ΔR² > 0.02。在留出细胞系划分（基因组泛化性的决定性测试）上，所有 51 个细胞系的平均 ΔR² = 0.016，表明基因组编码器学习了超越细胞系身份的可转移生物学信号。在 27 种癌症组织类型的 601 个细胞系上的外部验证（CellTiter-Glo 数据集；与训练集无细胞系重叠）达到了中位 R² = 0.627，在内部随机划分性能范围（R² = 0.61–0.69）内，证实了泛癌症泛化性。细胞系塔上的 GradCAM 可解释性在跨细胞系基因组激活因子中恢复了 TP53（5/51 个细胞系），以及几个未表征的候选基因（例如 FSIP2，6/51）——无需任何先验通路注释——为学习到的表征提供了部分生物学验证，同时也表明编码器排名最高的信号中有相当大一部分对应于目前未被注释为乳腺癌驱动因素的基因。代码和数据可在 https://github.com/bayjuan5/DL4DR 获取。

## Abstract
Predicting drug sensitivity across diverse cancer cell lines remains a fundamental challenge in precision oncology, particularly for data-scarce cell lines where per-cell-line models overfit and lookup-table approaches cannot generalise to unseen biological contexts. We present DL4DR, a Two Tower Residual Late Fusion deep learning model that addresses this challenge through content-based, identity-free genomic conditioning. The Cell Line Tower encodes each cell line as a 3 x 139 x 139 genomic image - encoding gene expression, mutation severity, and copy-number variation as RGB channels - using a convolutional encoder that maps directly from biological content, never from a cell line ID. The Compound Tower combines three complementary molecular representations: D-MPNN graph message passing, ORNN octave convolutional image features, and an ECFP hard-memorization head that preserves activity-cliff resolution. Predictions are composed as a residual sum: f = fhard + {lambda}(zc). fresidual, where the learned gate $\lambda$ modulates how much interaction signal supplements the memorization baseline. Evaluated across 51 breast cancer cell lines(136,342 records), Residual Fusion outperforms the ECFP-Only baseline in 48/51 cell lines (94.1%), with {Delta}R2 > 0.02 in 26/51 (51.0%). On the leave-cell-line-out split - the decisive test of genomic generalisation - the mean {Delta} R2 = 0.016 across all 51 lines demonstrates that the genomic encoder learns transferable biological signal beyond cell line identity. External validation on 601 cell lines across 27 cancer tissue types (CellTiter-Glo dataset; 0 cell line overlap with training) achieves median R2 = 0.627, within the range of the internal random-split performance (R2 = 0.61--0.69), confirming pan-cancer generalisation. GradCAM interpretability on the Cell Line Tower recovers TP53 among the top-five cross-cell-line genomic activators (5/51 cell lines) alongside several uncharacterised candidate genes (e.g.FSIP2, 6/51) - without any prior pathway annotation - providing partial biological validation of the learned representation, while also indicating that a substantial share of the encoder's top-ranked signal corresponds to genes with no current annotation as breast cancer drivers. Code and data are available at https://github.com/bayjuan5/DL4DR.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：精准肿瘤学中，预测不同癌细胞系对药物的敏感性（即药物反应预测）是一个基本挑战。现有方法在数据稀缺的细胞系上容易过拟合（per‑cell‑line 模型）或无法泛化到未见的生物学情境（基于查找表的细胞系编码模型）。关键是，许多实际应用（如药物重定位、患者来源类器官预测）需要模型对从未训练过的细胞系进行零样本推理。
- **核心问题**：如何同时解决两个瓶颈：(a) 化合物表征中的活性悬崖（activity cliff）分辨与结构泛化矛盾；(b) 细胞系表征中对未见细胞系的泛化能力，避免依赖细胞系 ID 的查找表。
- **背景**：现有主流方法（ECFP + MLP、GNN）各有局限：ECFP 能记住活性悬崖但无法泛化到结构新颖化合物；GNN 可学习可表征但深度增大时过平滑，丢失局部结构；细胞系查找表嵌入本质上无法处理未见过的细胞系。本文提出 **DL4DR**，通过内容驱动、无身份标识的基因组图像条件化实现真正的泛化。

## 2. 方法论：核心思想、关键技术细节、公式或算法流程

### 2.1 核心思想

- **残差融合原则**：将预测分解为“硬记忆基线（ECFP 主效应）”与“门控交互残差（基于注意力机制的细胞系‑化合物交互修正）”，两者相加。门控 λ(z_c) 控制交互项贡献，当 λ→0 时退化为纯记忆模型，保证结构上不退化。
- **内容基矩阵补全**：化合物轴由 SMILES 分子结构参数化；细胞系轴由基因组图像参数化，不使用任何 ID 信息，实现零样本泛化。

### 2.2 关键技术细节

- **双塔架构**：
  - **化合物塔**：结合三种互补表征：
    - **ECFP 硬记忆头**：固定哈希指纹 + MLP，捕捉活性悬崖。
    - **D‑MPNN 图神经网络**：消息传递学习任务自适应的分子表征，但深度过大时过平滑。
    - **ORNN 八度卷积图像编码器**：将 SMILES 渲染为 2D 分子图像，利用高‑低频分解保留局部与全局结构信息。
  - **细胞系塔**：将每个细胞系编码为 **3×139×139 RGB 图像**（通道 R：基因表达；通道 G：表达×突变严重性；通道 B：保留给拷贝数变异）。CNN 编码器直接从基因组内容映射到嵌入 z_c，无细胞系 ID 维度。

- **残差融合公式**：
  \[
  f(\text{compound, cell line}) = f_{\text{hard}}(x_{\text{ECFP}} \oplus z_c) + \lambda(z_c) \cdot f_{\text{residual}}\bigl(\text{CrossAttn}(Q=z_c, K/V=[z_{\text{ORNN}}, z_{\text{DMPNN}}])\bigr)
  \]
  其中 λ(z_c) ∈ [0,1] 是学习的标量门，基于基因组嵌入调节交互项。

- **训练细节**：
  - 损失函数：Huber 损失（SmoothL1）+ ℓ2 正则化。
  - 采样策略：√·温度采样（α=0.5），将细胞系不平衡从 2050:1 降至约 45:1。
  - 实现：PyTorch，Google Colab（NVIDIA Tesla T4 GPU），GroupNorm 用于细胞系塔。

## 3. 实验设计：数据集、场景、benchmark、对比方法

### 3.1 数据集

- **训练集**：BREAST‑136344‑56786‑51（来自 DepMap GDSC2），包含 51 个乳腺癌细胞系、56785 个唯一化合物、136342 条记录，矩阵密度仅 4.71%，极度稀疏。
- **外部验证集**：CellTiter‑Glo 数据集，601 个细胞系（27 种组织类型），与训练集零细胞系重叠；化合物部分重叠（175/197 与训练集相同）。

### 3.2 评估场景（划分方式）

1. **随机划分**（80/10/10 行级）：性能上界，存在插值泄露。
2. **留化合物**（GroupKFold 按 smi_id）：测试化合物塔对结构新颖分子的泛化。
3. **留细胞系**（GroupKFold 按 ACH ID）：决定性测试，查找表基线未定义，ΔR²>0 代表真正的基因组泛化。

### 3.3 对比方法

- 基线：全局均值、每细胞系均值、每化合物均值、**加性基线**（per‑cell‑line mean + per‑compound mean − global mean）。
- 核心对比：**ECFP‑Only MLP**（仅使用 ECFP 硬记忆头）vs. **残差融合**（ECFP + ORNN + D‑MPNN + ChemBERT 等变体）。
- 消融实验：八度比 α ∈ {0.25, 0.50, 0.75, 0.90}，在不同数据量级细胞系上比较。

### 3.4 Benchmark

- 内部 51 个乳腺癌细胞系留细胞系划分：残差融合在 48/51 细胞系上优于 ECFP‑Only，平均 ΔR²=0.016；26/51 的 ΔR²>0.02。
- 外部 601 细胞系：中位 R²=0.627，与内部随机划分性能（0.61–0.69）相当。

## 4. 资源与算力

- **文中明确提及**：模型在 **Google Colaboratory** 上训练，使用 **NVIDIA Tesla T4 GPU**（未提及数量，通常为单卡或单进程）。训练时长未明确给出，但从描述（epoch 52 达到最高验证 R²=0.718）可推断训练数小时至数十小时。未说明具体 GPU 数量或总 GPU 小时数。

## 5. 实验数量与充分性

- **实验组数**：
  - 内部 benchmark：51 细胞系留细胞系划分，每个细胞系对比残差融合 vs. ECFP‑Only（共 51 组比较）。
  - 留化合物划分：在 6 个代表性细胞系上报告 R²。
  - 消融实验：3 个细胞系 × 4 种 α × 3 种模型配置（共 36 组子实验）。
  - 外部验证：601 细胞系 × 1 个模型（epoch 52），按组织类型聚合分析。
  - 解释性分析：化合物级（3 个化合物）和细胞系级（GradCAM 跨 51 细胞系 + 2 个案例）。
- **充分性与公平性**：
  - 数据泄露验证严格：检查了组别独享性、行级去重、基因组图像唯一性（MD5 哈希差异），确保留细胞系结果不是由泄露引起。
  - 对比了必要的加性基线（很多同行未做）。
  - 消融实验覆盖了关键超参数 α 和不同数据量级细胞系，分析细致。
  - **不足**：未与最新的多模态方法（如 DeepDTF）进行直接数值比较（文中仅在引言对比了思想，但未在相同数据上重跑对比实验）。此外，实验仅限于乳腺癌训练，泛化性虽经外部验证但仅在一个训练条件下。总体实验设计较充分，但横向比较不够全面。

## 6. 主要结论与发现

- **残差融合有效**：在 94.1% 的乳腺癌细胞系上优于 ECFP 纯记忆基线，且未导致任何有意义退化（3/51 退化在方差内）。
- **基因组编码器真正泛化**：留细胞系测试平均 ΔR²=0.016，外部验证中位 R²=0.627，且泛化性呈现生物学合理的组织类型梯度（乳腺癌最高，上皮癌中等，造血系统最低），说明模型学习的是基因组内容而非组织标签。
- **GradCAM 部分恢复已知癌症驱动基因**：TP53 出现在跨细胞系激活因子前列（5/51），BRCA2 也在特定细胞系中被识别，但同时也发现大量未注释候选基因（如 FSIP2），表明编码器学到的信号并非仅由已知驱动基因主导。
- **残差结构非退化保证**：即使软分支贡献噪声，门控 λ 可抑制之，确保性能不会低于基线。
- **活性悬崖分辨率与结构泛化兼顾**：ECFP 硬记忆头保留活性悬崖分辨，而 D‑MPNN、ORNN、ChemBERT 提供结构泛化能力。

## 7. 优点：方法或实验设计亮点

- **无身份标识的基因组图像编码**：创新地将基因组状态（表达、突变、CNV）编码为多通道图像，使用 CNN 直接映射生物学内容，避免了查找表泛化失败的根本问题。
- **残差融合设计**：严格保证结构非退化，将主效应与交互效应分离，数学上优雅且实用。
- **全面的泄露验证**：显式检查组别独享性、行级重复、图像 MD5 哈希，增强结果可信度。
- **外部验证规模大**：601 细胞系 27 组织类型，且零重叠，展示了模型的跨癌种泛化能力。
- **解释性分析有生物学验证**：GradCAM 恢复 TP53、BRCA2 等已知驱动基因，提供部分生物学合理性证据，并诚实地报告了主导信号是未注释基因，不夸大。
- **代码与数据开放**：GitHub 仓库便于复现和扩展。

## 8. 不足与局限

- **训练数据范围局限**：仅使用 51 个乳腺癌细胞系训练，外部验证虽跨癌种，但泛化可能因训练数据单一而受限于基因组距离（造血系统性能低）。作者自己也指出应扩展到全 DepMap 泛癌数据集。
- **解释性结果存在检查点依赖性**：TP53 的排名在早期检查点更突出，在最佳验证 R² 检查点有所减弱。作者诚实地指出了这一点，但未提供多检查点聚合分析，影响稳定性。
- **未与最新多模态方法定量对比**：如 DeepDTF 等使用多组学融合的模型，文中仅在引言思想对比，未在相同数据上重现比较。
- **化合物覆盖局限性**：59% 的化合物仅在一个细胞系中测试，交互信号学习极其受限。
- **CNN 编码器缺乏基因网络先验**：当前架构未利用基因调控网络或预训练基因组模型，改进方向（Geneformer、scGPT）已提及但未验证。
- **计算资源报告不详细**：未说明训练总时长、GPU 数量，不利于复现或估计大规模扩展所需算力。
- **应用限制**：模型输入需要基因组图像（表达、突变、CNV），对于一些临床样本可能数据缺失或不完整；仅预测 IC50，未涉及更丰富的药物反应指标（如 AUC、生长抑制百分数）。

（完）
