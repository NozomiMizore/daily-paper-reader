---
title: "CSGDA: A Cell State-Guided Graph Domain Adaptation Network for Single-Cell Drug Response Prediction"
title_zh: CSGDA：一种细胞状态引导的图域自适应网络用于单细胞药物反应预测
authors: "Yan, F., Cao, X., Mao, F., You, Z., Chen, Y., Du, Z., Huang, Y.-A."
date: 2026-07-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.02.735966v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 基于领域适应的单细胞药物响应预测
tldr: "单细胞药物反应预测面临体外到体内、原发到转移等跨域分布偏移挑战，现有方法极少针对性解决。本文提出CSGDA，将基因表达映射为功能细胞状态，引导图结构学习，并采用图域适应与重叠惩罚机制对齐分布。在五个scRNA-seq数据集上，CSGDA相较最优方法平均提升约6%的ACC和AUPR。在跨转移顺铂数据集中，模型通过集成梯度精准定位耐药关键基因，凸显其解析单细胞异质性的潜力，助力精准医学。"
source: biorxiv
selection_source: fresh_fetch
motivation: 跨域分布偏移（不同平台、微环境、转移演化）严重阻碍单细胞药物反应预测模型泛化，现有方法未有效解决。
method: 提出CSGDA，利用生物先验映射基因表达为细胞状态，引导图结构学习，结合图域适应与重叠惩罚机制实现跨域对齐。
result: "在五个scRNA-seq数据集上，CSGDA平均提升约6%的ACC和AUPR，并在跨转移顺铂场景中识别出耐药关键基因。"
conclusion: CSGDA有效解决单细胞跨域预测难题，提升精度并揭示耐药机制，为精准医学提供新工具。
---

## 摘要
瘤内异质性驱动癌症复发和转移，然而单细胞药物反应预测面临严重的“跨域”挑战，例如将体外模型应用于体内组织或从原发肿瘤推断转移耐药性。这些场景引发了由异质测序平台、不同组织微环境和转移演变引起的分布偏移——现有方法很少解决这些问题。我们提出了CSGDA，一种细胞状态引导的图域自适应框架，旨在跨这些生物异质性预测药物反应。CSGDA整合生物学先验知识将基因表达映射到功能性细胞状态，引导结构学习模块构建稳健的细胞拓扑。为了克服分布偏移，该模型采用图域自适应结合一种新颖的重叠惩罚机制。在五个scRNA-seq数据集上的广泛基准测试表明，CSGDA优于最先进的方法，在ACC和AUPR上平均提升约6%。除了预测准确性，我们还在一个具有挑战性的跨转移顺铂数据集中使用积分梯度有效定位了参与耐药性的关键基因。这些发现强调了CSGDA在单细胞药物反应预测中的优越性能及其在解决单细胞异质性方面的潜力，为精准医学铺平了道路。

## Abstract
Intratumoral heterogeneity drives cancer recurrence and metastasis, yet single-cell drug response prediction faces severe "cross-domain" challenges, such as applying in vitro models to in vivo tissues or inferring metastatic resistance from primary tumors. These scenarios trigger distribution shifts arising from heterogeneous sequencing platforms, distinct tissue microenvironments, and metastatic evolution - problems rarely addressed by existing methods. We introduce CSGDA, a cell state-guided graph domain adaptation framework designed to predict drug responses across these biological heterogeneities. CSGDA incorporates biological priors to map gene expression into functional cell states, guiding a structure learning module to construct robust cell topology. To conquer distribution shifts, the model employs graph domain adaptation combined with a novel overlap penalty mechanism. Extensive benchmarks on five scRNA-seq datasets demonstrate that CSGDA outperforms state-of-the-art methods, achieving an average gain of ~6% in ACC and AUPR. Beyond prediction accuracy, we employed integrated gradients to effectively pinpoint key genes involved in drug resistance within a challenging cross-metastasis cisplatin dataset. These findings underscore CSGDA's superior performance in single-cell drug response prediction and its potential in resolving single-cell heterogeneity, paving the way for precision medicine.

