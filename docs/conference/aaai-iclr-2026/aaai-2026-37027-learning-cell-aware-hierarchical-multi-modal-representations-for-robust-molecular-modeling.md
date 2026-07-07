---
title: Learning Cell-Aware Hierarchical Multi-Modal Representations for Robust Molecular Modeling
title_zh: 学习细胞感知的分层多模态表示以实现鲁棒分子建模
authors: "Mengran Li, Zelin Zang, Wenbin Xing, Junzhou Chen, Ronghui Zhang, Jiebo Luo, Stan Z. Li"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37027/40989"
tags: ["query:virtual-cell"]
score: 7.0
evidence: 联合建模分子层次和细胞对化学扰动的响应
tldr: 针对现有分子建模仅关注化学结构而忽略细胞响应的问题，本文提出CHMR框架，联合建模分子、细胞和基因组水平上的局部-全局依赖关系，使用细胞感知的分层多模态表示。在多个分子性质预测任务上，CHMR利用细胞形态和基因表达数据显著提升了预测精度，表明考虑细胞扰动响应对于鲁棒分子建模的重要性，直接关联虚拟细胞中的扰动响应预测。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37027/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 887, \"height\": 759, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37027/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1836, \"height\": 885, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37027/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 835, \"height\": 773, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37027/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1823, \"height\": 483, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37027/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1843, \"height\": 950, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37027/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 891, \"height\": 996, \"label\": \"Table\"}]"
motivation: 现有方法常忽略细胞响应，且未充分建模跨层级依赖。
method: 提出CHMR，联合建模分子与细胞响应的分层多模态表示。
result: 在分子性质预测上优于忽略细胞响应的方法。
conclusion: 细胞感知的表示学习对鲁棒分子建模至关重要，支持虚拟细胞应用。
---

## Abstract
Understanding how chemical perturbations propagate through biological systems is essential for robust molecular property prediction. While most existing methods focus on chemical structures alone, recent advances highlight the crucial role of cellular responses such as morphology and gene expression in shaping drug effects. However, current cell-aware approaches face two key limitations: (1) modality incompleteness in external biological data, and (2) insufficient modeling of hierarchical dependencies across molecular, cellular, and genomic levels. We propose CHMR (Cell-aware Hierarchical Multi-Modal Representations), a robust framework that jointly models local-global dependencies between molecules and cellular responses and captures latent biological hierarchies via a novel tree-structured vector quantization module. Evaluated on public benchmarks spanning 696 tasks, CHMR outperforms state-of-the-art baselines, yielding average improvements of 3.6% on classification and 17.2% on regression tasks. These results demonstrate the advantage of hierarchy-aware, multi-modal learning for reliable and biologically grounded molecular representations, offering a generalizable framework for integrative biomedical modeling.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：现有分子性质预测方法多仅关注化学结构（如分子指纹、图结构、3D构象），忽略了分子诱导的**细胞响应**（如形态变化、基因表达）对药物效果的塑造作用。
- **两大关键局限**：
  - **生物模态不完整**：细胞表型或基因表达数据常因实验成本或条件限制缺失（不对称缺失），导致分布偏移和模态不平衡。
  - **跨层级层次依赖建模不足**：分子扰动引发从化学结构→细胞过程→基因表达的级联反应，但现有方法将模态扁平化处理，仅做实例级对齐，无法捕捉多跳语义关系和跨尺度生物学机制。
- **整体含义**：需要一种**细胞感知的、层次化的多模态表示学习框架**，以提升模型在真实场景中处理缺失模态和跨尺度生物机制的鲁棒性，从而更准确可靠地预测分子性质。

## 2. 方法论

### 核心思想
提出 **CHMR（Cell-aware Hierarchical Multi-Modal Representations）** 框架，联合建模分子结构、细胞表型和基因表达三种模态，通过结构感知传播、语义一致性对齐、树结构化向量量化和上下文传播重建四个模块，实现鲁棒的、层次化的多模态分子表示学习。

### 关键技术细节

