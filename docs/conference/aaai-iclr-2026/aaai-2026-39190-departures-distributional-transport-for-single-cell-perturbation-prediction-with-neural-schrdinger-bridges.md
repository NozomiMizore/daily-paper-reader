---
title: "Departures: Distributional Transport for Single-Cell Perturbation Prediction with Neural Schrödinger Bridges"
title_zh: "Departures: 基于神经薛定谔桥的分布传输用于单细胞扰动预测"
authors: "Changxi Chi, Yufei Huang, Jun Xia, Jiangbin Zheng, Yunfan Liu, Zelin Zang, Stan Z. Li"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39190/43151"
tags: ["query:virtual-cell"]
score: 9.5
evidence: 使用神经薛定谔桥进行单细胞扰动预测
tldr: 单细胞扰动预测面临数据未配对的瓶颈，本文提出基于神经薛定谔桥的分布传输方法，直接建模细胞状态的分布变化，无需成对数据。该方法能够准确预测扰动后的单细胞转录组分布，为基因功能分析和药物筛选提供有力工具。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39190/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 719, \"height\": 258, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39190/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1740, \"height\": 696, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39190/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 768, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39190/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 782, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39190/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 681, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39190/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 705, \"height\": 395, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39190/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1562, \"height\": 845, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39190/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 712, \"height\": 176, \"label\": \"Table\"}]"
motivation: 单细胞扰动数据因测序破坏性而无法配对，现有方法缺乏显式条件化或依赖间接对齐。
method: 提出Departures方法，近似求解薛定谔桥，实现未配对单细胞扰动数据的分布传输。
result: 在多个数据集上优于现有方法，准确预测扰动后细胞状态分布。
conclusion: 为单细胞扰动预测提供有效生成式框架，具有生物学发现和药物筛选潜力。
---

## Abstract
Predicting single-cell perturbation outcomes directly advances gene function analysis and facilitates drug candidate selection, making it a key driver of both basic and translational biomedical research. However, a major bottleneck in this task is the unpaired nature of single-cell data, as the same cell cannot be observed both before and after perturbation due to the destructive nature of sequencing. Although some neural generative transport models attempt to tackle unpaired single-cell perturbation data, they either lack explicit conditioning or depend on prior spaces for indirect distribution alignment, limiting precise perturbation modeling. In this work, we approximate Schrödinger Bridge (SB), which defines stochastic dynamic mappings recovering the entropy-regularized optimal transport (OT), to directly align the distributions of control and perturbed single-cell populations across different perturbation conditions. Unlike prior SB approximations that rely on bidirectional modeling to infer optimal source-target sample coupling, we leverage Minibatch-OT based pairing to avoid such bidirectional inference and the associated ill-posedness of defining the reverse process. This pairing directly guides bridge learning, yielding a scalable approximation to the SB. We approximate two SB models, one modeling discrete gene activation states and the other continuous expression distributions. Joint training enables accurate perturbation modeling and captures single-cell heterogeneity. Experiments on public genetic and drug perturbation datasets show that our model effectively captures heterogeneous single-cell responses and achieves state-of-the-art performance.

---

## 论文详细总结（自动生成）

### 论文中文详细总结

#### 1. 核心问题与整体含义
- **研究动机**：单细胞扰动预测（如基因敲除、药物处理）对于基因功能分析和药物筛选至关重要。但单细胞测序具有破坏性，无法在同一细胞上同时获得扰动前后的表达谱，导致数据天然**未配对**。
- **现有局限**：部分方法忽略未配对问题；另一些方法通过无条件模型或间接对齐（如共享先验空间）来应对，但未能直接建模分布间的能量最优传输路径，导致预测精度受限。
- **本文贡献**：提出 **Departures** 框架，利用**神经薛定谔桥（Schrödinger Bridge, SB）** 直接对齐控制组与扰动组的分布，以进行分布级预测，无需成对数据。

