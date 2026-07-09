---
title: Biologically informed neural network models are robust to spurious interactions via self-pruning
title_zh: 生物学启发的神经网络模型通过自剪枝对虚假相互作用具有鲁棒性
authors: "Nordenstorm, O., Baghdassarian, H., Xu, X., Lauffenburger, D. A., Nilsson, A."
date: 2026-07-09
pdf: "https://www.biorxiv.org/content/10.1101/2025.10.24.684155v3.full.pdf"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 生物信息神经网络建模细胞网络
tldr: 生物信息神经网络（BINNs）通过结合深度学习与先验知识建模细胞网络，但评估其对未知相互作用的鲁棒性是个挑战。本研究提出通过测量模型在训练中对故意引入的虚假相互作用的自剪枝能力来评估鲁棒性，并开发了新的指标RRA和GPU加速的LEMBAS框架。在三个数据集上，随机虚假相互作用被剪枝的程度大于先验知识网络的真实相互作用，前提是L2正则化足够大。该工作表明BINNs对先验知识的不确定性具有鲁棒性，为模型可靠性评估提供了新方法。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-24-684155-v3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1704, \"height\": 829, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-24-684155-v3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1631, \"height\": 1412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-24-684155-v3/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1677, \"height\": 727, \"label\": \"Figure\"}]"
motivation: 评估生物信息神经网络（BINNs）对先验知识中不确定相互作用的鲁棒性，以信任其推断的机制。
method: 提出自剪枝指标RRA，通过GPU加速的LEMBAS框架测量模型对故意引入的虚假相互作用的下加权程度。
result: 在三个数据集上，随机虚假相互作用被有效剪枝（RRA接近零），只要L2正则化足够大，剪枝程度高于真实相互作用。
conclusion: BINNs通过自剪枝对先验知识中的虚假相互作用具有鲁棒性，提高了模型在复杂生物网络中的可靠性。
---

## 摘要
细胞网络的计算模型有望揭示疾病机制并指导治疗策略。生物学启发的神经网络（BINNs）是一种新兴方法，通过结合深度学习的预测能力与先验知识（生物学研究的关键方面）来创建此类模型。BINNs的架构强制了一种网络结构，理想情况下可从中推断机制。然而，关键挑战在于评估这些模型的可靠性，因为细胞本质上是复杂的，涉及错综复杂且有时未知的相互作用。目前，分析主要集中于选定的通路，而非更全面的视角。在本工作中，我们展示了一种替代性的整体方法：我们衡量BINN在训练过程中有意引入的虚假相互作用被降低权重的程度（自剪枝）。所提出的指标RRA（相对残差面积）允许直接分布比较，其中零表示完美的自剪枝，大于一则表示自剪枝失败。为了实现快速测试，我们更新了LEMBAS（大规模知识嵌入的人工信号网络）——我们的细胞内信号动力学循环神经网络框架，并实现了完全的GPU加速。与原始版本相比，我们的实现实现了>7倍的加速，同时保持了预测准确性。我们在3个不同数据集上评估了自剪枝，发现当随机引入虚假相互作用时，只要模型通过足够大的L2范数进行正则化，模型对这些相互作用的剪枝程度大于对先验知识网络（PKN）的剪枝。这表明BINNs可以对PKN中的不确定性具有鲁棒性。

实现与应用
我们的LEMBAS实现根据MIT许可证在https://github.com/AvlantNilssonLab/LEMBAS_GPU上免费提供。用于生成图表的模型和结果可通过https://zenodo.org/records/17425598下载。

## Abstract
Computational models of cellular networks hold promise to uncover disease mechanisms and guide therapeutic strategies. Biology-informed neural networks (BINNs) is an emerging approach to create such models by combining the predictive power of deep learning with prior knowledge, a vital aspect of biological research. The architectures of BINNs enforces a network structure from which mechanism can ideally be inferred. However, a key challenge is to evaluate the reliability of these models, as cells are inherently complex, involving intricate and sometimes unknown interactions. Currently, analysis mainly focuses on selected pathways rather than a more comprehensive perspective. In this work we demonstrate an alternative holistic approach: we measure to which extent purposefully introduced spurious interactions are down-weighted by a BINN during training (self-pruning). The metric suggested RRA (Relative Residual Area) allows for direct distribution comparison with perfect self-pruning achieved at zero and a failure to self-prune if above one. To enable rapid testing, we updated LEMBAS (Large-scale knowledge-EMBedded Artificial Signaling-networks), our recurrent neural network framework for intracellular signaling dynamics, with full GPU acceleration. Our implementation achieves a >7-fold speedup compared to the original while preserving predictive accuracy. We evaluated self-pruning in 3 different datasets and found that when spurious interactions are introduced at random, the model prunes these to a larger extent than those from the prior knowledge network (PKN), provided the model is regularized with a sufficiently large L2 norm. This suggests that BINNs can be robust to uncertainty in the PKN.

