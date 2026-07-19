---
title: Learning the Cellular Dynamics as a Port-Hamiltonian System
title_zh: 将细胞动力学学习为端口-哈密顿系统
authors: "Sigdel, D., Panday, N."
date: 2026-07-13
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.11.737972v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 使用端口-哈密顿系统建模细胞动力学，通过图神经网络代理，直接构建虚拟细胞模型
tldr: 细胞动态建模需同时满足热力学一致性和多时钟调控，但现有方法未能兼顾。本文提出复合分区端口-哈密顿模型，将细胞分为五个功能分区，用图神经网络学习其动态，并内置两个机制不同的时钟通过零功率端口耦合。在老鼠肝脏三组学昼夜节律数据上，模型满足被动性、预测轨迹RMSE 0.324、召回调控边AUROC 0.94，且核心预测的跨组学相位滞后与独立测量一致。该框架为细胞动态提供了可证伪、热力学自洽的刻画，同时揭示了其假设的局限性。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737972-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1027, \"height\": 763, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737972-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1668, \"height\": 1066, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737972-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1666, \"height\": 860, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737972-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1636, \"height\": 734, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737972-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 919, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737972-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 457, \"height\": 478, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737972-v1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 626, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737972-v1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 930, \"height\": 418, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-11-737972-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1423, \"height\": 541, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-11-737972-v1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1553, \"height\": 1364, \"label\": \"Table\"}]"
motivation: 现有细胞动态模型缺乏热力学一致性和多时钟共同调控机制，导致预测不可靠。
method: 利用图神经网络学习复合分区端口-哈密顿系统，结构包含五个功能分区和两个时钟耦合。
result: 模型在昼夜节律数据上被动性零违规，预测RMSE 0.324，调控边AUROC 0.94，相位滞后预测与实验一致。
conclusion: 提出热力学基础的可证伪细胞动态框架，指明多时钟级联假设需更多数据验证。
---

## 摘要
我们提出了一个由图神经网络代理学习的复合、分区、多时钟端口-哈密顿细胞动力学模型。状态对丰度偏差qj（即组学检测所测量的量）与仅从通过节律门认证为周期性的池中导出的振荡向量相关联。存储函数分解为五个功能分区（核心时钟、氧化还原、能量、信号传导、生物合成），因此无源性逐个分区得到认证，模型通过一个零净功率信号端口耦合了两个机制上不同的时钟，其中中心法则被硬连接，保守部分作为精确不变量保留。我们在从公共存储库整理的真实小鼠肝脏三组学昼夜节律数据集上评估了该模型，并报告了一个有意混合的结果。训练后的模型是无源的（[公式]，三个种子无违规），预测保留的轨迹片段（RMSE 0.324 ± 0.0004），并在置换零假设之上恢复了被隐藏的调控边（AUROC 0.94 ± 0.01）。其核心预测——跨组学相位滞后遵循 Δφ = arctan(ω/kdeg)——与独立测量的总转录-蛋白质滞后（5.7 h vs 4.9 h）吻合，但未反映基因间变异，且内部双时钟级联在现有跨队列代谢组学数据上无法评分。因此，该框架提供了可证伪的、基于热力学的细胞动力学描述，并具有明确的局限性。

## Abstract
We present a composite, compartmental, multi-clock port-Hamiltonian model of cell dynamics learned by a graph-neural-network surrogate. The state pairs abundance deviation qj, the quantity omics assays measure, with oscillatory phasors derived only for pools a rhythmicity gate certifies as periodic. The storage function decomposes over five functional compartments (core clock, redox, energy, signalling, biosynthesis), so passivity is certified compartment by compartment, and the model carries two mechanistically distinct clocks coupled through a zero-net-power signalling port, with the central dogma hard-wired and conserved moieties held as exact invariants. We evaluate it on a real mouse-liver tri-omic circadian dataset assembled from public repositories and report a deliberately mixed verdict. The trained model is passive ([Formula], no violations over three seeds), forecasts held-out trajectory segments (RMSE 0.324 {+/-} 0.0004), and recovers withheld regulatory edges above a permuted null (AUROC 0.94 {+/-} 0.01). Its central prediction -- that cross-omic phase lags follow {Delta}{varphi} = arctan({omega}/kdeg) -- matches the aggregate transcript-to-protein lag measured independently (5.7 vs 4.9 h) but not the gene-to-gene variation, and the internal two-clock cascade is not scoreable on the available cross-cohort metabolome. The framework thus gives a falsifiable, thermodynamically-grounded account of cell dynamics with explicit limits.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

