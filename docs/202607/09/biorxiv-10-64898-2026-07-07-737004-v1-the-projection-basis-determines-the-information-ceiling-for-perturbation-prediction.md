---
title: The projection basis determines the information ceiling for perturbation prediction
title_zh: 投影基决定了扰动预测的信息上限
authors: "BIANCO, S."
date: 2026-07-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.07.737004v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 扰动预测的信息上限
tldr: "扰动预测中深度学习模型不如PCA简单基线，根源在于投影基的信息上限：预测性能受基所解释的方差束缚。化学扰动下PCA捕获90-99%方差，而网络特征基仅10-12%；遗传扰动则相反。图小波利用全图频谱可同时恢复两类信号。这揭示了投影基必须匹配扰动模态的结构特性。"
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1668, \"height\": 674, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1668, \"height\": 580, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1670, \"height\": 596, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1080, \"height\": 516, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1081, \"height\": 551, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1235, \"height\": 672, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1181, \"height\": 910, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1687, \"height\": 555, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1691, \"height\": 550, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1699, \"height\": 522, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1314, \"height\": 399, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1209, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1280, \"height\": 381, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1569, \"height\": 698, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1327, \"height\": 508, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1355, \"height\": 291, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 916, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1229, \"height\": 380, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1226, \"height\": 378, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 913, \"height\": 922, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 930, \"height\": 422, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1237, \"height\": 1108, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1446, \"height\": 874, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1237, \"height\": 275, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1488, \"height\": 656, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1114, \"height\": 425, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1217, \"height\": 234, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1463, \"height\": 381, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1413, \"height\": 291, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1082, \"height\": 275, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1415, \"height\": 786, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-07-737004-v1/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1380, \"height\": 363, \"label\": \"Table\"}]"
motivation: 解释为何深度模型在扰动预测中无法超越PCA简单基线。
method: 证明预测与真实值的平方相关性受投影基解释方差的界限约束。
result: 化学扰动PCA优于网络基；遗传扰动网络基更佳；图小波可兼顾两类。
conclusion: 投影基选择需匹配扰动模态的底层结构（方差主导或网络级联）。
---

## 摘要
最近的基准测试表明，用于扰动预测的深度学习模型并不优于在主成分（PCA）空间中运行的简单基线。我们用信息论上限来解释这一点：对于任何标准正交投影基 Phi，预测与真实值之间的平方相关性受该基解释的方差限制（r² ≤ VE），因此没有模型复杂度可以恢复投影时丢弃的信号。在化学扰动（sciPlex3, LINCS L1000）上，基因关联网络的特征基仅捕获了药物响应方差的10-12%，并产生随机水平的预测，而PCA捕获了90-99%。基于同一网络的图小波恢复了约88%的方差，将药物信号定位在高频模式中，而标准的低通特征基则丢弃了这些模式。在CRISPRa遗传扰动上，排名反转：网络基在所有测试维度上均优于PCA。对拓扑结构、空网络和数据泄漏的控制实验证实了该效应是结构性的。正确的基取决于扰动模态：PCA捕获驱动化学响应的方差，网络基捕获驱动遗传响应的级联结构，而能够访问网络完整图谱谱的基（如图小波）则从同一拓扑中恢复两者。

## Abstract
Recent benchmarks show that deep-learning models for perturbation prediction do not outperform simple baselines operating in principal-component (PCA) space. We explain this with an information-theoretic ceiling: for any orthonormal projection basis Phi, the squared correlation between prediction and truth is bounded by the variance the basis explains (r2 [&le;] VE), so no model complexity can recover signal discarded at projection. On chemical perturbations (sciPlex3, LINCS L1000), the eigenbasis of a gene association network captures only 10-12% of drug-response variance and yields chance-level predictions, while PCA captures 90-99%. Graph wavelets built on the same network recover approx. 88%, localising the drug signal in high-frequency modes that the standard low-pass eigenbasis discards. On CRISPRa genetic perturbations the ranking inverts: the network basis outperforms PCA across all dimensions tested. Controls on topology, null networks and data leakage confirm the effect is structural. The right basis depends on the perturbation modality: PCA captures the variance that drives chemical responses, the network basis captures the cascade structure that drives genetic ones, and bases that access the network's full graph spectrum (such as graph wavelets) recover both from the same topology.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