Implementation and applicationOur implementation of LEMBAS is freely available under a MIT license at https://github.com/AvlantNilssonLab/LEMBAS_GPU. The models and results to generate the figures can be downloaded through https://zenodo.org/records/17425598.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：生物学启发的神经网络（BINNs）通过将先验知识网络（PKN）嵌入模型架构，试图在保持预测能力的同时提供机制可解释性。然而，先验知识本身存在不确定性（虚假相互作用、缺失边、细胞类型特异性差异），如何评估模型对这些不确定性的鲁棒性成为关键挑战。现有评价多集中在特定通路分析，缺乏系统级、全面的可靠性度量。
- **整体含义**：作者提出通过“自剪枝”（self-pruning）能力——即模型在训练过程中主动抑制虚假相互作用的能力——作为衡量BINNs可靠性的新范式。如果模型能够自发地将错误先验知识降低权重，则表明其对先验知识的不确定性具有鲁棒性，从而增强对模型推断机制的信任。该工作为BINNs的评估提供了一种无需手动通路标注的自动化、系统性指标。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

### 核心思想
- 在BINN的PKN中**随机添加一定数量的虚假边**（确保与真实边具有相同的连接度分布），然后训练模型。通过比较训练后虚假边与真实边的权重分布，判断模型是否将虚假边权重降低（剪枝）。
- 定义指标 **RRA (Relative Residual Area)**：  
  \( \text{RRA} = \frac{\text{虚假边的残差面积}}{\text{真实边的残差面积}} \)  
  - 残差面积：权重累积分布函数（CDF）与点(0,1)之间左上角的面积。权重越趋向于大值，残差面积越大。
  - RRA = 0 表示完美自剪枝（虚假边权重无限接近0）；RRA = 1 表示无自剪枝；RRA > 1 表示模型偏好虚假边。

### 关键技术细节
- **框架升级**：重新实现了BINN框架**LEMBAS**（循环神经网络架构，模拟信号传导）的GPU版本：
  - 使用PyTorch的密集矩阵乘法替代原始CPU稀疏乘法（因网络密度>99%，GPU上密集乘法更快）。
  - 用**幂迭代法**（5次迭代）替代CPU上的ARPACK特征值求解器，用于谱半径正则化。
  - 引入**梯度噪声注入**代替原有的防止神经元死亡的权重惩罚。
  - 改进**状态正则化**：用linspace值近似均匀分布，替换原基于均值和方差的惩罚。
  - 提供可选输出偏置项，允许负输出（不再强制Sigmoid变换）。
- **正则化**：标准L2权重正则化（惩罚权重大小），在实验中测试三种强度（1e-6, 1e-5, 1e-4）。
- **训练算法**：采用与原始CPU版本相同的交叉验证流程（留一法），但批大小和梯度噪声调度针对GPU优化。

### 算法流程（文字说明）
1. 初始化：基于PKN构建网络拓扑，所有边权重可学习，非PKN边固定为0。
2. 在每个训练迭代中：
   - 使用循环神经网络（RNN）对给定输入（如配体刺激）传播信号，计算稳态隐藏状态。
   - 从隐藏状态提取输出（转录因子活性）。
   - 计算损失：均方误差（MSE） + L2权重正则化 + 可选项（谱半径正则化、状态正则化、梯度噪声）。
   - 反向传播更新权重；训练结束后，强制非PKN边权重归零（稀疏掩码）。
3. 自剪枝评估：训练收敛后，计算虚假边与真实边的权重CDF，得出各自残差面积，再计算RRA。

## 3. 实验设计：使用的数据集、基准测试、对比方法

### 数据集
| 数据集 | 描述 | 规模 | 备注 |
|--------|------|------|------|
| 低覆盖巨噬细胞数据集 | 23种不同配体刺激下的转录应答 | 23个条件 | 来源于Xue等(2014) |
| 高覆盖巨噬细胞数据集 | 59种配体，±LPS共刺激 | 59 + 59(共刺激) | 来源于Nilsson等(2022) |
| 合成数据集 | 由LEMBAS自身生成，使用KEGG通路网络，目标最大化信号多样性 | 与低覆盖相同结构 | 已知真实参数（ground truth） |

### 基准与对比
- **GPU vs CPU版本对比**：比较两者在相同fold上的预测性能（Pearson相关系数）和运行时间。
- **自剪枝实验**：每个数据集上，每个L2水平训练50个独立模型（ensemble），每个模型添加100个随机虚假边。
- **消融实验**：测试是否去除状态正则化、权重正则化（L2）、输出偏置等对性能和权重分布的影响。
- **统计检验**：使用Wilcoxon test、Mann-Whitney U-test、GAMM（广义可加混合模型）控制拓扑结构，验证权重大小与预测敏感性的关系。

### 对比方法
未与其他BINN框架（如P-NET等）进行直接横向对比，仅与原始CPU版LEMBAS对比。主要聚焦于LEMBAS自身行为。

## 4. 资源与算力

