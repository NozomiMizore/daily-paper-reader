---
title: "Title: HypoGeneAgent: Hypothesis Language Agent for Gene-set Cluster Resolution Selection Using Perturb-seq Datasets"
title_zh: HypoGeneAgent：利用Perturb-seq数据集的基因集聚类分辨率选择的假设语言智能体
authors: "Ying Yuan, Xing-Yue Monica Ge, Aaron Archer Waterman, Tommaso Biancalani, David Richmond, Yogesh Pandit, Avtar Singh, Russell Littman, Jin Liu, Jan-Christian Huetter, Vladimir Ermakov"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=xDO0239YOm"
tags: ["query:virtual-cell"]
score: 5.0
evidence: 使用Perturb-seq数据进行基因集分析，与单细胞扰动相关
tldr: 针对单细胞Perturb-seq聚类标注主观性强的问题，提出HypoGeneAgent框架，利用大语言模型作为基因集分析师，生成基于Gene-Ontology的假设并校准置信度，将聚类注释转化为可定量优化的任务，提升了分析效率和客观性。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 单细胞Perturb-seq的聚类分辨率和功能注释依赖启发式方法。
method: 利用大语言模型分析基因程序或扰动模块内容，生成排序的GO假设。
result: 实现了定量优化的聚类注释。
conclusion: LLM可有效辅助单细胞扰动数据分析。
---

## Abstract
Large-scale single-cell and Perturb-seq investigations routinely involve clustering cells and subsequently annotating each cluster with Gene-Ontology (GO) terms to elucidate the underlying biological programs. However, both stages, resolution selection and functional annotation, are inherently subjective, relying on heuristics and expert curation. We present HYPOGENEAGENT, a large language model (LLM)-driven framework, transforming cluster annotation into a quantitatively optimizable task. Initially, an LLM functioning as a gene-set analyst analyzes the content of each gene program or perturbation module and generates a ranked list of GO-based hypotheses, accompanied by calibrated confidence scores. Subsequently, we embed every predicted description with a sentence-embedding model, compute pair-wise cosine similarities, and let the agent referee panel score (i) the internal consistency of the predictions, high average similarity within the same cluster, termed intra-cluster agreement (ii) their external distinctiveness, low similarity between clusters, termed inter-cluster separation. These two quantities are combined to produce an agent-derived resolution score, which is maximized when clusters exhibit simultaneous coherence and mutual exclusivity. When applied to a public K562 CRISPRi Perturb-seq dataset as a preliminary test, our Resolution Score selects clustering granularities that exhibit alignment with known pathway compared to classical metrics such silhouette score, modularity score for gene functional enrichment summary. These findings establish LLM agents as objective adjudicators of cluster resolution and functional annotation, thereby paving the way for fully automated, context-aware interpretation pipelines in single-cell multi-omics studies.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机与背景）

- **研究动机**：大规模单细胞及Perturb-seq数据分析中，细胞聚类后的**分辨率选择**（即确定聚类数量）和**功能注释**（为每个簇分配Gene-Ontology术语）两个关键步骤目前高度依赖**启发式方法和专家手动标注**，导致结果主观性强、可重复性差。
- **整体含义**：现有方法（如轮廓系数、模块度分数）无法自动捕捉生物学语义的一致性，亟需一种**客观、可量化**的聚类评估与注释方法，以推动单细胞多组学分析管线的全自动化。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：利用大语言模型（LLM）作为基因集分析师，将聚类注释转化为**可定量优化的任务**，通过生成基于GO的假设并计算置信度得分，进而构建一个**智能体仲裁得分**（Agent Referee Panel Score）来评估聚类质量。
- **关键技术细节**：
  1. **GO假设生成与置信度校准**：LLM分析每个基因程序或扰动模块的内容，输出**排序的GO假设列表**，并附带校准后的置信度分数。
  2. **嵌入与相似度计算**：使用句子嵌入模型（如Sentence-BERT）将每个假设的文本描述映射为向量，计算**簇内余弦相似度**（高相似度代表内部一致性）和**簇间余弦相似度**（低相似度代表外部分离度）。
  3. **智能体仲裁得分**：将簇内一致性（Intra-cluster Agreement）和簇间分离度（Inter-cluster Separation）组合为一个**分辨率得分**（Resolution Score），当簇既彼此一致又相互排斥时得分最大。
