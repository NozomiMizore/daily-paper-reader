---
title: "{Sigma}0-EvoCell: An AI-Native Ontology that Unifies Evolutionary and Cell Biology in Latent Space"
title_zh: "Σ0-EvoCell: 一种统一进化生物学与细胞生物学于潜空间的人工智能原生本体论"
authors: "Pan, L."
date: 2026-07-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.15.738795v1.full.pdf"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 直接针对利用原生AI本体预测遗传扰动效应
tldr: "当前基础模型难以预测遗传扰动效应，因生物知识需损失性重编码才能被神经网络处理。本文提出进化细胞本体（ECO），基于Sigma0底物，将生物知识表示为携带双重语义（进化与细胞时间尺度）的向量编码关系图，并使用16个结构算子同时作为知识符号和张量操作。通过潜在空间通信协议（LSCP）将ECO图映射到语言模型残差流，实现知识审计。在珠蛋白进化模拟中，ECO恢复长程共进化耦合，祖先状态重建准确率达82-91%；细胞周期模拟中，CDK-周期蛋白注意图自发产生四吸引子相图；跨60个蛋白家族对齐时，ECO嵌入距离与进化分歧显著相关（r=0.50）。该工作以AI处理约束替代人类可读性约束，将模型不透明性转化为可测量的覆盖图。"
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-15-738795-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1382, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-15-738795-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1324, \"height\": 260, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-15-738795-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1683, \"height\": 570, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-15-738795-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1697, \"height\": 552, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-15-738795-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1690, \"height\": 574, \"label\": \"Figure\"}]"
motivation: 现有基础模型在分子序列上表现良好，但预测遗传扰动效果差，且生物知识需损失性重编码才能被模型处理，导致统计相关与机制理解间的鸿沟。
method: 提出ECO本体，使用16个结构算子将生物知识表示为向量编码的关系图，算子同时具有进化和细胞时间尺度的双重语义，并通过LSCP协议映射到语言模型残差流中。
result: "珠蛋白进化模拟恢复长程共进化耦合，祖先状态重建准确率82-91%；细胞周期模拟再现振荡周期和四吸引子相图；潜在空间对齐中ECO距离与蛋白进化分歧相关（r=0.50），且关系型概念编码弱于序列事实。"
conclusion: ECO用AI处理约束替代人类可读性约束，将基础模型的不透明性转化为可测量、可导航的覆盖图，提升了模型对机制性知识的表达能力。
---

## 摘要
生物学基础模型在分子序列和单细胞转录组学的模式识别上取得了令人瞩目的成就，但在预测遗传扰动效应方面却未能超越简单的线性基线，暴露了统计相关性与机制理解之间的差距。这一差距因接口问题而加剧：生物学知识以人类可读格式（FASTA、SBML、本体三元组）存在，在神经网络能够推理之前必须进行有损的重新编码。在此，我们引入进化细胞本体论（ECO），这是一种基于Σ0基底构建的人工智能原生形式语言，将生物学知识直接表示为向量编码的关系图。ECO使用16个结构算子，同时作为知识符号、张量操作，并且——关键的是——承载跨越进化时间尺度和细胞时间尺度的双重语义，因此，在系统发育尺度上表示物种形成的同一算子，在细胞周期尺度上表示不可逆的APC/C承诺。我们定义了一个潜空间通信协议（LSCP），将ECO图映射到大语言模型的残差流中，从而能够系统审计模型实际包含的生物学知识。我们通过受控模拟在三个领域展示了ECO：（i）跨越约15亿年的珠蛋白家族进化，其中ECO上位性注意力恢复了长程共进化耦合，祖先状态重建根据保守类别达到82-91%的准确率；（ii）哺乳动物细胞周期动态，其中包含GATE检查点和FUSE承诺节点的CDK-细胞周期蛋白注意力图在没有显式编程的情况下产生了两个完整振荡周期，并出现四吸引子相图；（iii）潜空间对齐，其中ECO嵌入距离追踪了60个蛋白质家族的趋异度（Pearson r = 0.50），一个说明性的LSCP审计表明，关系型多尺度概念的编码远弱于序列级事实。ECO用人工智能处理约束取代了人类可读性约束，并在此过程中将基础模型的不透明性转化为可测量、可导航的覆盖图。