- **硬件**：
  - 低覆盖和高覆盖数据集性能对比：Dell Precision 3680 (Intel i7-14700, NVIDIA RTX 4000 Ada Generation, 32GB显存)。
  - 自剪枝实验及高覆盖数据集交叉验证：Berzelius集群（多节点，含不同GPU，如NVIDIA V100）。
  - 部分计算使用MIT Satori集群（64个Power9节点，每个节点4张NVIDIA V100 32GB GPU，NVLink2连接）。
- **训练时长**：
  - 低覆盖数据集：GPU平均9分钟 vs CPU平均23分钟（加速~2.4倍）。
  - 高覆盖数据集（超参数优化后）：GPU约20分钟 vs CPU约3小时（加速7.1倍）。
- **总实验量**：450+个模型训练（3数据集×3L2×50模型），加上GPU/CPU对比、消融实验、GAMM分析等，算力消耗较大。

## 5. 实验数量与充分性

- **数量充分**：在三个完全不同的数据集（合成/真实低覆盖/真实高覆盖）上重复验证，每个条件50个随机初始化模型，共约450个独立训练，具有很强的统计功效。
- **消融实验**：系统地测试了状态正则化、权重正则化、输出偏置、谱半径计算方式的影响，并比较了梯度噪声与原有神经元死亡预防方案。
- **分析深度**：不仅比较RRA，还通过零化权重法、GAMM回归、与文献支持数关联等，验证了权重大小与机制相关性的联系。
- **客观性**：使用了原始论文中相同的交叉验证fold，并进行了统计显著性检验（Wilcoxon、Mann-Whitney U-test）、效应量（Cohen's d）以及置换检验。未发现选择性报道偏差。
- **局限性**：所有实验仅针对LEMBAS这一种BINN架构，未与其他BINNs（如P-NET、Pathformer等）对比，通用性待验证。此外，虚假边生成方式单一（随机添加，保持度分布），未测试其他噪声类型（如错误符号、缺失边）。

## 6. 论文的主要结论与发现

1. **GPU加速版LEMBAS有效且高效**：在保持预测精度（Pearson r 低覆盖0.69 vs 0.68；高覆盖0.83 vs 0.85）的前提下，训练速度提升2.4~7.1倍，且平均性能略有提高。
2. **BINNs表现出自剪枝能力**：在所有数据集和较高L2正则化下，随机添加的虚假边在训练后权重分布显著小于真实边；RRA值普遍低于1（7/9条件下），接近零。
3. **自剪枝依赖于正则化强度**：较低L2时自剪枝减弱甚至消失（高覆盖数据集下显著），表明强正则化是促进自剪枝的关键。
4. **自剪枝可作为模型机制合理性的启发式指标**：在合成数据中，RRA与学习权重和真实权重的相关系数负相关（r=-0.379）；在真实数据中，权重更大的边有更多的文献支持，间接验证了权重大小与机制相关性一致。
5. **自剪枝是一个逐渐出现的过程**：初始训练时，真假边权重分布无差异；随着训练进行，两者残差面积逐渐分离。

## 7. 优点：方法或实验设计上的亮点

- **新颖的系统级评估指标**：RRA不依赖具体通路先验，简洁、可解释、易于跨模型比较；零和一的参考点使结果直观。
- **将“Grokking”概念迁移到BINNs**：借鉴深度学习泛化理论中的稀疏化思想，为机制学习提供了新视角。
- **全面的统计建模**：使用GAMM控制网络拓扑混杂因素，验证了权重大小对预测的独立贡献，增强了结论可靠性。
- **工程贡献显著**：开源、MIT许可证、GPU加速代码，可复现性强；引入梯度噪声、幂迭代等现代技巧。
- **实验设计严谨**：多数据集（含合成真值）、多正则化水平、多随机种子、消融实验，提供了自剪枝现象的充分证据。

## 8. 不足与局限

- **自剪枝并非普适**：在高覆盖真实数据集上，低L2时未观察到自剪枝，而此时预测性能最优。提示自剪枝可能与预测精度存在权衡，需要进一步研究。
- **模型简化导致局限**：LEMBAS假设相互作用独立、忽略细胞区室化等，可能迫使模型利用虚假边补偿欠参数化，限制了自剪枝的完美实现。
- **RRA指标自身局限**：RRA是相对指标，如果模型将很多真实边也剪枝了，仍可获得低RRA。因此自剪枝是必要非充分条件，需结合其他指标。
- **缺乏跨框架验证**：仅测试了LEMBAS一种BINN，无法证明其他BINNs（如基于GCN的、基于注意力的）也具备相同性质。
- **实验设计偏向**：虚假边生成方式单一（随机添加、保持度分布），未模拟更真实的先验知识噪声（如错误符号、缺失边、不属于该细胞类型的正确边等）。后者可能对自剪枝产生不同影响。
- **计算资源需求仍较高**：虽然GPU加速了7倍，但ensemble训练仍需大量GPU时间，可能限制非专业用户的复现。

（完）