#### 2. 方法论：核心思想、关键技术细节
- **核心思想**：通过**近似熵正则化最优传输**（SB）来学习从控制分布到扰动分布的随机动态映射。不同于传统SB依赖双向迭代推断样本配对，本文利用**Minibatch-OT**（Sinkhorn算法）在每个批次内构建源-目标样本配对，规避了反向过程病态问题，并直接引导桥匹配训练。
- **关键技术细节**：
  - **连续表达桥**：定义布朗桥过程，通过Doob h-变换构造起点到终点的随机路径（式7-8）。训练时预测终点表达值，损失仅计算扰动后非零基因（式9），避免模式崩溃。
  - **离散激活桥**：将基因表达二值化为激活/未激活状态，使用连续时间马尔可夫链（CTMC）建模状态转移。中间状态按概率插值（式11），通过预测条件后验分布（式13）优化交叉熵损失（式14）。
  - **联合训练**：同时训练连续模型 \(x_\theta\) 和离散模型 \(d_\theta\)，总损失 \(L = L_{\text{cont}} + L_{\text{disc}}\)。
  - **生成过程**：从真实控制细胞出发，分别对连续和离散模型进行Euler–Maruyama迭代（式16）和CTMC采样（式17），最终将预测表达值和激活状态逐元素相乘得到结果（式18）。

#### 3. 实验设计
- **数据集**：
  - **Adamson**：CRISPR knockout数据集，87种单基因扰动，单细胞类型（K562），取前5,000个高变基因。
  - **sci-Plex3**：化学扰动数据集，187种化合物×4个剂量×3种细胞类型，取前2,000个高变基因。
- **数据划分**：Adamson将扰动基因按70%/30%分为训练/测试；sci-Plex3按30%概率将每个扰动条件整体划入测试集。
- **对比方法**：GRAPE、GEARS、GraphVCI、scGPT、chemCPA、CPA。对于回归方法（GEARS、GRAPE），通过向不同控制样本添加预测差值来生成多样性。
- **评估指标**：**能量距离（E-distance）** 和 **平方地球移动距离（EMD²）**，分别在全部基因、Top20差异表达基因、Top40差异表达基因上计算。

#### 4. 资源与算力
- **计算资源**：使用 **2块 Nvidia A100 GPU** 进行训练。
- **超参数**：优化器 AdamW，学习率 0.001，batch size 64，推理步数 50，噪声尺度 \(\sigma=0.2\)。
- **训练时长**：论文未明确说明具体训练时长。

#### 5. 实验数量与充分性
- **实验数量**：
  - 主实验在两个数据集（Adamson、sci-Plex3）上进行，对比了7种基线方法，每个指标报告均值和标准差。
  - 消融实验：去除离散模型（w/o Discrete）、去除Minibatch-OT配对（w/o OT）、使用余弦/欧氏距离作为OT代价。
  - 额外分析：离散激活预测的PCC（表2）、可视化（小提琴图、UMAP）。
- **充分性与公平性**：
  - 覆盖了遗传和化学两类扰动，指标分布级全面。
  - 基线方法使用相同基因集，回归方法通过加扰动控制样本来促进输出多样性，较为公平。
  - 消融实验验证了各模块贡献。整体实验设计充分、客观。

#### 6. 主要结论与发现
- Departures 在 **Adamson** 和 **sci-Plex3** 两个数据集的所有指标上均**显著超越现有方法**，尤其在高差异基因的EMD²上优势明显。
- **离散激活模型**能够准确预测基因表达状态（PCC > 0.94），联合离散/连续建模有效防止模式崩溃。
- 消融实验表明：**离散模型**和 **Minibatch-OT配对**都是性能提升的关键组件。
- 通过直接分布传输替代间接对齐，能够更真实地捕捉细胞异质性。

#### 7. 优点
1. **直接分布对齐**：无需显式细胞配对，避免了信息损失和噪声放大。
2. **规避反向过程病态**：利用Minibatch-OT构建配对，无需学习双向模型，大幅简化训练并提升可扩展性。
3. **离散+连续联合建模**：同时捕捉基因表达水平和激活状态，提高生物保真度。
4. **广泛适用**：同时支持遗传和化学扰动数据集，且代码开源。
5. **理论根基扎实**：基于薛定谔桥和最优传输，提供了清晰的物理/统计解释。

#### 8. 不足与局限
1. **实验覆盖范围有限**：仅验证了两个数据集，在更多扰动类型（如多基因组合、多剂量组合）上的泛化性未知。
2. **原始数据的维度压缩**：仅使用前N个高变基因（5,000或2,000），可能丢失全转录组信息。
3. **依赖基因调控网络（GRN）先验**：论文引用了外部方法（Chi et al. 2025a）来处理扰动条件，但未讨论GRN的质量对结果的影响。
4. **计算开销**：每epoch需重新计算Minibatch-OT配对，在大规模数据集上可能成为瓶颈。
5. **未探讨不确定性量化**：模型输出为生成的样本，缺乏对预测置信度的估计。
6. **对极端稀疏数据的敏感性**：掩码机制虽缓解了模式崩溃，但非常稀疏的数据下可能仍存在挑战。

（完）