1. **模态增强（Modality Augmentation）**  
   - 构建分子间结构相似度矩阵 **W**，对每个分子取 top-K 近邻。  
   - 对缺失的细胞模态，沿邻接图做迭代传播（基于Dirichlet能量最小化思想）：  
     \( x_{i}^{c,(T)} = \sum_{j \in N_K(v_i)} W_{ij} x_j^{c,(T-1)} \)（缺失时），观测模态保留原始值。

2. **语义一致性对齐（Semantic Consistency Alignment, SCA）**  
   - 将各模态特征投影到共享隐空间，得到 \( p_i^m, p_i^c, p_i^{c,aug} \)。  
   - **实例级对齐**：InfoNCE对比损失，将分子锚点向量 \( p_i^{anch} \) 与细胞投影 \( p_i^c \) 作为正对。  
   - **分布级对齐**：VICReg损失，约束原始与增强后的细胞特征在语义和统计上一致。  
   - 总损失 \( \mathcal{L}_{SCA} = \mathcal{L}_{IA} + \mathcal{L}_{DA} \)。

3. **树结构化向量量化（Tree-VQ）**  
   - 构建深度为 H 的二叉树 \( \mathcal{T} = \bigcup_{h=1}^H \{e_j^{(h)}\}_{j=1}^{2^h} \)，所有模态共享该树。  
   - 逐层计算余弦距离，并施加路径掩码（只允许从父节点到两个子节点之一）。  
   - 对称VQ损失：\( \mathcal{A}(p_\xi, q_{\xi,h}) = 1 - \cos(sg[q_{\xi,h}], p_\xi) + \eta(1 - \cos(q_{\xi,h}, sg[p_\xi])) \)，平均跨模态和层级得 \( \mathcal{L}_{TreeVQ} \)。

4. **上下文传播重建（Context-Propagation Reconstruction, CPR）**  
   - 构造上下文图 \( \mathcal{H} \)，包含分子和外部生物实体，边权重 \( \beta \) 来自生物先验。  
   - 对每个节点进行长度为 L 的随机游走，累积传播权重 \( \beta_{i,l} \)。  
   - 使用解码器重建分子锚点和细胞特征，损失 \( \mathcal{L}_{CPR} = -\frac{1}{|V|} \sum_i \sum_{l=0}^L \beta_{i,l} \mathcal{D}(\hat{x}_{u_{i_l}}, x_{u_{i_l}}) \)，对离散/连续特征分别使用BCE/MSE。

### 整体训练目标
\[
\mathcal{L}_{total} = \mathcal{L}_{CPR} + \lambda_1 \mathcal{L}_{SCA} + \lambda_2 \mathcal{L}_{TreeVQ}
\]
预训练后冻结主干，仅训练轻量预测头用于下游任务。

## 3. 实验设计

### 数据集与场景

| 数据源 | 用途 | 规模 |
|--------|------|------|
| DrugBank + Cell Painting + JUMP-CP + L1000 | 预训练 | 129,592 分子，含完整化学结构，超90%分子缺失部分细胞模态 |
| ChEMBL (41任务) | 多任务分类（药物活性） | 2,355 分子 |
| ToxCast (617任务) | 多任务分类（毒性） | 8,576 分子 |
| Broad (32任务) | 多任务分类（生物响应） | 6,567 分子 |
| Biogen (6任务) | 多任务回归（ADME性质） | 3,521 分子 |

共 **696 个预测任务**，涵盖分类和回归。

### Benchmark 与对比方法
- **单模态方法**：MLP、RF、GP、AttrMask、ContextPred、EdgePred、GraphCL、GROVER、JOAO、MGSSL、GraphLoG、GraphMAE、DSLA 等。
- **多模态方法**：RoBERTa-102M、GPT2-87M、MolT5、UniMol、CLOOME、InfoCORE（GE/CP）、InfoAlign（SOTA）。
- 对比场景：分类用 AUC，回归用 MAE。

### 训练/验证/测试划分
- ChEMBL/Broad/Biogen：0.6/0.25/0.15 随机划分。
- ToxCast：0.8/0.1/0.1 基于骨架（scaffold）划分（遵循OGB默认）。

