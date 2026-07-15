---
title: "Reliability-weighted target prioritization in CD4+ T-cell Perturb-seq: a generalizability-theory decomposition"
title_zh: CD4+ T细胞Perturb-seq中的可靠性加权靶点优先排序：一种概化理论分解
authors: "Cheng, C."
date: 2026-07-15
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.13.738312v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: Perturb-seq; 单细胞扰动; 靶标优先级; 概化理论
tldr: 基因组Perturb-seq筛选常依据扰动效应强度排序目标，但忽略测量可靠性。本文引入概化理论，将效应分解为跨靶标、向导、供体、条件的可靠与特异部分，计算联合概化系数加权排序。在Zhu等数据上，去除测量误差后，可靠基因从40增至7674；激活状态分析显示TCR信号模块仅在活化细胞中可靠。该方法为筛选提供可靠性导向，表明增加向导数可提升可靠性。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738312-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1300, \"height\": 1238, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738312-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1645, \"height\": 923, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738312-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1678, \"height\": 860, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738312-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1193, \"height\": 798, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738312-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1614, \"height\": 590, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-13-738312-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1071, \"height\": 360, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-13-738312-v1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 944, \"height\": 309, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-13-738312-v1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1714, \"height\": 495, \"label\": \"Table\"}]"
motivation: 现有Perturb-seq优先排序基于效应强度，未考虑效应在不同向导与供体间的可重复性，导致假阳性成本高。
method: 应用概化理论，在Target×Guide×Donor×Condition设计中分解效应方差，计算联合概化系数作为可靠性权重。
result: 去除测量误差后，可靠基因数从40升至7674；TCR信号模块可靠性仅在活化细胞中可检测。
conclusion: 可靠性加权可减少假阳性，增加guide数比增加donor数更能提升可靠性，建议未来实验增加guide。
---

## 摘要
全基因组规模的Perturb-seq筛选通过扰动转录效应的强度来优先排序候选靶点。但效应强度并不能回答一个先验的测量问题：读数是否可靠？从单个向导、单个供体或少量细胞的伪批量中估计出的强效应不一定能复制，而对于靶点优先排序，每个错误线索都会导致一次验证实验的成本。我们将每个扰动效应视为一个交叉的靶点×向导×供体×条件设计中的测量，并应用概化理论（Cronbach等，1972；Brennan，2001）将效应的可靠部分与侧面特定的特异性分离开来。向导和供体作为随机侧面进入；条件作为固定侧面进入，并在其水平内进行分析。对于每个靶点，我们报告一个在侧面上的可靠性轮廓，以及两个随机侧面的联合概化系数，并根据该系数加权的效应大小重新排序靶点。在已发布的筛选数据（Zhu等，2025）中，移除从非靶向对照估计的测量误差下限后，具有可靠靶点信号份额高于0.10的基因数量从40个增加到7,674个。在激活状态内分析时，可靠性恢复了T细胞受体信号模块，仅在激活细胞中可靠测量，无需借助基因注释。一项设计研究表明，可靠性受向导数量而非供体数量的限制，因此未来的筛选应增加向导。所有方法论决策均被记录并经过对抗性审查，所有结果均可从已发布的汇总统计数据中再生。