现代系统生物学面临根本性矛盾：多组学技术产生的是静态、高维的快照，而细胞是一个开放、热力学驱动的连续时间动态系统。现有方法未能同时满足三个关键要求：
- **数据驱动的可学习性**：如单细胞基础模型（scGPT、Geneformer）是静态和关联性的，缺乏时间轴和守恒律。
- **连续时间动态性**：基于物理信息的神经网络（PINNs）或结构保持架构（哈密顿/拉格朗日神经网络）虽能保持能量守恒，但缺乏对生物特异性组分（如多时钟、功能分区）的建模。
- **热力学一致性**：传统约束性方法（如通量平衡分析）仅在稳态下保证热力学可行，而实时动态中缺乏此类保证。

本文的目标是填补上述空白，提供一个同时满足“可学习、动态、热力学一致”的虚拟细胞模型，并通过真实小鼠肝脏三组学昼夜节律数据进行验证。

---

## 2. 方法论

### 核心思想
采用**端口-哈密顿（port-Hamiltonian, pH）系统**形式化细胞动力学，并通过**图神经网络（GNN）代理**学习该系统。核心创新包括：
- **双层状态**：原始状态为丰度偏差 qj（直接测量），仅对通过节律门认证的振荡性池推导相量 zj（复振幅+相位）。
- **复合分区哈密顿量**：存储函数 H = Σc Hc + Hint，分解为五个功能分区（核心时钟、氧化还原、能量、信号传导、生物合成），每个分区携带自己的时钟和内部能量。
- **双时钟库**：包含机制不同的昼夜节律时钟（TTFL，周期~24h）和氧化还原时钟（转录独立，周期~20h），通过零净功率的 NAD+/SIRT1 信号端口耦合。
- **结构保持连接与耗散**：互连矩阵 J 为块对角（分区内）+ 区间质量键和调制端口（反对称化确保零净功率）；耗散矩阵 R 为对角正定，初始化为测量到的降解速率。
- **硬编码约束**：中心法则（基因→蛋白质）作为近对角质量键；化学计量守恒（如腺苷酸池、NAD 池）作为精确不变量。

### 关键技术细节
- **节律门**：对每个池进行 Butterworth 带通滤波 + Lomb-Scargle 周期图，分配至对应时钟的频段（22-26.5h 昼夜，18-22h 氧化还原），并通过最小二乘拟合估计时间参考的峰值相位。
- **GNN 能量网络**：分层 GNN，输入包含丰度、化学势和（对振荡池）相量特征；分区内自注意力 + 跨组学注意力。输出哈密顿量及其各分区贡献。
- **复合物理损失**：L = λk Lk + λp Lp + λpc Lcomp_p + λeb Leb + λc Lc + λs Ls + λh Lh，包含运动学 MSE、全局/分区无源性惩罚、功率平衡、化学计量守恒、稳态固定、相位锁定值（PLV，弱先验权重 0.01）。
- **相位级联预测**：跨组学相位滞后由 ∆φ = arctan(ω/kdeg) 决定，其中 kdeg 为降解速率，ω 为时钟频率。这一预测无需拟合滞后数据，直接基于公开的降解半衰期计算。

---

## 3. 实验设计

### 数据集
- **转录组**：Zhang et al. 2014（GSE54650），小鼠肝脏，CT18-64，2h 分辨率，22105 基因。
- **蛋白质组**：Robles, Cox & Mann 2014（SILAC 小鼠肝脏），CT0-45，3h 分辨率，3072 蛋白质，并附有作者测量的 139 个转录-蛋白质相位滞后（Table S4）。
- **代谢组**：Meng et al.（Metabolomics Workbench ST002079），ZT0-20，4h 分辨率，3552 特征，但仅 6 个时间点（单周期）。

三者来自不同队列和平台，仅按昼夜节律相位对齐，非同一动物采样。最终构建 100 个分子池（40 基因组/转录组 + 35 蛋白质组 + 25 代谢组），分配至五个功能分区。

### 实验设置
- 时间跨度：T = 480 步（∆t = 0.1h，48h），80/20 时间分割（最后 20% 作为保留轨迹）。
- 隐藏维度 dh = 128，3 个随机种子各训练 300 轮。
- 优化器：Adam，余弦退火（初始学习率 5e-4，最小 1e-5），梯度裁剪（最大范数 2）。

### 基准与对比
- **无直接对比方法**：本文未与现有方法（如纯物理信息网络、静态单细胞模型）进行定量对比，而是强调自身框架的独特性（同时满足三个要求）。
- **消融实验**：通过控制 PLV 先验权重（λcoh = 0.01 弱先验）来检验边恢复是否来自动态拟合而非注入结构；通过测试模型独立预测（相位级联）来验证机制。

---

## 4. 资源与算力

论文未明确说明所使用的 GPU 型号、数量或训练时长。仅提及优化使用 Adam 配合余弦退火，每轮训练约 300 个 epoch，3 个随机种子。对于 100 个节点、128 隐藏维度的 GNN 代理，训练计算量应中等，但具体硬件信息缺失。