---

## 论文详细总结（自动生成）

# 论文总结：CSGDA: A Cell State-Guided Graph Domain Adaptation Network for Single-Cell Drug Response Prediction

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：单细胞药物反应预测面临严重的“跨域”分布偏移挑战，例如将体外模型（cell line）应用于体内组织，或从原发肿瘤推断转移性耐药。这些偏移源于异质测序平台、不同组织微环境和转移演化，现有方法（如SCAD、scDEAL等）主要依赖“Bulk-to-Single-Cell”跨模态迁移范式，未能有效处理高度异质的非独立同分布（non-I.I.D.）场景。
- **整体含义**：本文提出CSGDA框架，将单细胞药物反应预测从“Bulk-to-SC”转向“SC-to-SC”端到端范式，利用生物学先验（细胞状态）作为语义锚点，结合图结构学习和图域自适应，实现跨域泛化，旨在突破现有方法在真实临床场景（如跨组织、跨转移）中的性能瓶颈，为精准医学提供新工具。

## 2. 论文提出的方法论
### 核心思想
以“细胞功能状态”（如EMT、DNA修复等）作为跨域不变语义变量，引导图结构学习构建稳健拓扑，再通过图域自适应对齐跨域分布，并引入重叠惩罚机制增强决策边界鲁棒性。

### 关键技术细节（文字说明）
1. **细胞状态提取与伪标签分配**：
   - 从CancerSEA数据库构建状态-基因映射字典（8个功能状态），计算每个细胞在各状态下的活性得分（基于共享基因表达均值），采用“赢家通吃”原则分配伪标签（dominant state）。
2. **细胞状态感知图结构学习（CSA-GSL）**：
   - 基于细胞状态特征矩阵X，通过KNN构建初始噪声图G_init。
   - 借鉴ProGNN框架，联合优化图结构G和GNN参数θ，损失函数包括：分类引导损失、稀疏/低秩约束、特征平滑约束（基于归一化拉普拉斯矩阵）、以及保真度约束（防止结构坍缩）。
   - 采用交替优化：先对图结构梯度下降+近端算子（核范数、L1范数）更新，再固定图结构更新GNN参数。
3. **共享图Transformer编码器**：
   - 将基因表达通过线性层映射到低维空间，输入结构约束的多头注意力（只聚合图中相邻节点），经残差连接、批归一化、FFN更新。
   - 引入随机潜在正则化（重参数化技巧）增强鲁棒性。
4. **图域自适应模块（GDA）**：
   - 对抗性域对齐：通过梯度反转层（GRL）最小化域分类损失，使编码器提取域不变特征。
   - 目标域信息熵最小化：强制目标域预测接近决策边界。
   - 分类优化（重叠惩罚）：定义敏感/耐药类别的预测概率分布，通过Overlap Loss（L_olp）拉大类间间隔，公式为 \( L_{olp} = \frac{1}{|S_{pos}||S_{neg}|} \sum_{s_a \in S_{pos}} \sum_{s_u \in S_{neg}} \max(0, \mu + s_u - s_a) \)。
5. **总目标函数**：\( L_{total} = L_{cls} + \lambda_d L_{dom} + \lambda_e L_{ent} \)，其中 \( L_{cls} = \lambda_c L_{ce} + \lambda_o L_{olp} \)。采用动态热身策略控制 \(\lambda_d\) 和 \(\lambda_e\)。

## 3. 实验设计
- **数据集与场景**：5个scRNA-seq数据集，涵盖4种跨域场景：
  - 跨平台（Cross-Platform）
  - 跨细胞系（Cross-Cell Line）
  - 跨组织（Cross-Tissue）：单药治疗（Monotherapy）和联合治疗（Combination）
  - 跨转移（Cross-Metastasis，预测顺铂响应）
