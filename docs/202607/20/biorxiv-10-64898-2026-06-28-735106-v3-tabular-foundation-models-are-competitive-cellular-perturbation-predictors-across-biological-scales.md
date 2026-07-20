---
title: Tabular Foundation Models Are Competitive Cellular Perturbation Predictors Across Biological Scales
title_zh: 表格基础模型在跨生物尺度的细胞扰动预测中具有竞争力
authors: "Palla, G., Hillsley, A., Kim, Y.-J., Royer, L. A."
date: 2026-07-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.28.735106v3.full.pdf"
tags: ["query:virtual-cell"]
score: 10.0
evidence: 直接比较表格基础模型与专用单细胞模型在细胞扰动预测上的表现
tldr: 预测细胞对遗传和化学扰动的响应是药物发现和功能基因组学的核心挑战。本文系统比较了通用表格基础模型（TabICL、TabPFN）与多个领域特定模型（scGPT、PRESAGE等）在细胞级跨细胞类型、伪bulk、全基因组CRISPR筛选及胚胎发育四种场景下的性能。结果表明，通用表格模型在多数任务中表现相当或优于专门模型，尤其在伪bulk预测中一致领先。这证明了无需领域定制的通用表格上下文学习可作为扰动响应建模的强大可扩展替代方案。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1451, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1442, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 783, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 871, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1438, \"height\": 671, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1447, \"height\": 889, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1446, \"height\": 888, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1439, \"height\": 985, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1434, \"height\": 494, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1430, \"height\": 987, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1433, \"height\": 951, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1437, \"height\": 780, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1515, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 971, \"height\": 355, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1105, \"height\": 439, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1314, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 596, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 774, \"height\": 268, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 889, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1632, \"height\": 972, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1315, \"height\": 972, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1504, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v3/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 867, \"height\": 835, \"label\": \"Table\"}]"
motivation: 评估通用表格基础模型相比领域特定模型在细胞扰动预测中的实际优势。
method: 在四种互补评估设置中对比TabICL、TabPFN与PRESAGE、scGPT等模型。
result: 通用表格模型在细胞级跨细胞类型和伪bulk预测中优于专门模型，在全胚胎预测中有竞争力。
conclusion: 通用表格上下文学习为扰动响应建模提供了强有力且可扩展的替代方案。
---

## 摘要
预测细胞如何响应遗传和化学扰动是药物发现和功能基因组学中的一个核心挑战。为此，已经发展出一个日益壮大的专用单细胞基础模型生态系统，但这些模型相对于领域无关方法的实际优势仍不明确。在这里，我们评估了表格基础模型（如TabICL和TabPFN，即通用预训练回归模型）与领域特定架构（包括PRESAGE、scGPT、scLAMBDA、STACK和Prophet）在四个互补评估场景中的性能：细胞层面的上下文内跨细胞类型预测、基于五个细胞系Perturb-seq数据集的伪批量扰动预测、原代人CD4+ T细胞的全基因组CRISPR筛选，以及斑马鱼发育扰动图谱中的胚胎水平细胞类型组成预测。在细胞层面的跨细胞类型扰动预测中，表格基础模型的表现与专用模型相当或更优。在伪批量扰动预测中，表格基础模型在多个评估指标和数据集上持续优于专用基线模型。在胚胎整体细胞类型组成预测中，表格基础模型与专用基线模型具有竞争力。这些结果表明，通用表格上下文学习为跨细胞系统和尺度的扰动响应建模提供了一种强大且可扩展的替代方案，超越了定制的生物架构。

## Abstract
Predicting how cells respond to genetic and chemical perturbations is a central challenge in drug discovery and functional genomics. A growing ecosystem of specialized single-cell foundation models has been developed to address this problem, yet their practical advantage over domain-agnostic approaches remains unclear. Here we evaluate the power of Tabular Foundation Models such as TabICL and TabPFN, general-purpose pre-trained regression models, against domain-specific architectures including PRESAGE, scGPT, scLAMBDA, STACK and Prophet across four complementary evaluation settings: cell-level in-context cross-cell-type prediction, pseudobulk perturbation prediction on five Perturb-seq datasets of cell-lines, a genome-wide CRISPR screen in primary human CD4+ T cells, and embryo-level cell-type composition prediction in a zebrafish developmental perturbation atlas. In the cell-level cross-cell type perturbation prediction, Tabular Foundation Models perform on par or better than specialized models. On pseudobulk perturbation prediction, Tabular Foundation Models consistently outperform specialized baselines across multiple evaluation metrics and datasets. On whole-emrbryo cell-type composition prediction, Tabular Foundation Models are competitive with specialized baselines. These results demonstrate that general-purpose tabular in-context learning provides a strong and scalable alternative to bespoke biological architectures for perturbation response modeling across cell systems and scales.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：预测细胞对遗传和化学扰动的响应是药物发现和功能基因组学的核心挑战。领域内已出现大量专用单细胞基础模型（如 scGPT、PRESAGE、STACK 等），但它们是否比领域无关的通用模型更具优势仍不明确。
- **整体含义**：本文系统比较了通用表格基础模型（TabICL、TabPFN）与多个专用架构在四种细胞扰动预测场景中的性能，揭示了通用表格上下文学习可作为跨系统、跨尺度的强大替代方案，挑战了“需要生物学专门归纳偏置”的普遍假设。

### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：将细胞扰动预测统一视为回归问题，利用 Prior-Fitted Networks (PFNs) 在零样本下进行近似贝叶斯后验预测。PFNs 在合成数据上预训练，无需对目标任务进行梯度适应即可执行上下文学习。
- **关键技术细节**：
  - **伪批量预测**：将每个扰动的基因表达响应通过 PCA 分解为多个标量成分，独立训练回归器。输入特征由多模态嵌入（基因共表达、蛋白质互作网络、文献嵌入等）构建。
  - **细胞级预测**：通过最优传输（OT）匹配源控制细胞与目标控制细胞，学习跨细胞类型的映射；然后将该映射应用于药物处理后的源细胞，得到目标细胞的单细胞表达预测。
  - **斑马鱼胚胎预测**：预测每个（扰动×时间点）条件下的细胞类型比例向量，同样使用 PCA 分解输出空间。
  - **零样本推断**：TabICL 和 TabPFN 在测试时只进行一次前向传播，无需微调，计算效率极高。

### 3. 实验设计：数据集 / 场景、基准、对比方法
- **场景与数据集**：
  - **细胞级跨细胞类型预测**：OpenProblems 基准（298K 细胞，144 种化学扰动，4 种细胞类型）；T 细胞训练，预测 NK、B、Myeloid 细胞。
  - **伪批量扰动预测**：5 个 Perturb-seq 数据集（Nadig HepG2/Jurkat、Replogle K562 Essential/GW、RPE1 Essential），5 折扰动留出交叉验证。
  - **全基因组 CRISPR 筛选**：原代 CD4+ T 细胞（Zhu et al., 2025），两个供体，约 7k 有意义扰动；5 折交叉验证。
  - **斑马鱼发育扰动**：zscape 图谱（2.7M 细胞，28 个遗传扰动，5 个时间点，98 种细胞类型）；5 折严格时间点留出交叉验证。
- **对比方法**：TabICL、TabPFN、CatBoost（强基线） vs 专用模型 STACK、PRESAGE、scGPT、scLAMBDA、Prophet；还包括 Mean 基线和 Bootstrap 噪声上限。
- **评估指标**：相对 MSE、余弦相似性、Phenocopy AUROC、Recall@10（伪批量）；Pearson Δ、DE Spearman、方向匹配、DE Recall、判别分数、E-距离（细胞级）；Spearman 相关系数、R²（斑马鱼）。

### 4. 资源与算力
- **硬件**：所有实验在单张 NVIDIA L40 或 A40 GPU 上运行。STACK 推理需要 128GB RAM、8 CPUs，最多 6 小时/供体。
- **每折耗时（中位数）**：TabICL / TabPFN（零样本） 约 3 秒；CatBoost 4-7 秒；PRESAGE（从头训练）约 253 秒。
- **未明确**：总 GPU 小时数、具体 CPU/内存等细节。但总体计算成本适中，且 TFMs 因零样本而极为高效。

### 5. 实验数量与充分性
- **实验数量**：涵盖 4 个主要场景，每个场景包含多个数据集（共 8+ 个自有数据集）、多种对比方法（6-7 种），并进行了大量消融实验：
  - 输出空间几何消融（PCA tail、随机旋转、ICA、NMF 等）。
  - 支持集选择（最远点采样 vs 随机）。
  - 数据效率扫描（25%–100% 训练数据）。
  - 概念细胞扫描（10%–100% 上下文细胞）。
  - 模态留一消融（6 个嵌入模态）。
- **充分性与公平性**：
  - 所有方法使用相同的特征输入和交叉验证协议（扰动留出、时间点留出）。
  - Bootstrap 基线提供 Oracle 上限，Mean 基线提供负控制。
  - 重复数：伪批量 5-fold × 5 数据集，细胞级 3 供体 × 3 目标类型，CD4 2 供体 × 5 fold。消融实验均跨多折。
  - 结论稳健，但消融实验显示 NMF 有时优于 PCA，提示 PCA 并非唯一最优分解。

### 6. 论文的主要结论与发现
- 通用表格基础模型（TabICL、TabPFN）在 **大多数任务** 匹配或超越所有测试的专用模型。
- 在 **伪批量预测** 中一致领先；在 **细胞级跨细胞类型** 上占优；在 **斑马鱼** 上 TabPFN 最优，Prophet 次之。
- 优点来源于：强后验回归能力、PCA 分解使每分量回归条件良好、零样本推断高效。
- 专用生物学偏置并非必需，通用上下文学习可提供强大且可扩展的替代方案。

### 7. 优点
- **方法简洁统一**：仅需 PCA 分解 + 零样本表格回归，即可跨生物尺度有效，无需领域定制。
- **计算高效**：TFMs 推理所需 GPU 时间远少于从头训练专用模型（秒级 vs 分钟级）。
- **实验设计全面**：覆盖细胞、伪批量、全基因组和发育四个层级，包含多种消融和基线。
- **严谨消融**：隔离输出空间几何、支持集多样性、模态贡献等关键因素，揭示性能来源。
- **最优传输匹配**：可泛化至单细胞预测，且优于近邻匹配。

### 8. 不足与局限
- **未覆盖所有场景**：仅测试了 4 种场景，可能遗漏其他扰动类型（如化学扰动、多模态数据）或大规模预训练优势场景。
- **CD4 全基因组信号弱**：所有模型表现均接近 Mean 基线，说明任务信噪比极低，结论在该场景的推广有限。
- **PCA 分解的非唯一性**：消融显示 NMF 有时优于 PCA，暗示目前流程并非最优；需进一步研究如何选择输出空间分解。
- **不确定性未利用**：PFNs 可输出完整后验分布，但本文仅用点估计，未评估不确定性量化。
- **可解释性与因果发现**：文中提及但未实际探索，论文仅专注于预测性能比较。
- **预印本状态**：未经同行评审，部分细节（如 CD4 数据预处理）需进一步验证。

（完）