## Abstract
Genome-scale Perturb-seq screens prioritize candidate targets by the strength of a perturbation's transcriptional effect. Effect strength does not answer a prior measurement question: is the readout dependable? A large effect estimated from a single guide, a single donor, or a pseudobulk of few cells need not survive replication, and for target prioritization each false lead costs a validation experiment. We treat each perturbation effect as a measurement in a crossed Target x Guide x Donor x Condition design and apply generalizability theory (Cronbach et al., 1972; Brennan, 2001) to separate the dependable part of an effect from facet-specific idiosyncrasy. Guides and donors enter as random facets; condition enters as a fixed facet and is analyzed within its levels. For each target we report a dependability profile over the facets and a joint generalizability coefficient over the two random facets, and we re-rank targets by effect magnitude weighted by that coefficient. On the released screen (Zhu et al., 2025), removing the measurement-error floor estimated from the non-targeting controls raises the number of genes with a dependable target-signal share above .10 from 40 to 7,674. Analyzed within activation states, dependability recovers the T-cell-receptor signaling module as reliably measurable only in activated cells, without recourse to gene annotation. A design study indicates that reliability is limited by the number of guides rather than the number of donors, so a future screen should add guides. Every methodological decision was recorded and adversarially reviewed, and all results regenerate from the released summary statistics.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：全基因组Perturb-seq筛选通常仅依据扰动效应强度（effect size）对候选靶点排序，忽略效应在不同实验条件（如不同向导、不同供体）下的可重复性。这导致大量“强但脆弱”的假阳性靶点被优先推荐，后续验证实验成本高昂。
- **背景**：已有研究关注可重复性（如不可重复发现率IDR、线性混合模型方差分解），但缺乏一个与效应强度结合的可排序的每靶点可靠性指标。本文引入**概化理论**（Generalizability Theory），将效应分解为可靠部分和侧面特异性噪声，提供联合概化系数用于加权排序，从而降低验证成本，提高筛选可信度。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- 将每个扰动效应视为一次测量，处于交叉设计：**Target × Guide × Donor × Condition**。
  - 对象 of measurement：靶点基因（target）。
  - 随机侧面：guide（每个靶点2个）、donor（每个靶点4个）——希望跨这些因素泛化。
  - 固定侧面：condition（Rest, Stim8hr, Stim48hr）——分别分析，不要求泛化。
- 基于方差分解，计算两个层面的可靠性系数：
  - **每靶点层面**：三个侧面可靠性系数（R_guide, R_donor, R_condition），以及联合概化系数 \( R_{\text{dep}} \)。
  - **设计层面**：整体概化系数 \( E\rho^2 \)。

### 关键技术细节
- **方差分解模型**（每基因拟合线性混合模型）：  
  \( y \sim condition + (1|\text{target}) + (1|\text{target:guide}) + (1|\text{target:donor}) \)  
  得到 \(\sigma^2_T, \sigma^2_{TG}, \sigma^2_{TD}\) 及残差（吸收三阶交互）。
- **每靶点可靠性系数**（基于分裂半相关，经验贝叶斯收缩）：
  - \( R_{\text{guide},t} \)：将靶点的2个guide分为两半，计算平均表达谱的Pearson相关。
  - \( R_{\text{donor},t} \)：将4个donor分为2对共3种分法，取平均相关后向全局均值收缩（Fay-Herriot形式，本文用简化全局权重0.5）。
  - 联合系数：  
    \( R_{\text{dep},t} = 1 / \left(1 + \frac{1-R_{\text{guide}}}{R_{\text{guide}}} + \frac{1-R_{\text{donor}}}{R_{\text{donor}}}\right) \)  
    仅当guide和donor误差独立时精确，否则为上界。
- **加权得分**：\( S_t = M_t \cdot R_{\text{dep},t} \)，其中 \( M_t \) 为效应幅度（表达谱的均方根）。
- **测量误差去除**：利用非靶向对照（non-targeting controls）的方差估计测量误差下限，从设计层面残差中减去，抬升靶点信号份额（target-signal share）。
- **设计研究（D-study）**：将概化系数投影到不同guide数和donor数组合上，识别限制因子。

## 3. 实验设计

- **数据集**：Zhu等人（2025）发布的CD4⁺ T细胞全基因组Perturb-seq筛选数据。
  - 约2200万细胞，12,731个靶点基因，每靶点约2个guide，4个donor，3种激活状态（Rest/Stim8hr/Stim48hr），共278,684个伪批量（pseudobulk）观测。
- **基准**：传统效应大小排序（单一效应强度指标）。
- **对比方法**：五种候选估计量：
  1. 每靶点因子ANOVA（不可识别，弃用）
  2. 精度加权交叉REML/GLS（用于设计层面，不用于每靶点）
  3. 核/距离分解（非方差分量，仅作诊断）
  4. 鲁棒层次泛函模型（假设强，计算重，作对照）
  5. **分裂半相关 + 经验贝叶斯收缩**（被选择，能在合成数据中恢复真实分量）
- **模拟数据**：在预注册的合成测试中，使用高斯噪声和重尾噪声验证估计量恢复能力。
- **设计研究**：在真实数据上改变guide数（1-12）和donor数（1-12），计算 \( E\rho^2 \)。

## 4. 资源与算力