- **基准方法与对比**：与5种SOTA方法比较：SCAD、scDEAL、scAdaDrug、SSDA4Drug、scGSDR。评价指标：AUROC、AUPR、ACC、F1-macro。
- **消融实验**：分别移除生物先验（改为PCA+K-Means）、去除图学习模块（使用静态KNN/Pearson/Spearman）、去除域适应模块、以及单独使用交叉熵或重叠损失。
- **生物学可解释性分析**：利用集成梯度（Integrated Gradients）在跨转移顺铂数据集中识别耐药关键基因，并映射到CancerSEA功能状态。

## 4. 资源与算力
- **论文未明确说明**使用的GPU型号、数量、训练时长等算力信息。仅提到超参数通过网格搜索调优，但未报告具体训练资源。这是本文在可复现性方面的一个不足。

## 5. 实验数量与充分性
- **实验数量**：主要对比实验在5个数据集上进行，每个数据集均报告4项指标；消融实验包含4个变体分别在5个数据集上的结果（图4），另有范式对比实验（图3）和生物解释分析（图5、6）。总体来说实验组数较多（约30+组）。
- **充分性与公平性**：
  - 充分：覆盖了主要跨域类型，消融实验验证了各模块贡献，且进行了无监督域适应与半监督方法的对比。
  - 公平：超参数对baseline方法均按官方推荐设置，所有方法使用相同预处理数据。但CSGDA本身超参数（如α, β, λ等）仅在一组默认值上报告，未进行敏感性分析。
  - 局限：每个跨域类型仅对应一个数据集，缺乏更多样化数据验证；未比较与近期更多方法的性能（如仅5种baseline）。

## 6. 论文的主要结论与发现
- CSGDA在所有5个跨域场景中优于现有方法，平均提升ACC和AUPR约6%。
- 在跨组织单药治疗场景中，CSGDA将AUPR从0.839（去除域适应）提升至0.964，验证了域对齐的必要性。
- 生物学分析验证了模型识别耐药关键基因的能力：RAD51C（DNA修复通路）和TMEM205（跨膜排出泵）被正确识别，且模型能无监督发现非预设基因（如NDUFA11、NDUFS6）。
- 从“Bulk-to-SC”转向“SC-to-SC”范式可有效缓解流形结构不匹配问题，为后续研究提供了新方向。

## 7. 优点
- **方法创新性**：首次将细胞状态作为语义锚点引入图域自适应，利用生物学先验指导图学习，降低技术噪声影响，比纯统计方法更鲁棒。
- **解决真实挑战**：专门针对高异质性非I.I.D.场景（跨组织、跨转移），填补现有方法空白。
- **强可解释性**：集成梯度+状态映射的双向验证框架，能揭示耐药机制，辅助生物学发现。
- **无监督性**：在完全不使用目标域标签的情况下，性能超越半监督方法SSDA4Drug，具有实际应用价值。
- **消融设计完整**：依次验证了每个核心组件（生物先验、图学习、域适应、损失函数）的必要性。

## 8. 不足与局限
- **资源开销未报告**：缺乏GPU训练时间、内存消耗等细节，影响可复现性评估。
- **数据规模有限**：仅使用5个数据集，且每类跨域场景仅一个数据集，可能不足以证明泛化性。未来需更多肿瘤类型、药物和测序平台验证。
- **超参数敏感性未知**：图学习中的多个正则化参数（α, β, λ, φ, γ）及损失权重（λ_c, λ_o, λ_d, λ_e）未进行系统分析，最优解可能依赖数据集。
- **仅使用转录组数据**：未整合拷贝数变异、表观遗传等多组学，可能遗漏耐药关键因素。
- **临床应用距离**：模型基于已标记的scRNA-seq（source域有标签），实际中source域（如原发肿瘤）的标签获取可能困难；且未在独立临床队列测试。
- **计算复杂度**：基于ProGNN的图学习需要交替优化，每轮迭代涉及SVD分解，可能不适用于超大规模单细胞数据（>10万细胞）。

（完）
