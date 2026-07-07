---
title: "CellForge: Agentic Design of Virtual Cell Models"
title_zh: CellForge：虚拟细胞模型的智能体设计
authors: "Xiangru Tang, Zhuoyun Yu, Jiapeng Chen, Yan Cui, Daniel Shao, Weixu Wang, Fang Wu, Yuchen Zhuang, Wenqi Shi, Zhi Huang, Arman Cohan, Xihong Lin, Fabian J Theis, Smita Krishnaswamy, Mark Gerstein"
date: 2025-09-17
pdf: "https://openreview.net/pdf?id=6v7GkwSwtp"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 虚拟细胞模型的智能体设计
tldr: 针对虚拟细胞建模中生物系统复杂性、数据模态异质性和多学科专业知识需求等挑战，本文提出CellForge，一个基于多智能体框架的系统，能够将原始单细胞多组学数据和任务描述自动转化为优化的虚拟细胞计算模型。该方法直接支持扰动响应预测等任务，为虚拟细胞建模提供了自动化工具。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 虚拟细胞建模面临生物系统复杂、数据模态异质和领域知识需求高的挑战，缺乏自动化构建方法。
method: 提出CellForge多智能体系统，输入原始单细胞多组学数据和任务描述，自动生成优化的虚拟细胞模型。
result: CellForge能够高效地将数据和任务转化为虚拟细胞模型，适用于扰动响应预测等场景。
conclusion: CellForge为虚拟细胞模型的自动化构建提供了有效框架，有望推动虚拟细胞研究。
---

## Abstract
Virtual cell modeling represents an emerging frontier at the intersection of artificial intelligence and biology, aiming to predict quantities such as responses to diverse perturbations quantitatively. However, autonomously building computational models for virtual cells is challenging due to the complexity of biological systems, the heterogeneity of data modalities, and the need for domain-specific expertise across multiple disciplines. Here, we introduce CELLFORGE, an agentic system that leverages a multi-agent framework that transforms presented biological datasets and research objectives directly into optimized computational models for virtual cells. More specifically, given only raw single-cell multi-omics data and task descriptions as input (e.g., for control and perturbed conditions and a directive to build a model of a new perturbation), CELLFORGE outputs both an optimized model architecture and executable code for training virtual cell models and inference. The framework integrates three core modules: Task Analysis for presented dataset characterization and relevant literature retrieval, Method Design, where specialized agents collaboratively develop optimized modeling strategies, and Experiment Execution for automated generation of code. The agents in the Design module are separated into experts with differing perspectives and a central moderator, and have to collaboratively exchange solutions until they achieve a reasonable consensus. We demonstrate CELLFORGE’s capabilities in single-cell perturbation prediction, using six diverse datasets that encompass gene knockouts, drug treatments, and cytokine stimulations across multiple modalities. CELLFORGE consistently outperforms task-specific state-of-the-art methods, achieving up to 40% reduction in prediction error and 20% improvement in correlation metrics. Overall, CELLFORGE demonstrates how iterative interaction between LLM agents with differing perspectives provides better solutions than directly addressing a modeling challenge

---

## 论文详细总结（自动生成）

# CellForge：虚拟细胞模型的智能体设计——详细中文总结

## 1. 论文的核心问题与整体含义
- **研究动机**：虚拟细胞建模旨在通过计算模型预测细胞对多种扰动的响应，但面临三大挑战：生物系统的高度复杂性、单细胞多组学数据模态的异质性、以及需要跨学科领域专业知识。目前缺乏能够自动将原始数据和任务描述转化为优化计算模型的系统性方法。
- **整体含义**：本文提出 CellForge，一个基于多智能体框架的自动化系统，能够直接从原始单细胞多组学数据和任务描述生成优化的虚拟细胞模型架构及可执行代码，显著降低人工建模门槛，推动虚拟细胞研究从手工试错转向自动化智能化。

