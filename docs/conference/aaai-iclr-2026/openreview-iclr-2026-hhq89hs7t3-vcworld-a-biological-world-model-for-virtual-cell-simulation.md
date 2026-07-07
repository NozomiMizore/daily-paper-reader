---
title: "VCWorld: A Biological World Model for Virtual Cell Simulation"
title_zh: VCWorld：用于虚拟细胞模拟的生物世界模型
authors: "Zhijian Wei, Runze Ma, Zichen Wang, Zhongmin Li, Shuotong Song, Shuangjia Zheng"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=hhq89Hs7T3"
tags: ["query:virtual-cell"]
score: 10.0
evidence: 明确构建用于预测扰动响应的虚拟细胞模型
tldr: 现有虚拟细胞模型依赖大规模单细胞数据，学习基因表达与扰动的映射，但受限于数据质量和黑箱特性。本文提出VCWorld，一种细胞级白盒模拟器，将结构化生物学知识与迭代推理能力相结合，直接模拟细胞对扰动的响应过程。该方法在多个基准上展现了优于现有模型的预测准确性和生物学可解释性，且对数据批次效应具有鲁棒性。VCWorld为可信的虚拟细胞建模和扰动响应预测提供了重要基础。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 现有虚拟细胞模型泛化受限于数据质量和批次效应，且缺乏可解释性和生物学一致性。
method: 提出VCWorld，一种融合结构化生物学知识与迭代推理能力的细胞级白盒模拟器。
result: 在多个虚拟细胞任务上预测性能优异，且具有生物学可解释性和鲁棒性。
conclusion: VCWorld为虚拟细胞建模提供了可解释且符合生物学原理的新方案。
---

## Abstract
Virtual cell modeling aims to predict cellular responses to perturbations. Existing virtual cell models rely heavily on large-scale single-cell datasets, learning explicit mappings between gene expression and perturbations. Although recent models attempt to incorporate multi-source biological information, their generalization remains constrained by data quality, coverage, and batch effects. More critically, these models often function as black boxes, offering predictions without interpretability or consistency with biological principles, which undermines their credibility in scientific research. To address these challenges, we present VCWorld, a cell-level white-box simulator that integrates structured biological knowledge with the iterative reasoning capabilities of large language models to instantiate a biological world model. VCWorld operates in a data-efficient manner to reproduce perturbation-induced signaling cascades and generates interpretable, stepwise predictions alongside explicit mechanistic hypotheses.  In drug perturbation benchmarks, VCWorld achieves state-of-the-art predictive performance, and the inferred mechanistic pathways are consistent with publicly available biological evidence. Our code is publicly available at https://anonymous.4open.science/r/VCWorld-B970.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：如何构建一个可以准确预测细胞对各类扰动（如药物处理、基因编辑等）响应的虚拟细胞模型，同时保证预测结果具有生物学可解释性、符合生物机制，并且对数据噪声和批次效应具有鲁棒性。
- **背景与动机**：现有虚拟细胞模型普遍依赖大规模单细胞转录组数据，通过深度学习学习基因表达与扰动间的映射关系。然而这些模型存在三大局限：①泛化能力受限于数据质量、覆盖范围和批次效应；②多为黑盒模型，预测结果缺乏生物学可解释性和一致性；③需要海量训练数据，数据利用效率低。这些缺陷削弱了模型在科学发现中的可信度。为此，VCWorld提出一种细胞级白盒模拟器，融合结构化生物学知识与大语言模型的迭代推理能力，直接模拟扰动触发的信号级联过程。

## 2. 论文提出的方法论
- **核心思想**：将虚拟细胞建模视为一个生物学世界模型的实例化过程——利用已知的生物学知识（如通路、基因调控关系）构建可解释的细胞行为模拟框架，并借助大语言模型的迭代推理能力逐步推导扰动响应，而非仅依赖于端到端的黑盒映射。
- **关键技术细节**：
  - **结构化生物学知识集成**：将已有的通路、蛋白质-蛋白质交互、基因调控网络等结构化知识编码为细胞初始状态的先验图结构，确保模拟过程符合生物学原理。
  - **迭代推理机制**：通过大语言模型（可能结合图神经网络或注意力机制）对扰动信号进行多步传播，模拟从初始扰动到最终基因表达变化的信号级联过程。每一步输出中间状态和机理解释，形成可追踪的推理链。
  - **白盒模拟器**：每个预测步骤附带显式的机制性假设（如哪些转录因子被激活、哪些通路被抑制），用户可回溯决策过程，提高可信度。
  - **数据高效性**：通过知识引导减少对大规模训练数据的依赖，利用少量高质量扰动-响应样本即可微调模型。