- **算法流程**（文字说明）：
  1. 输入：聚类后的基因程序/扰动模块集合。
  2. LLM为每个簇生成候选GO假设列表，并输出置信度。
  3. 对所有假设进行句子嵌入，计算两两余弦相似度。
  4. 计算每个簇的平均内部相似度（Intra）和不同簇间的平均相似度（Inter）。
  5. 通过公式（文中未显式给出）组合Intra与Inter得到Resolution Score。
  6. 选择使Resolution Score最大的聚类粒度作为最优分辨率。

## 3. 实验设计

- **数据集**：仅使用了一个公开的**K562 CRISPRi Perturb-seq数据集**作为初步测试（preliminary test）。
- **基准（Benchmark）**：与经典指标**轮廓系数（Silhouette Score）**、**模块度分数（Modularity Score）** 进行对比，评估所选聚类粒度与已知通路的一致性。
- **对比方法**：未明确列出其他LLM基线或传统方法，仅与传统启发式指标比较。
- **实验场景**：单一数据集、单一细胞系（K562）、单一扰动类型（CRISPRi），未涉及多数据集或跨物种验证。

## 4. 资源与算力

- **未明确说明**：论文摘要中未提及使用的GPU型号、数量、训练时长、显存消耗等任何算力信息。由于HypoGeneAgent主要依赖LLM推理和轻量级嵌入计算，推测算力需求较低，但无具体数据支持。

## 5. 实验数量与充分性

- **实验数量**：仅进行了**一组初步实验**（单一数据集、单一对比设置），未展示多数据集、多分辨率参数扫描或消融实验。
- **充分性评价**：
  - **不足**：实验规模过小，缺乏统计显著性验证；未展示不同LLM（如GPT-4、Llama等）的鲁棒性对比；未进行消融分析（如去除置信度校准的效果）。
  - **客观性**：对比了经典指标，但未说明P值或置信区间，且结果“exhibit alignment”表述较模糊，缺乏定量评估（如富集分析的p值）。
  - **公平性**：仅与两个传统指标比较，未与基于LLM的其他聚类评价方法（如直接询问LLM）对比。

## 6. 主要结论与发现

- **结论**：HypoGeneAgent框架能够选出与已知通路对齐的聚类粒度，优于轮廓系数和模块度分数。
- **发现**：LLM智能体可作为聚类分辨率和功能注释的**客观裁决者**，为全自动、上下文感知的单细胞多组学分析管线奠定基础。

## 7. 优点

- **创新性**：首次将LLM引入聚类分辨率选择与功能注释的联合优化，将主观任务转化为可定量优化的目标。
- **可解释性**：生成的GO假设列表直接提供生物学含义，而非仅依赖数值指标。
- **普适潜力**：方法不限于特定细胞类型或扰动方式，理论上可扩展到其他单细胞多组学数据（如scRNA-seq、scATAC-seq）。

## 8. 不足与局限

- **实验覆盖不足**：仅在一个数据集上测试，未在多种细胞系、多种扰动类型（如CRISPRa、shRNA）、不同测序平台或组织上验证，泛化性存疑。
- **偏差风险**：LLM生成的GO假设可能存在知识偏差或幻觉，置信度校准的可靠性未深入分析；句子嵌入模型的选择（未指定）可能影响余弦相似度结果。
- **应用限制**：
  - 依赖LLM的推理质量，对于罕见或特异性基因程序可能生成不准确的假设。
  - 计算Resolution Score时需要遍历所有候选聚类粒度，当数据规模极大时，多次调用LLM可能导致成本上升（但未评估）。
  - 未与人工专家注释进行系统性对比（如计算与金标准注释的一致性），无法确认绝对优劣。

（完）