深度学习方法（如 GEARS、CPA、scGen 等）在单细胞扰动预测任务中的表现被证明没有超过在 PCA 空间中运行的简单线性基线。这一现象此前被归因于模型容量或归纳偏置不足，但该论文提出一个不同的解释：**信息天花板**。具体来说，对于任何使用固定线性投影基（如 PCA、网络特征基）的模型，预测性能存在一个由投影基所解释的方差（VE）决定的硬上限——预测-真实相关系数的平方 \( r^2 \) 不超过该基的方差解释率 \( \text{VE} \)。因此，**模型无法恢复被投影丢弃的信号**，无论架构多么复杂。这一框架有助于厘清模型瓶颈究竟是来自“信息可用性”（即投影保留了多少任务相关方差）还是“信息利用效率”（模型从保留的信号中提取了多少）。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：投影基的选择决定了扰动预测的信息上限。对于任意正交基 \(\Phi \in \mathbb{R}^{G \times k}\) 和任意在 \(\Phi\) 值域中的预测器 \(\hat{\delta}\)，有 \( r^2 \le \text{VE}(\Phi) \)，其中 \(\text{VE} = \text{Var}(\Phi\Phi^\top \delta)/\text{Var}(\delta)\)。该上限将信息瓶颈分为“可用性”（VE）和“利用性”（\( r^2/\text{VE} \)）两部分。

- **关键技术细节**：
  - **Waddington Potential Network (WPN)**：将细胞表达映射到势能面，细胞速度由势能的负梯度给出（\( v = -\nabla U \)）。WPN 使用残差 MLP 学习势函数，通过自动微分计算梯度。该模型是研究基效应的理想载体，因为其梯度约束限制了模型只能学习保守（无旋）速度场，且投影基是唯一的输入表示。
  - **投影基的构建**：包括 PCA、基因关联网络（GRN）拉普拉斯特征基、图小波基（带通、谱图小波、扩散小波）、混合基、随机正交基、扰动加权基等。
  - **数据与网络**：使用 sciPlex3 化学扰动数据集（3 个细胞系，188 种药物 × 4 剂量）和 LINCS L1000 数据验证化学扰动；使用 Norman 2019 CRISPRa 遗传扰动数据集验证遗传扰动。构建了包含 534,670 条边的基因-基因关联网络（来自 STRING、OmniPath、Reactome、KEGG、GO 等）。

### 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- **数据集**：
  - **sciPlex3**：三个细胞系（K562、A549、MCF7），188 种药物 × 4 剂量，8,288 基因，共 2,202 条件（过滤后）。使用每细胞系独立对照（校正了池化对照伪影）。
  - **LINCS L1000**：基于磁珠的 978 标志基因平台；MCF7: 6,282 条件，A549: 4,524 条件；基因集与网络交集 596 基因。
  - **Norman 2019 CRISPRa**：K562 中 236 个单基因 CRISPRa 激活，91,168 个细胞，与网络词汇交集 2,257 基因，189 训练/47 验证。
- **Benchmark 及对比方法**：
  - 基线：**零参数均值预测器**、**Ridge 回归**（PCA-256 空间，以剂量为特征）。
  - 模型：**WPN**（19.6M 参数）、3 层残差 **MLP**（79K–525K 参数）、**scGen 风格 VAE**。
  - 投影基对比：PCA、GRN 特征基（低通）、随机正交基、扰动加权基（α=0.5/0.8）、混合基（GRN+PCA 正交化）、图小波基（带通、谱图、扩散）、细胞类型特异网络等。
  - 评估指标：方向准确率（dir acc）、前 200 DEG 的 Pearson 相关系数、MSE 20、求解器一致性。

### 4. 资源与算力

论文中未明确说明使用的 GPU 型号、数量及具体训练时长。仅提到训练了 WPN（19.6M 参数）等模型，使用 AdamW 优化器，学习率 3e-4，余弦退火 40 个 epoch，batch size 32。由于作者来自 Altos Labs，且为单作者论文，未提供算力细节。但实验规模（数据维度 ~8k 基因，种子 3 次重复，多基、多架构、多细胞系）表明需要适量的 GPU 资源。

### 5. 实验数量与充分性

