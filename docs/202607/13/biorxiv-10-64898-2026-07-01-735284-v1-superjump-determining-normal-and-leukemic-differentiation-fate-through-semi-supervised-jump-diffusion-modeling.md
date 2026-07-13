---
title: "SupeRJump: Determining normal and leukemic differentiation fate through semi-supervised jump diffusion modeling"
title_zh: SupeRJump：通过半监督跳跃扩散模型确定正常和白血病分化命运
authors: "Bowman, M., Bandopadhyay, R., Singh, V., Telpoukhovskaia, M., Vander Velde, R., Shaffer, S. M., Trowbridge, J. J., Bowman, R. L."
date: 2026-07-07
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.01.735284v1.full.pdf"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 使用半监督跳跃扩散模型从单细胞数据预测细胞命运
tldr: 单细胞RNA测序可解析分化动态，但现有方法无法处理白血病中不连续分化。为此提出SupeRJump，一种基于跳跃-漂移-扩散的半监督细胞命运模型，通过半监督伪时间策略和吸收马尔可夫链预测谱系命运，并引入量化细胞偏向和不连续转变的度量。应用于人骨髓、衰老造血和AML模型，识别出偏向分化的细胞及其转录网络，揭示了导致分化不连续的基因程序。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-01-735284-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 2057, \"height\": 1812, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-01-735284-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 2089, \"height\": 1702, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-01-735284-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 2149, \"height\": 2401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-01-735284-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 2129, \"height\": 2683, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-01-735284-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 2196, \"height\": 2810, \"label\": \"Figure\"}]"
motivation: 现有方法无法评估恶性白血病中的不连续分化过程，需要新模型来捕捉跳跃式转变。
method: 提出SupeRJump，采用半监督伪时间策略拟合跳跃-漂移-扩散模型，结合批次校正和吸收马尔可夫链进行谱系命运预测。
result: 成功应用于人骨髓、衰老造血和AML模型，识别出偏向分化的细胞及导致分化不连续的基因程序。
conclusion: SupeRJump可有效分析正常和白血病分化中的连续与不连续动态，揭示关键转录网络。
---

## 摘要
单细胞RNA测序（scRNA）为细胞和克隆异质性提供了前所未有的分辨率。计算方法已能够恢复分化动态，但现有方法无法评估恶性白血病中存在的非连续分化过程。为解决这些不足，我们开发了SupeRJump：一种基于跳跃-漂移-扩散的监督细胞命运模型（https://github.com/namwob44/SupeRJump/）。我们将该方法应用于人类骨髓、小鼠衰老造血以及慢病毒条形码标记的急性髓系白血病小鼠模型。我们的框架引入了一种半监督伪时间策略来拟合跳跃-漂移-扩散模型，并通过吸收马尔可夫链进行谱系命运预测的批次校正。我们引入了量化细胞向特定谱系偏斜程度、通过中间祖细胞状态向终末分化状态的转变，以及非连续转变动态的指标。利用这些指标，我们识别出优先偏向分化的细胞、其背后的转录网络以及导致分化不连续的基因程序。