## 2. 论文提出的方法论
- **核心思想**：利用大型语言模型（LLM）驱动多个专业智能体协同工作，通过迭代交流达成共识，从而自动完成数据集分析、方法设计与实验执行。
- **关键技术细节**：
  - **三大核心模块**：
    1. **Task Analysis（任务分析）**：对输入数据集进行表征，并检索相关文献。
    2. **Method Design（方法设计）**：包含多个不同视角的专家智能体和一个中央协调器（central moderator）。各专家智能体分别提出建模策略，通过反复交流、交换方案直至达成合理共识，最终形成优化的建模方法。
    3. **Experiment Execution（实验执行）**：自动生成可训练和推理的代码。
  - **输入**：原始单细胞多组学数据 + 任务描述（如控制条件与扰动条件，以及构建新扰动模型的要求）。
  - **输出**：优化后的模型架构 + 可执行代码。
- **算法流程**（文字说明）：输入数据与任务 → 任务分析模块解析并检索文献 → 方法设计模块中各专家智能体独立提出策略 → 中央协调器组织迭代讨论与方案融合 → 达成共识后输出建模方案 → 实验执行模块自动生成代码并训练/推理。

## 3. 实验设计
- **数据集与场景**：使用六个不同数据集，涵盖**基因敲除、药物治疗、细胞因子刺激**等扰动类型，且涉及多种单细胞模态。
- **基准测试**：对比了任务特定的**最先进方法（SOTA）**。
- **对比方法**：未在摘要中列出具体方法名称，但明确表示与各扰动预测任务中已有的最优方法进行比较。
- **评估指标**：预测误差（降低达40%）与相关性指标（提升达20%）。

## 4. 资源与算力
- **文中说明**：摘要及元数据中**未明确提及**使用的GPU型号、数量或训练时长等算力信息。
- **结论**：本文未公开具体的计算资源消耗，可能在正文或附录中会有说明，但依据提供的文本无法总结。

## 5. 实验数量与充分性
- **实验数量**：使用了**六个不同数据集**，覆盖三类典型扰动（基因敲除、药物、细胞因子），实验数量较为丰富。
- **充分性评估**：数据集多样、扰动类型代表性较强，且与多个SOTA方法对比，结果显示出明显优势（误差降低40%、相关性提升20%），说明实验设计较为充分。但摘要未提及消融实验（如对智能体数量、迭代次数的分析），可能削弱对方法各组件贡献的验证。

## 6. 论文的主要结论与发现
- CellForge能够将原始单细胞多组学数据和任务描述自动转化为优化的虚拟细胞模型，在单细胞扰动预测任务中**一致优于**任务特定的SOTA方法，预测误差最高降低40%，相关性指标提升20%。
- 证明了**LLM多智能体迭代交互**（不同视角的专家通过讨论达成共识）比直接建模挑战更能产生更好的解决方案。

## 7. 优点
- **自动化程度高**：直接从原始数据到可执行代码，无需人工干预。
- **模块化设计**：任务分析、方法设计、实验执行解耦，具有良好的可扩展性。
- **多智能体协作机制**：通过专家智能体的不同视角和迭代协商，提高方案质量，避免单一模型偏见。
- **性能显著**：在多个数据集上大幅超越SOTA，证明了方法的有效性。
- **通用性**：适用于基因敲除、药物、细胞因子等多种扰动类型，跨模态适用。

## 8. 不足与局限
- **算力与效率未透露**：缺少训练时间、GPU需求等关键资源信息，难以评估实际应用成本。
- **消融实验缺失**：未明确报告对智能体数量、迭代轮次等设计选择的消融研究，无法确定各组件贡献。
- **实验覆盖范围**：虽然数据集多样，但可能仍局限于单细胞类扰动预测，未涉及其他虚拟细胞建模任务（如基因调控、细胞状态转换等）。
- **领域知识依赖**：虽然方法自动检索文献，但文献检索的质量和时效性可能影响结果，存在偏差风险。
- **可重复性**：代码和模型权重是否开源未提及，可能影响他人复现。

（完）