- **文中未明确说明GPU型号、数量、训练时长**。作者提到“全规模蒙特卡洛门控确认计划在计算集群上运行”，但本文呈现的结果来自本地合成和真实数据层级。
- 由于仅使用已发布的汇总统计数据（伪批量表达矩阵），无需处理全单细胞数据，计算量相对较小。算法主要涉及线性混合模型（REML）和分裂半相关，可在一般计算节点上完成。
- **可复现性**：代码公开（Apache-2.0），所有结果可一键再生。

## 5. 实验数量与充分性

- **主要实验**：一个真实数据集分析，回答四个研究问题（RQ1-RQ4），包括每靶点重排序、激活状态特异性、整体可靠性、设计优化。
- **合成实验**：在预注册中选择估计量时，进行了模拟恢复测试（两种噪声类型）。
- **无正式消融实验**：但对比了五种候选方法，并记录了决策路径。
- **设计研究**：系统扫描了guide和donor数量组合（至少7种guide×6种donor=42种组合），提供热力图。
- **公平性**：预注册的估计量选择基于合成数据的恢复能力，而不是基于真实结果的外观。所有决策记录在GitHub Issues中并接受对抗性审查（GPT-5.6 Sol模型进行攻击并解决）。
- **不足**：仅基于一个数据集（特定细胞类型、特定筛选设计），泛化性需更多验证。供体数仅4，自由度低，导致系数噪音大。

## 6. 论文的主要结论与发现

1. **RQ1**：可靠性加权排序大幅重排了候选列表：效应大小排名前100的靶点中有50个在加权后跌出前100；RPS3从79位升至4位。说明单纯效应大小会偏向脆弱靶点，而可靠性加权能检出可复制的效应。
2. **RQ2**：在激活状态内分析，92个靶点表现出状态特异性可靠性。TCR信号模块（CD3D, CD3G, CD247, ZAP70, LAT）仅在活化细胞中可靠，静息态处于噪声底限——无需基因注释，方法自行重构了功能模块。
3. **RQ3**：去除测量误差后，整体概化系数 \( E\rho^2 \approx 0.44 \)（中等可靠），可靠信号基因数从40增至7,674（增加192倍）。此系数为当前设计（2 guides, 4 donors）下靶点分数与独立复制间期望相关。
4. **RQ4**：限制因素是**guide数量**而非donor数量：guide误差项是donor误差项的2.4倍；增加1个guide的效果约等于增加3个donor；达到0.70可靠性需要约15个guide，而增加donor无法突破上限。建议未来实验增加guide数。

## 7. 优点

- **方法论创新**：首次将概化理论系统应用于Perturb-seq可靠性评估，巧妙地区分随机侧面和固定侧面，提供每靶点联合可靠性系数。
- **实用导向**：直接输出可排序的加权得分，帮助实验人员优先选择高可靠性靶点，减少验证成本。
- **生物学验证**：通过TCR模块重建证明可靠性系数反映真实生物学信号，而非统计伪像。
- **透明可复现**：全流程代码公开、决策记录在GitHub、对抗性审查、预注册合成选择、所有结果可一键再生。
- **设计指导**：D-study明确提供量化建议（增加guide数），对后续实验设计有直接价值。
- **测量误差处理**：利用非靶向对照估计误差下限，揭示了被噪声掩盖的大量可靠信号。

## 8. 不足与局限

- **数据局限**：仅4个供体，自由度低，donor方差分量和系数不稳定（尽管使用了收缩）。
- **模型假设**：guide和donor误差独立，忽略guide×donor交互作用，实际交互存在时联合系数为上界而非精确值。
- **Pearson相关**：测量一致性而非幅度一致性，可能遗漏纯量变；未使用Concordance Correlation。
- **测量误差去除**仅作用于设计层面残差，未在每靶点分裂半系数层面单独处理；分裂半相关本身仍受测量误差影响。
- **计算验证**：全规模蒙特卡洛门控确认尚未完成（仅计划）。
- **混淆因素**：测序批次与供体部分混淆，未矫正。
- **效应估计**：使用log-CPM相对差值，对低计数基因采用截断处理，作者承认替代负数二项模型可能更优但排名大致稳健。
- **泛化性**：结果基于单一细胞类型和特定筛选平台（CRISPRi），其他场景（如CRISPRn、其他组织）需另行验证。
- **整体可靠性中等**（0.44），无法对单个靶点做绝对结论，仅适用于相对排序。

（完）