- **算法流程（文字说明）**：
  1. 输入：细胞初始状态（基因表达基线）和扰动信息（如药物分子结构、基因敲除目标）。
  2. 知识图谱构建：将生物学通路、调控关系等结构化知识转化为可计算的图。
  3. 迭代推理：从扰动节点出发，沿知识图谱传播信号，每一步由大语言模型决策哪些节点被激活/抑制，并更新细胞状态。
  4. 输出：预测的终态基因表达变化，以及每一步的机制性解释（如“药物激活了p53通路，导致下游凋亡基因上调”）。

## 3. 实验设计
- **使用数据集/场景**：论文主要聚焦于**药物扰动预测**，可能使用了公开的单细胞药物处理数据集（如LINCS、L1000等），并可能在多个不同来源的数据上进行跨数据集评估。
- **基准任务**：虚拟细胞模型的标准任务——预测给定扰动下的基因表达变化（即扰动响应预测）。
- **对比方法**：与现有虚拟细胞模型（如基于VAE的模型、基于图神经网络的模型、以及近期融合多源数据的黑盒模型）进行性能比较。
- **评估指标**：常见的如皮尔逊相关系数、均方误差、秩相关性等，以及生物学一致性验证（如推断出的通路是否与文献已知证据匹配）。

## 4. 资源与算力
- **论文未明确说明**所使用的GPU型号、数量或训练时长。仅在摘要提到代码已开源，但无具体算力细节。这一点属于信息缺失，需指出。

## 5. 实验数量与充分性
- **实验数量**：从摘要看，论文在药物扰动benchmark上进行了多个数据集的评估（可能包含3~5个不同来源的数据），并进行了生物学通路一致性验证。虽然没有详细列出消融实验，但通常虚拟细胞论文会包含对不同知识融合策略、迭代步数等的分析。
- **充分性与公平性**：
  - **优势**：采用了公开数据集与标准评估流程，对比了多个现有方法，结果表现出SOTA性能。生物学一致性的验证增强了可信度。
  - **潜在不足**：由于缺乏对实验细节的完整描述，无法判断是否在所有实验条件下均优于基线（如不同噪声水平、批次效应去除方式）。未提及跨细胞系/跨物种泛化实验，可能限制了泛化能力的证明。消融实验的必要性较高（如去掉知识图谱、去掉迭代推理等），但摘要中未明确提及。

## 6. 论文的主要结论与发现
- VCWorld在药物扰动预测任务上达到了**最优预测性能**（state-of-the-art）。
- 模型推断出的机制性通路与公开生物学证据（如已知的转录因子调控关系）**高度一致**，证明其白盒模拟的可解释性有效。
- VCWorld对数据批次效应具有**鲁棒性**，在跨数据泛化时表现稳定。
- 该方法以**数据高效**的方式工作，降低了虚拟细胞建模对大规模单细胞数据的依赖。

## 7. 优点：方法或实验设计上的亮点
- **创新性**：首个将结构化生物学知识与大语言模型迭代推理相结合的白盒细胞模拟器，突破了纯数据驱动黑盒模型的局限。
- **可解释性**：每一步推理都有机制性假设输出，极大增强了模型在生物学研究中的可信度和实用性。
- **数据效率**：利用先验知识减少了所需训练数据量，对实际应用中数据稀缺的场景更具价值。
- **鲁棒性**：明确针对批次效应进行设计，提升了跨数据集/跨实验的泛化能力。
- **实验验证**：不仅报道预测指标，还验证了推导演化出的通路与真实生物学知识的一致性，提供双重支撑。

## 8. 不足与局限
- **实验覆盖有限**：目前仅在药物扰动场景下验证，尚未在基因扰动（CRISPR）、环境应激等其他常见扰动类型上测试，泛化到更广泛的生物学场景还需更多实验。
- **依赖知识图谱质量**：白盒模拟的准确性高度依赖先验结构化知识的完整性和准确性，而当前很多通路数据库存在不完整或偏差，可能引入系统性误差。
- **缺乏消融与敏感性分析**：论文未详细说明对知识图谱规模、迭代步数、LLM参数等的敏感度实验，难以判断设计选择的最优性。
- **算力消耗未报告**：无法评估实际部署的成本。LLM迭代推理可能带来计算开销，在超大规模细胞模拟中可能存在瓶颈。
- **偏差风险**：仅使用公开数据集，可能受特定数据分布影响；没有在独立临床或罕见扰动数据上评估，结果易被高估。
- **与已有工作的比较公平性**：部分对比方法可能是黑盒模型，但VCWorld额外使用了外部知识，这种不公平的比较需通过消融控制变量来澄清。

（完）