## Abstract
Single cell RNA-seq (scRNA) has provided unprecedented resolution into cellular and clonal heterogeneity. Computational approaches have enabled recovery of differentiation dynamics, yet current approaches do not evaluate discontinuous differentiation processes present in malignant leukemia. To address these gaps, we developed SupeRJump: a jump-drift-diffusion based supervised cell-fate model (https://github.com/namwob44/SupeRJump/). We deploy this approach in human bone marrow, murine aging hematopoiesis, and lentivirally barcoded mouse models of acute myeloid leukemia. Our framework introduces a semi-supervised pseudotime strategy to fit a jump-drift-diffusion model and batch correction for lineage fate predictions from absorbing Markov chains. We introduce metrics to quantify a cells skewness toward particular lineages, transitions through intermediate progenitor states toward terminally differentiated states, and discontinuous transition dynamics. We use these metrics to identify cells preferentially biased for differentiation, their underlying transcriptional networks, and gene programs responsible for differentiation discontinuity.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
单细胞 RNA 测序（scRNA）已能高分辨率解析细胞异质性和分化动态。然而，现有计算方法主要假设分化是连续扩散过程，无法有效处理恶性白血病中存在的**非连续（跳跃式）分化**，例如白血病细胞绕过某些中间状态直接进入终末分化。这种不连续性是白血病异常造血的关键特征。因此，作者开发了 **SupeRJump**——基于跳跃-漂移-扩散（jump-drift-diffusion）模型的半监督细胞命运推断框架，旨在同时捕捉连续与不连续的分化动态，并识别推动这些不连续过程的转录程序。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：将细胞分化建模为具有跳跃项（jump）的随机微分方程，弥补传统纯扩散模型（如 diffusion map）中邻居数量受限、无法表达稀疏状态间的跳跃转换的缺陷。
- **关键技术细节**  
  - **半监督伪时间**：用户可选择自定义基因集或使用 Seurat 的 `FindAllMarkers` 导出终末集群的标志基因，通过 `AddModuleScore` 计算伪时间；当多组件伪时间时，采用**熵效率**合并为单一伪时间。
  - **余弦相似度变换**：将 PCA 空间中的细胞坐标转为余弦相似度（方向性度量），改善高维聚类。
  - **跳-漂-扩散模型拟合**：对每个主成分（PC）和每个细胞类型（通过“特征细胞” eigen cell 表示），优化一组参数（漂移项 μ、扩散项 σ、跳跃率 λ、跳跃幅度 θ、跳跃方差 φ），目标是最小化负对数似然。获得的概率经加权后形成细胞‑细胞转移概率矩阵（TPM）。
  - **吸收马尔可夫链**：将 TPM 划分为过渡态和吸收态（终末分化细胞），计算基础矩阵得到**命运概率**（每个细胞到达各谱系的概率）、**访问概率**（过渡态之间被遍历的概率）、**条件平均首达时间**（到达某个中间状态的期望步数）和**加权目的地时间**（综合访问几率与速度），并实施类似 ComBAT 的批次校正。
  - **偏倚细胞检测**：对某集群内每个细胞，基于其命运概率、该谱系成员概率和自身集群成员概率构建经验 CDF 的异常得分，经 Huber 鲁棒回归和 Tukey 准则筛选出偏向特定谱系的细胞。
  - **JumpROPE**：识别需用跳跃拟合的 PC‑细胞类型对，提取该 PC 中正/负载荷基因，进行 GO 富集分析，揭示可能驱动不连续过程的生物学通路。

## 3. 实验设计
- **数据集/场景**  
  1. **人类骨髓**[Setty et al., Palantir 数据]：用于比较跳跃模型与纯扩散模型的性能，评估伪时间与吸收步数的相关性。  
  2. **正常小鼠衰老造血**[Young et al.]：14 个生物学样本（年轻 vs 中年），共 52967 个细胞，用于分析年龄相关谱系偏倚及 JumpROPE。  
  3. **慢病毒条形码小鼠急性髓系白血病（AML）模型**（Npm1<sup>c-Frt</sup> /Flt3<sup>ITD-Frt</sup>，CROP-seq）：体外培养 9 天，7348 个细胞，含 75 个克隆（≥5 个细胞），用于实验验证克隆内命运一致性。
- **对比方法**：主要对比 **纯扩散模型**（不包含跳跃项，类似 CellRank2 风格），通过比较伪时间与吸收步数相关性、分布拖尾、网络同配性、访问概率热图等。未与其他完整单细胞轨迹推断方法（如 Palantir、CellRank2、destiny）做系统基准测试，仅在跳跃 vs 扩散层面进行了消融对照。
- **评估指标**：Pearson 相关性、吸收步数分布、同配性系数、差异基因表达、转录因子活性（使用 decoupleR + SwissRegulon 网络）显著性检验等。

## 4. 资源与算力
**文中未明确说明**使用的 GPU 型号、数量或训练时长。代码实现基于 R（nloptr 包进行约束优化），运行在普通计算服务器上即可。作者未报告硬件细节，也未提及其他专用的算力消耗或训练时间。

## 5. 实验数量与充分性
- **数量**：覆盖 3 个不同数据集（包括体内和体外实验），每个数据集内部进行多项分析（如跳跃 vs 扩散的对比、批次校正效果、偏倚细胞检测、克隆内 fate 相关性、JumpROPE 通路提取）。
- **消融实验**：明确比较了纯扩散与跳跃-扩散模型，展示了跳跃带来的相关性提高和分布正态化；评估了批次校正前后的 fate 概率；在 AML 数据中比较了克隆内 vs 克隆间命运连接。
- **充分性与公平性**：实验设计合理，验证了跳跃模型在仿真和真实数据上的优势。但**不足**在于：
  - 未与现有主流命运推断方法（如 CellRank2、Palantir、CytoTRACE）在相同度量下进行全面定量比较；
  - 仅用了一个人体数据集和一个正常小鼠数据，缺乏更多异质性系统（如其他血液病或非造血组织）的验证；
  - 跳跃参数拟合的稳定性未充分讨论（如是否对初始值敏感、收敛性分析）。

## 6. 主要结论与发现
1. **跳跃模型优于纯扩散**：跳跃模型下的伪时间与吸收步数的相关性更高（r = −0.857 vs −0.794），且吸收步数分布无明显拖尾（峰度 0.6 vs 26.44），说明跳跃模型能更均匀、更真实地捕获细胞间转换。
2. **访问概率揭示不同分支路径**：跳跃模型允许更多跨集群连接（同配性 0.33 vs 0.75），可识别不同的祖细胞分支偏好。
3. **批次校正保留生物学信号**：细胞谱系特异性转录因子（如 IRF8、GATA1）表达与其 fate 概率呈正相关，且不同重复间行为一致。
4. **JumpROPE 发现不连续相关通路**：例如 GMP 向 PC4 跳跃时，负载荷基因富集细胞周期，正载荷基因富集 ER 应激/转录调控，提示 ER 应激在 GMP 命运决定中的作用。
5. **衰老增加中性粒细胞偏倚**：中年小鼠 GMP 中中性粒细胞偏倚细胞比例增加（8.3% vs 6.4%），且偏倚细胞中 Ddit3、Xbp1（UPR 通路）活性降低。
6. **慢病毒条形码验证克隆内 fate 倾向**：同一克隆内 HSPC/MultiLin→cDC 的 fate 概率显著高于跨克隆连接，且同一克隆的中间状态访问概率更高、速度更快。

## 7. 优点
- **创新性**：首次将跳跃-扩散模型引入单细胞命运映射，弥补了现有扩散方法无法处理不连续分化的空白。
- **丰富的新指标**：引入访问概率、加权目的地时间等，可评价细胞通过中间状态的概率和速率，超越了简单的 fate 概率。
- **半监督伪时间**：允许用户指定基因集或通过差异标记自动生成，灵活适应不同生物学场景。
- **批次校正**：解决了不同条件和重复间细胞组成不均衡导致的 fate 偏差，提升统计效力。
- **实验验证**：利用慢病毒条形码体外培养系统，直接支持了模型预测的命运在不同克隆间的差异，增强可信度。
- **开源工具**：提供完整 R 包，易于复现和扩展。

## 8. 不足与局限
- **对比不完整**：未与多个现有命运推断方法（如 CellRank2、Palantir、Waddington-OT、VIA 等）进行全面、公平的基准测试，因此无法充分评估 SupeRJump 的整体性能排名。
- **依赖已知 TF 网络**：TF 活性推断基于 SwissRegulon 数据库，可能遗漏新或物种特异性互作，且无法发现未注释的 TF-靶基因规律。
- **偏倚检测的敏感性**：当大部分细胞已高偏向某谱系时，仅对极端异常值敏感，可能低估中等偏倚的细胞。
- **应用场景有限**：仅验证于造血系统（正常及白血病），在非造血组织或更复杂的多谱系系统中的泛化能力未知。
- **计算资源缺失**：未报告模型拟合的耗时、内存需求或 GPU 利用情况，难以评估方法的可扩展性（如处理 10 万级以上细胞的数据集）。
- **跳跃机制的解释性**：跳跃被抽象为节点概率搜索的扩展，但其生物学等价性（如是否为表观遗传开关、转录爆发等）缺乏深入解释。
- **试验覆盖不足**：衰老数据只有年轻 vs 中年，缺少老年阶段；AML 模型只有一个基因型（Npm1/Flt3-ITD），其他驱动突变的适用性不确定。

（完）