## 4. 资源与算力
- 文中仅提及实验在 **NVIDIA RTX 3090 GPU** 上进行。
- **未明确说明训练时长、GPU数量、显存消耗、总计算量**等具体算力指标。

## 5. 实验数量与充分性

### 实验数量
- **主实验**：在4个数据集、696个任务上与20+基线比较，每个任务5次不同随机种子，报告均值和标准差。
- **消融实验**：对4大模块（MA、SCA、Tree-VQ、CPR）及子组件进行了 **16种变体** 对比，覆盖零填充、随机填充、邻域填充、去掉各子损失、扁平VQ、去除随机游走、不同模态组合等。
- **超参数敏感性**：共4组分析（λ1, λ2 网格9×9、η 6种、树深度 9种）。
- **可视化分析**：t-SNE 展示跨模态对齐和层次中心分布（4幅2 subplot 图）。

### 充分性与公平性
- **充分**：涵盖多任务、多指标、多基线、多消融、超参敏感性和可视化，实验设计系统。
- **公平**：与SOTA（InfoAlign）相同训练/测试划分，基线方法引用原始论文配置，报告均值和标准差。
- **潜在偏差**：未对比其他层次化VQ方法（如VQ-VAE-2）；仅在一个显卡平台上测试；实际应用时缺失模态模式可能更复杂。

## 6. 主要结论与发现

1. CHMR 在 **所有四个数据集上全面超越SOTA**，分类任务平均提升 2.0–4.4%，回归任务（Biogen）MAE降低 **17.2%**。
2. **每个模块均不可或缺**：缺失任意模块（SCA、Tree-VQ、CPR）或简化策略（零/随机/邻域填充、扁平VQ）均导致性能明显下降（相对变化 -2.0%～-5.3%）。
3. **多模态协同优于单模态**：仅用分子特征下降4.9%；加入任一细胞模态均有改善，多种模态联合最佳。
4. **层次建模优于扁平对齐**：Tree-VQ 相比 Flat VQ 提升约 2%。
5. 可视化表明 CHMR 能同时实现 **跨模态对齐** 和 **层次结构保持**，而单独使用 SCA 或 Tree-VQ 只能做到其中一项。

## 7. 优点

1. **统一解决两大关键挑战**：同时处理模态缺失和层次依赖，设计巧妙。
2. **新颖的技术贡献**：提出树结构向量量化（Tree-VQ），在所有模态上共享一个语义树，实现跨尺度层次量化，并设计对称VQ损失。
3. **结构感知的模态增强**：基于图传播的迭代填充优于简单填充，且能利用局部-全局分子上下文。
4. **模块组合合理**：SCA 保证语义一致性，CPR 提供跨模态监督，Tree-VQ 强化学层次结构，三者互补。
5. **实验充分且对比全面**：26个基线+16种消融+超参分析+可视化，验证了鲁棒性和可解释性。
6. **公开代码**：提供 GitHub 仓库，便于复现和扩展。

## 8. 不足与局限

1. **算力资源未透明报告**：缺少训练时间、GPU数量、显存占用等信息，影响可复现性和能耗评估。
2. **外部数据依赖**：预训练需要大规模配对分子-细胞/基因数据（如JUMP-CP、L1000），对于罕见疾病或未覆盖的细胞系可能失效。
3. **假设所有分子模态完整**：文中仅关注细胞模态缺失，实际中分子结构也可能缺失（如3D构象），未覆盖。
4. **层次树的深度固定（H=6）**：未探索自适应深度或动态树结构，可能对某些任务不是最优。
5. **未与其他层次VQ方法（如VQ-VAE-2、Residual VQ）对比**：消融中仅比较了Flat VQ，缺乏更多基线验证Tree-VQ的优越性。
6. **下游任务仅限性质预测**：未在分子生成、逆向设计等任务上验证可迁移性。
7. **生物先验（关系图权重β）需要人工定义或额外知识库**：可能引入人为偏差，且未讨论不同先验的影响。

（完）