---

## 5. 实验数量与充分性

### 实验覆盖
- **训练收敛**：展示损失曲线（图 1），验证各项损失（尤其是无源性惩罚）持续为零。
- **时钟恢复**：应用节律门于真实数据，恢复昼夜节律基因（如 Arntl、Nr1d1），但氧化还原时钟分配受限于代谢组稀疏性（6 个时间点），为采样伪像。
- **相位级联预测**：
  - 模型独立预测（使用公开半衰期） vs. Robles 测量的 27 个配对转录-蛋白质滞后：总滞后均值匹配（5.7h vs 4.9h），但基因间相关性为噪声水平（r = -0.06）。
  - 内部双时钟级联（昼夜 G→P 和氧化还原 P→M）：因代谢组分辨率不足，无法评分。
- **无源性**：自由积分下 max_t dH/dt < 0，所有状态无违规（图 4a）。
- **边恢复**：AUROC = 0.941 ± 0.012，高于置换零假设（z=5.6），但仅测试了一组带标签的隐藏边（具体数量未给出）。
- **保留轨迹预测**：RMSE = 0.324 ± 0.0002，能量相关性 r=0.79±0.09。

### 充分性评估
- **优势**：覆盖了物理约束、预测能力、结构恢复等多种指标，且报告了三个种子的均值和标准差。
- **不足**：
  - 仅在一个数据集（小鼠肝脏昼夜节律）上验证，缺乏跨组织/物种的泛化。
  - 无对比实验（与基线方法如单纯 GNN、静态 Port-Hamiltonian 等）。
  - 消融实验仅限 PLV 权重，未系统探索其他损失项权重或分区结构的影响。
  - 内部双时钟级联未能测试，削弱了“双时钟耦合”核心声明的验证。
  - 代谢组数据稀疏性限制了结论的充分性。

---

## 6. 主要结论与发现

1. **无源性成立**：训练后的模型在自由积分中满足 dH/dt ≤ 0，零违规，且分区无源性也成立（图 4a）。
2. **预测能力**：保留轨迹 RMSE 0.324，能量相关性 0.79，边恢复 AUROC 0.94 高于零假设。
3. **相位级联的混合结果**：
   - 整体均值滞后（5.7h vs 4.9h）正确，证明“降解速率决定滞后”机制在群体水平有效。
   - 基因间变异无法捕捉，因使用层水平半衰期先验而非基因特异性测量。
4. **双时钟级联未证实**：由于代谢组数据问题，氧化还原时钟对代谢物滞后的预测不可评分。
5. **模型局限性明确**：数据跨队列、降解速率先验粗糙、代谢组时间点稀疏，限制了部分声明的验证。

---

## 7. 优点

1. **理论严谨性**：将端口-哈密顿系统引入细胞建模，同时满足热力学守恒（无源性、质量守恒、反对称耦合）和数据驱动学习。
2. **生物解释性**：复合哈密顿量对应功能分区，提供能量分解诊断；相位级联预测具有可证伪性。
3. **结构保持**：J 的反对称性、R 的正定性硬编码，无需训练后校验；中央法则和质量键预先嵌入。
4. **诚实报告**：明确区分成功和失败的结果（如相位级联的聚合匹配 vs 基因间无技能），并解释原因，增加了可信度。
5. **扩展性**：端口-哈密顿框架允许模块化组合（如细胞间通过代谢端口互联），便于未来药物筛选。

---

## 8. 不足与局限

1. **数据局限**：
   - 三组学来自不同队列，仅相位对齐非同一动物，限制同一细胞动态的声索。
   - 代谢组（6 时间点）过于稀疏，无法区分 24h 与 20h 周期，导致氧化还原时钟分配为伪像。
   - 降解速率仅为层水平先验（mRNA t1/2 ≈ 7h，蛋白质 ≈ 46h），无法预测基因特异性滞后。
2. **验证不足**：
   - 缺乏基线方法对比（如普通 GNN、无物理约束的时序模型、静态 pH 模型）。
   - 双时钟耦合核心假设仅通过模拟端口（零净功率）实现，实验上未验证。
   - 内部级联无法评分，削弱了框架的完整验证链。
3. **方法局限**：
   - 存储函数 H 为 Lyapunov 函数而非可测量能量，其绝对值无物理单位。
   - 节律门基于固定频带划分（22-26.5h / 18-22h），可能将非时钟池误分（如代谢组案例）。
   - 模型规模较小（100 节点，128 隐藏维），真实细胞规模（数千基因）的扩展性未测试。
4. **可重复性**：代码、数据集处理流程未明确公开，仅提及数据来源和组装说明，可能影响他人复现。
5. **能耗与数据要求**：未讨论模型训练所需数据和计算成本，也未比较与纯数据驱动方法的效率。

（完）