## Abstract
Foundation models for biology achieve impressive pattern recognition on molecular sequences and single-cell transcriptomics, yet they fail to outperform simple linear baselines for predicting genetic perturbation effects, exposing a gap between statistical correlation and mechanistic understanding. This gap is compounded by an interface problem: biological knowledge lives in human-readable formats (FASTA, SBML, ontology triples) that must be lossily re-encoded before a neural network can reason about them. Here we introduce the Evolutionary Cell Ontology (ECO), an AI-native formal language built on the {Sigma}0 substrate that represents biological knowledge directly as vector-encoded relational graphs. ECO uses 16 structural operators that serve simultaneously as knowledge glyphs, tensor operations, and--critically--carry a dual semantics spanning both evolutionary and cellular timescales, so the same operator that denotes speciation at the phylogenetic scale denotes irreversible APC/C commitment at the cell-cycle scale. We define a Latent Space Communication Protocol (LSCP) that maps ECO graphs into the residual stream of large language models, enabling systematic auditing of the biological knowledge a model actually contains. We illustrate ECO across three domains using controlled simulations: (i) globin protein-family evolution across roughly 1.5 billion years, where ECO epistatic attention recovers long-range coevolutionary couplings and ancestral-state reconstruction reaches 82-91% accuracy graded by conservation class; (ii) mammalian cell-cycle dynamics, where a CDK-cyclin attention graph with GATE checkpoints and FUSE commitment nodes reproduces two full oscillatory cycles with a four-attractor phase portrait emerging without explicit programming; and (iii) latent-space alignment, where ECO embedding distance tracks divergence across 60 protein families (Pearson r = 0.50) and an illustrative LSCP audit projects that relational, multi-scale concepts are encoded far more weakly than sequence-level facts. ECO replaces the human-readability constraint with an AI-processing constraint and, in doing so, turns the opacity of foundation models into a measurable, navigable coverage map.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：当前生物学基础模型（如 scGPT、Geneformer）在分子序列和单细胞转录组模式识别上表现优异，但在预测遗传扰动效应（单/双扰动）时，未能超越简单的线性基线（如加法模型）。这暴露了统计相关性与机制理解之间的鸿沟：模型学习的是表达模式的统计相关性，而非因果、多尺度、关系性的生物机制。此外，生物知识以人类可读格式（FASTA、SBML、OWL/RDF 三元组）存在，必须经过有损的 tokenization 和重嵌入才能被神经网络处理，丢失了机制所需的关系结构。
- **整体含义**：论文提出一个正式的 AI 原生形式语言——进化细胞本体（Evolutionary Cell Ontology, ECO），使生物知识直接以向量编码的关系图形式被 AI 系统原生推理，消除接口损失，并将基础模型的不透明性转化为可测量、可导航的覆盖图，从而为可解释、因果性的虚拟细胞建模提供底层基础。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：基于 Σ0 底物构建 ECO，使用 16 个结构算子（如 BIND、EMIT、FUSE、GATE、GROW 等），每个算子同时作为 Unicode 符号、前缀无偏二进制码（按 Solomonoff 先验分配，高频算子用短编码）、以及具体的张量操作。**双重语义**是定义性特征：同一算子在进化尺度（如 FUSE 表示物种形成）和细胞尺度（如 FUSE 表示 APC/C 介导的有丝分裂不可逆承诺）具有具体但结构相同的含义。每个 ECO 值携带尺度标注（量子→分子→细胞→组织→生物体→进化→元尺度），关系是类型化态射，emerge 构建不可约类型，相位转变作为控制流原语。
- **关键技术细节**：
  - **Latent Space Communication Protocol (LSCP)**：将生物知识解析为 ECO 注意力图，向量化为前缀无偏包（携带结构码和 float32 语义内容），注入大语言模型的残差流。反向过程通过 ECO 概念向量查询模型并解码为结构化覆盖报告，将模型不透明性转化为可导航的知识地图；每个低覆盖格点对应具体算子/尺度坐标，直接提名需要补充的实验。
  - 没有给出具体的数学公式，但描述了算子功能（例如 BIND 创建关系、EMIT 求值、FUSE 不可逆融合、GATE 条件相位门等），以及它们如何映射到张量操作。
  - 注意：所有模拟实现基于 NumPy 和 SciPy，未使用深度学习梯度训练；这是受控模拟，非实际模型训练。

## 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- **三个受控模拟场景**（非实测数据）：
  1. **珠蛋白家族进化**：选择 8 个代表性珠蛋白（α-、β-血红蛋白、肌红蛋白、脑红蛋白、胞红蛋白等），将每个蛋白表示为 16 维物理化学向量（疏水性、电荷、大小、极性等）。使用四头上位性注意力（带线性位置衰减）计算共进化耦合。**无序列比对或替换模型**，仅从物理化学向量恢复耦合与分支。**没有外部基准**，只与内部保守类比较（例如血色素接触残基重建准确率 91% vs 可变环 73%）。分歧时间为近似数量级，非校准日期。
  2. **哺乳动物细胞周期动态**：编码 8 个调节因子（细胞周期蛋白 D/E/A/B、Rb/E2F 开关、APC/C 辅因子 Cdh1、纺锤体检查点 MAD2），检查点作为 GATE 算子，APC/C 驱动作为 FUSE 算子。使用 Novak-Tyson 风格的 CDK-细胞周期蛋白 ODE 模型（含 Wee1/Cdc25 双稳态），集成 60 小时。**无对比方法**，结果与已知细胞周期定性特征（周期波顺序、检查点、四吸引子相图）一致。
  3. **潜空间对齐与知识审计**：生成 60 个蛋白质家族（6 类：珠蛋白、激酶、转录因子、结构蛋白、通道/泵、伴侣蛋白）的物理化学向量，PCA 投影展示功能分离。ECO 余弦距离与合成的分歧度（种内 50-400 Mya，种间 400-2000 Mya）计算 Pearson 相关性（r=0.50）。**LSCP 审计是假设性投影**（图 4C），非实测 ESM-2 或任何生产模型，仅展示审计预期形状。

