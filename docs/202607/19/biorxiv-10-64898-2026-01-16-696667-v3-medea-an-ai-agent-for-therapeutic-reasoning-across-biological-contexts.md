---
title: "Medea: An AI agent for therapeutic reasoning across biological contexts"
title_zh: Medea：一个跨生物背景的治疗推理AI智能体
authors: "Sui, P., Li, M., Munson, B. P., Gao, S., Shen, W., Giunchiglia, V., Shen, A., Huang, Y., Kong, Z., Licon, K., Ideker, T., Zitnik, M."
date: 2026-07-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.01.16.696667v3.full.pdf"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 跨上下文的治疗推理AI代理，明确处理扰动效应
tldr: "治疗假设的跨疾病转移依赖生物背景，现有AI代理难以保持上下文并验证中间步骤。本文提出Medea，一个通过强制验证进行多步分析的治疗推理AI代理。在5,673个开放分析及酵母238,046基因对合成致死预测中，Medea优于多种模型，性能反映生物学相关性而非数据泄露。结果表明可验证AI代理能有效跨生物背景进行治疗分析。"
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-16-696667-v3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1455, \"height\": 1775, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-16-696667-v3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1395, \"height\": 1383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-16-696667-v3/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1690, \"height\": 1452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-16-696667-v3/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1633, \"height\": 1776, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-16-696667-v3/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1559, \"height\": 1930, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-16-696667-v3/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1673, \"height\": 1366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-16-696667-v3/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1686, \"height\": 879, \"label\": \"Figure\"}]"
motivation: 现有AI代理在治疗推理中未能保持生物背景、验证计算步骤或协调冲突证据。
method: Medea执行多步分析，结合生物工具、机器学习和文献检索，并在规划、执行和证据综合中强制验证。
result: "在5,673个分析及酵母238,046基因对合成致死预测中，Medea优于LLM、推理模型、生物代理和专用ML模型，性能反映生物学相关性。"
conclusion: 可验证AI代理能有效跨生物背景进行治疗推理，保持低失败率和校准弃权。
---

## 摘要
治疗假说可以在不同疾病之间转移，但其相关性取决于生物背景。相同的靶点、扰动或治疗方法可能在不同细胞类型、疾病状态、遗传背景和患者中产生不同效果。因此，治疗推理需要能够保留背景、检验证据是否支持转移、并识别背景特异性效应限制其转移的方法。尽管AI智能体可以执行治疗分析，但现有系统通常难以在长工作流中保留生物背景、验证中间计算步骤，或调和数据集和文献中的冲突证据。在此，我们提出Medea，一个跨生物背景的治疗推理AI智能体。Medea使用生物工具、机器学习模型和文献检索执行多步骤分析，同时在规划、执行和证据综合阶段强制执行验证。我们在三个领域的5673个开放式分析中评估Medea：五种疾病和29种细胞类型中的细胞类型特异性治疗靶点提名、7种癌细胞系中的合成致死预测，以及基于多模态患者特征的免疫治疗反应预测。利用一项先前未发表的、在两种DNA损伤处理下进行的表位微型阵列谱分析筛选，我们在酵母中238,046个基因对中评估Medea预测合成致死的能力。Medea准确预测了这些实验测量的合成致死相互作用，表明其性能反映的是生物相关性而非基准数据集的信息泄露。在这些评估中，Medea在保持低失败率和校准性弃权的同时，优于大型语言模型、推理模型、生物医学智能体和专门的机器学习模型。这些结果表明，可验证的AI智能体能够在不同生物背景下执行治疗分析。

## Abstract
Therapeutic hypotheses can transfer across diseases but their relevance depends on biological context. The same target, perturbation, or treatment can produce different effects across cell types, disease states, genetic backgrounds, and patients. Therapeutic reasoning therefore requires methods that preserve context, test when evidence supports transfer, and identify where context-specific effects limit it. Although AI agents can perform therapeutic analyses, existing systems often fail to preserve biological context over long workflows, verify intermediate computational steps, or reconcile conflicting evidence across datasets and literature. Here, we present Medea, an AI agent for therapeutic reasoning across biological contexts. Medea executes multi-step analyses using biological tools, machine learning models, and literature retrieval while enforcing verification during planning, execution, and evidence synthesis. We evaluate Medea across 5,673 open-ended analyses in three domains: cell type specific therapeutic target nomination in five diseases and 29 cell types, synthetic lethality prediction in 7 cancer cell lines, and immunotherapy response prediction from multimodal patient profiles. Using a previously unpublished epistatic miniarray profiling screen performed under two DNA-damaging treatments, we evaluate Medea on predicting synthetic lethality among 238,046 gene-gene pairs in yeast. Medea predicts these experimentally measured synthetic lethal interactions, indicating that its performance reflects biological relevance rather than information leakage from benchmark datasets. Across these evaluations, Medea improves performance over large language models, reasoning models, biomedical agents, and specialized machine learning models while maintaining low failure rates and calibrated abstention. These results show that verifiable AI agents can perform therapeutic analyses across biological contexts.

---

## 论文详细总结（自动生成）