实验设计较为充分：
- **主实验**：三个细胞系 ×（PCA vs GRN）在 sciPlex3 上重复 3 个随机种子；LINCS L1000 上验证两个细胞系。
- **架构无关性**：WPN（19.6M）、MLP（525K）、scGen VAE 均重现相同模式。
- **维度扫描**：PCA-k 从 10 到 512。
- **图小波实验**：三种小波基在三个细胞系上验证。
- **遗传扰动**：Norman 2019 上 k 从 25 到 189 的维度扫描，WPN 和 MLP 均验证了排名反转。
- **消融控制**：
  - 度保持置换检验（10 次置换）。
  - 合成 ground truth 网络（100 基因，30 扰动）。
  - 对照 PCA（仅用未处理细胞拟合）。
  - 跨细胞系 PCA 转移。
  - 细胞类型特异性网络、网络稀疏度、扰动加权等。
  - CRISPRi vs CRISPRa 分离测试（Replogle 2022）。
  - 有向调控网络（CollecTRI, DoRothEA）对比。
- **评估指标**：除主指标外，还检查了全基因指标、PerturBench 风格指标、求解器一致性、Hessian 条件数等。
总体而言，实验覆盖了化学和遗传两大类扰动、多种基、多种架构、多个控制条件，客观且公平地支持了结论。

### 6. 论文的主要结论与发现

1. **信息天花板存在并绑定于基的方差解释率**：所有测试的模型均满足 \( r^2 \le \text{VE} \)，且绝大部分模型远低于该上限（\( r^2/\text{VE} < 15\% \)），表明当前瓶颈是信息利用而非可用性。
2. **化学扰动下 PCA 主导，网络特征基失败**：GRN 低通特征基仅解释 ~12% 药物响应方差，PCA 解释 90-99%。药物响应在关联网络上频谱扩散（谱熵 ~0.935），信号主要在高频波段。
3. **图小波可恢复丢失信号**：在相同拓扑上使用带通/扩散小波可捕获约 88-90% 方差，性能接近 PCA。
4. **遗传扰动下排名反转**：CRISPRa 激活时，GRN 基 WPN/MLP 优于 PCA 基（方向准确率 0.723 vs 0.587），因为 CRISPRa 沿调控级联传播，与低频网络模式对齐。
5. **基效应的结构性质**：通过置换检验、合成网络、对照 PCA 等排除网络校准、维数伪影、数据循环等混淆因素。
6. **实用性指导**：基准应报告内部表示的 VE；生物启发基应与度保持置换零网络比较；图小波等全谱基优于截断低通基。

### 7. 优点

- **理论清晰**：提出简洁的投影界 \( r^2 \le \text{VE} \)，将矛盾归因于基础性问题而非模型能力。
- **设计精巧**：使用 WPN 梯度约束隔离基效应；控制实验系统（置换检验、合成网络、对照 PCA）排除混淆。
- **跨模态验证**：化学和遗传扰动均测试，且预测并验证了排名反转，增强了框架的普适性。
- **实践启示**：明确指出基准应报告 VE，提供具体的设计准则（如使用全谱图小波）。
- **代码与数据公开**：所有代码作为附件提供，数据来自公开来源。

### 8. 不足与局限

- **线性瓶颈限制**：论文的定界仅针对固定线性投影的模型（如 scGen、CPA），不直接适用于全基因方法（如 GEARS、PRiMeFlow），但指出后者在现有基准上并未超越 PCA 基线。
- **条件复用问题**：sciPlex3 的共享对照设计导致条件不变预测器（均值预测器）成为最优，限制了模型利用复杂结构的能力。论文指出在剂量响应、组合扰动等更丰富结构的数据集上，模型可能展现优势。
- **单作者 & 缺少算力细节**：未提供 GPU 型号、数量、训练时间，复现成本不确定。
- **遗传扰动验证集大小**：Norman 2019 仅有 236 个扰动，训练集 189 个，尽管维度扫描缓解了过拟合担忧，但更大规模的遗传数据集（如 Tahoe-100M）未测试。
- **跨模态推广未验证**：论文预测该框架适用于图像扰动读数、空间转录组学等，但未实验验证。
- **可解释性不足**：虽然解释了频谱扩散，但未深入探讨为何某些高频模式携带药物信号（如是否与特定基因功能模块相关）。
- **图小波计算开销**：论文未讨论图小波基的计算成本（特征分解或矩阵指数运算），在大规模全基因组网络上可能昂贵。

（完）