- **Benchmark**：未使用现有标准数据库或基准；所有比较为内部一致性评估。
- **对比方法**：无；论文旨在概念验证 ECO 框架的内部行为。

## 4. 资源与算力

- 论文**未明确说明**使用的 GPU 型号、数量或训练时长。所有模拟用 NumPy 和 SciPy 在 CPU 上实现，没有深度学习训练过程。因此无法评估计算资源需求。

## 5. 实验数量与充分性

- **实验数量**：三个模拟场景：
  - 珠蛋白：1 个案例（8 个蛋白），5 个内部节点重建。
  - 细胞周期：1 个 ODE 模型，运行 60 小时（两个周期）。
  - 60 家族对齐：1770 对距离比较，1 个相关性分析。
  - LSCP 审计：未实测，仅投影。
- **充分性**：作为概念验证，实验覆盖基本领域，但数量较少，**缺乏消融实验**（例如仅用部分算子、不同尺度标注）、**缺乏与传统方法定量比较**（如最大似然系统发育重建、HMM、标准动/静电场方程）。所有数据为受控合成，未在真实测序或单细胞数据上验证。因此**实验充分性有限**，论文也明确指出这是“设置下一阶段程序”，非实证验证。

- **客观性与公平性**：结果内部一致，但未与现有基准对比；在受控设定下选择参数可能偏向有利于 ECO 的展示（如物理化学向量选择、合成分歧结构）。细胞周期相图涌现虽声称无显式编程，但 ODE 模型本身已包含关键双稳态，降低了涌现的新颖性。

## 6. 论文的主要结论与发现

- 16 个算子集携带双重语义足以描述从密码子共进化到有丝分裂承诺的跨尺度过程。
- 珠蛋白模拟中，ECO 上位性注意力恢复了长程共进化耦合（嵌入距离与进化分歧 r=0.69），祖先状态重建准确性按保守类分级（血色素接触 91%、配体结合 88%、可变环 73%），且无需序列比对。
- 细胞周期模拟中，从 GATE 和 FUSE 算子组成的注意力图自发产生具有正确顺序的四吸引子相图，无需显式编程细胞周期相位。
- 60 家族潜空间对齐中，ECO 余弦距离与合成分歧度弱相关（r=0.50），功能类分离良好。
- LSCP 审计协议的设计表明可系统性探测模型知识覆盖，且预期关系型、多尺度概念（如基因调控、细胞周期控制、表观遗传、跨尺度涌现）编码弱于序列事实，这解释了当前基础模型在预测扰动效果上的失败。

## 7. 优点

- **创新性**：提出 AI 原生本体概念，同时作为知识表示、可执行注意力图和与 LLM 的通信协议，解决了生物知识接口损失问题。
- **形式统一**：16 个算子的双重语义设计将进化和细胞生物学统一在同一形式语言下，体现“过程本体论”立场，具有理论深度。
- **可审计性**：LSCP 将模型不透明性转化为可导航的覆盖图，每个低覆盖区直接提名需要补充的实验，具有实用诊断价值。
- **概念验证充分**：在三个代表性领域展示了框架的内部一致性，验证了从无序列信息中恢复进化结构和涌现细胞周期动态的能力。

## 8. 不足与局限

- **所有结果为受控模拟**，未使用真实测序、单细胞或实验数据验证，与“虚拟细胞”目标仍有巨大距离。
- **缺少与传统方法定量比较**：未与标准系统发育方法（如最大似然、贝叶斯）、细胞周期定量模型拟合（如针对具体细胞系）、或现有知识图谱（如 GO、REACTOME）比较性能。
- **合成数据局限性**：珠蛋白分歧时间为近似数量级，60 家族分歧为合成值，不能替代真实进化距离；细胞周期 ODE 模型未拟合真实动力学参数（如时间尺度、浓度）。
- **LSCP 审计未实测**：图 4C 是假设性投影，未对 ESM-2 或任何语言模型进行实际注入和量化，缺少真实覆盖分数。
- **缺乏消融实验**：未分析不同算子组合、尺度标注缺失、注意力头数等对性能的影响，无法评估框架各部分必要性。
- **可扩展性待验证**：仅处理小规模（8 蛋白、8 变量、60 家族），未讨论扩展到全蛋白组或全转录组的计算可行性和数值稳定。
- **未能解决学习问题**：ECO 算子集需领域专家手动构建（如将 CDK-细胞蛋白网络编码为注意力图），尚未实现自动从数据中学习 ECO 图，限制了端到端实用性。

（完）