# 论文详细总结：Medea——一个跨生物背景的治疗推理AI智能体

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：治疗假说（如靶点、扰动、治疗方法）在不同疾病或生物背景（细胞类型、疾病状态、遗传背景、患者）间的转移效果并非普适，而是强烈依赖于生物上下文。现有AI智能体在长工作流中难以保持上下文、验证中间计算步骤，并调和不同数据集和文献中的冲突证据。
- **研究动机**：开发一种能够保留生物背景、检验证据支持转移性、并识别上下文特异性效应限制的AI方法，以提升治疗推理的准确性和可解释性。
- **整体含义**：本文提出了Medea，一个通过强制验证进行多步分析的治疗推理AI智能体，旨在跨生物背景进行可靠的治疗分析，从而支持精准医学中的假设生成和决策。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将推理过程分解为规划（Planning）、执行（Execution）和证据综合（Evidence Synthesis）三个阶段，并在每个阶段强制进行验证（Verification），确保推理步骤的生物学合理性和计算正确性。
- **关键技术细节**：
  - Medea集成生物工具（如通路分析、基因网络）、机器学习模型（如预测模型）和文献检索（如自动查询PubMed）。
  - 在规划阶段：自动分解用户问题为可执行的子步骤，并验证子步骤的依赖关系和可行性。
  - 在执行阶段：调用外部工具或模型计算结果，并对中间输出进行校验（如检查数据格式、范围、一致性）。
  - 在证据综合阶段：整合来自不同来源的证据，识别冲突并尝试解决，若无法解决则选择弃权（calibrated abstention）。
- **算法流程**（文字说明）：
  1. 接收用户开放式治疗分析问题（如“在某种细胞类型中提名靶点”）。
  2. 智能体规划：生成多步执行计划，包含工具调用、数据查询、模型推理等。
  3. 验证计划：检查每个步骤的输入输出是否合理，若不合理则修订计划。
  4. 执行计划：依次运行工具/模型，每一步后验证结果（如数值范围、统计显著性）。
  5. 综合结果：对比多个证据源，利用置信度评分决定采纳或弃权。
  6. 输出最终结论及支持证据链。

## 3. 实验设计：数据集、场景与对比方法

- **数据集与场景**（共5,673个开放式分析）：
  - **场景1**：细胞类型特异性治疗靶点提名 – 5种疾病 × 29种细胞类型。
  - **场景2**：合成致死预测 – 7种癌细胞系。
  - **场景3**：免疫治疗反应预测 – 基于多模态患者特征。
  - **额外验证**：使用此前未发表的酵母表位微型阵列谱分析（epistatic miniarray profiling）数据，在两种DNA损伤处理下评估238,046个基因对的合成致死预测。
- **基准（Benchmark）**：以上述实验测量结果为金标准。
- **对比方法**：
  - 大型语言模型（如GPT-4等基础LLM）。
  - 推理模型（如Chain-of-Thought增强的LLM）。
  - 生物医学智能体（如BioAgent等）。
  - 专用机器学习模型（如合成致死预测专用ML模型）。
- **评估指标**：预测准确性、失败率（failure rate）、弃权校准度（calibrated abstention）。

## 4. 资源与算力

- **文中未明确说明**：论文未提及训练或推理所使用的GPU型号、数量、训练时长等具体算力信息。可能由于是预印本且侧重方法论，未详细报告计算资源消耗。

## 5. 实验数量与充分性

- **实验数量**：主实验涵盖5,673个开放式分析（三个场景），加上酵母238,046个基因对的合成致死预测。属于大规模评估。
- **充分性**：
  - 覆盖多种治疗推理任务（靶点提名、合成致死、免疫治疗反应），具有多样性。
  - 使用了独立新收集的实验数据（酵母筛选），避免基准数据集泄露风险。
  - 对比了多种主流AI方法（LLM、推理模型、生物代理、专用ML），对照设置较为全面。
- **客观公平性**：作者声称Medea的性能提升反映了生物学相关性而非数据泄露，且通过独立实验数据验证。但论文未报告多次重复实验的统计显著性检验，也未讨论超参数调优对结果的影响，因此公平性评估需更多细节。

## 6. 论文的主要结论与发现

- Medea在所有评估场景中优于对比模型，包括LLM、推理模型、生物医学智能体和专用机器学习模型。
- Medea在保持低失败率的同时，具备校准的弃权能力（即当证据不足时合理放弃回答）。
- 在酵母基因对合成致死预测中，Medea的预测与实验测量一致，表明其性能源于真实的生物学相关性，而非基准数据集的信息泄露。
- 结论：可验证的AI智能体能够有效跨生物背景进行治疗推理，为精准医学中的假设生成和决策提供可靠支持。

## 7. 优点：方法或实验设计上的亮点

- **方法亮点**：
  - 强制验证机制（Verification）嵌入推理全流程，提升了结果可解释性和可靠性。
  - 能够整合多源工具、模型和文献，具备跨背景推理能力。
  - 引入校准弃权，避免在证据不足时给出误导性结论。
- **实验设计亮点**：
  - 使用未公开的新实验数据（酵母筛选）验证，避免基准泄漏。
  - 评估涵盖多种任务和大量案例（5,673个分析），统计量大。
  - 对比方法全面，涵盖从纯LLM到专用模型的基线。

## 8. 不足与局限

- **实验覆盖**：主要聚焦于靶点提名、合成致死和免疫治疗反应，未涉及其他治疗推理任务（如药物重定位、剂量优化等），通用性有待扩展。
- **偏差风险**：验证机制可能依赖于预先定义的工具和知识库，若工具或数据库本身有偏差，Medea可能无法完全避免。未讨论对稀有疾病或低资源场景的适应性。
- **应用限制**：
  - 计算开销：多步验证和工具调用可能增加延迟，不适合实时决策场景。
  - 依赖外部工具和API的可用性及稳定性。
  - 未明确探讨与人类专家的协作模式，实际应用中可能需要人类在环。
- **资源与复现**：未提供算力需求和开源代码/模型，复现性和可扩展性受限。

（完）
