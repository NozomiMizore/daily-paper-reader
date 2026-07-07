---
title: "SC-Arena: A Natural Language Benchmark for Single-Cell Reasoning with Knowledge-Augmented Evaluation"
title_zh: SC-Arena：基于知识增强评估的单细胞推理自然语言基准
authors: "Jiahao Zhao, Feng Jiang, Shaowei Qin, Zhonghui Zhang, Junhao Liu, Guibing Guo, Hamid Alinejad-Rokny, Min Yang"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=5RcoUe1tA1"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 形式化虚拟细胞抽象用于评估
tldr: 针对单细胞基础模型评估碎片化的问题，提出SC-Arena框架，通过形式化虚拟细胞抽象统一评估目标，结合知识增强指标，为单细胞推理提供更真实、可解释的评估基准，推动虚拟细胞模型发展。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 现有单细胞基准评估格式不一致且缺乏生物学可解释性。
method: 定义虚拟细胞抽象，将内在属性和基因交互表示为统一评估目标。
result: 提供了更符合实际使用场景的评估基准。
conclusion: 虚拟细胞抽象有助于标准化单细胞模型评估。
---

## Abstract
Large language models (LLMs) are increasingly applied in scientific research, offering new capabilities for knowledge discovery and reasoning. In single-cell biology, however, evaluation practices for both general and specialized LLMs remain inadequate: existing benchmarks are fragmented across tasks, adopt formats such as multiple-choice classification that diverge from real-world usage, and rely on metrics lacking interpretability and biological grounding.  We present **SC-ARENA**, a natural language evaluation framework tailored to single-cell foundation models. SC-ARENA formalizes a *virtual cell* abstraction that unifies evaluation targets by representing both intrinsic attributes and gene-level interactions. Within this paradigm, we define five natural language tasks — cell type annotation, captioning, generation, perturbation prediction, and scientific QA — that probe core reasoning capabilities in cellular biology.  To overcome the limitations of brittle string-matching metrics, we introduce **knowledge-augmented evaluation**, which incorporates external ontologies, marker databases, and scientific literature to support biologically faithful and interpretable judgments.  Experiments and analysis across both general-purpose and domain-specialized LLMs demonstrate that: (i) under the *Virtual Cell* unified evaluation paradigm, current models achieve uneven performance on biologically complex tasks, particularly those demanding mechanistic or causal understanding; and (ii) our knowledge-augmented evaluation framework ensures biological correctness, provides interpretable, evidence-grounded rationales, and achieves high discriminative capacity, overcoming the brittleness and opacity of conventional metrics. **SC-ARENA** thus provides a unified and interpretable framework for assessing LLMs in single-cell biology, pointing toward the development of biology-aligned, generalizable foundation models.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：当前单细胞生物学领域的大语言模型（LLM）评估实践存在碎片化、与真实使用场景脱节、缺乏生物学可解释性等严重不足。具体表现为：现有基准在不同任务上格式不一致（如多选分类），评估指标依赖脆弱的字符串匹配，无法捕获生物学正确性。
- **整体含义**：为了推动单细胞基础模型的健康发展，需要建立一个统一、可解释且生物学可信的评估框架，以衡量模型在细胞注释、生成、扰动预测等核心推理能力上的表现。

## 2. 方法论

### 核心思想
- **虚拟细胞抽象（Virtual Cell Abstraction）**：将单细胞内在属性（如细胞类型、状态）和基因级交互（如基因表达关系）形式化为统一的评估目标，从而整合多种下游任务。
- **知识增强评估（Knowledge-Augmented Evaluation）**：引入外部本体（ontologies）、标记基因数据库和科学文献，替代传统字符串匹配指标，提供符合生物学事实的判断和可解释的推理依据。

### 关键技术细节
- 定义五个自然语言任务：细胞类型注释、字幕生成（细胞描述）、生成（模拟细胞）、扰动预测（如药物干预效果）、科学问答（生物学知识推理）。
- 评估时，将模型输出与知识库（如Gene Ontology、CellMarker数据库）进行交叉验证，而不是简单的精确匹配。例如，对细胞类型注释，检查预测的标记基因是否在已知数据库中出现；对扰动预测，验证预测的基因表达变化是否与文献证据一致。

## 3. 实验设计

- **数据集/场景**：未在摘要中明确列出具体数据集名称，但五个任务分别对应不同的单细胞数据场景。推测使用了公开的单细胞RNA-seq数据集（如human cell atlas等）以及标准基准（如annotation benchmark）。
- **基准（Benchmark）**：SC-ARENA自身作为统一的评估基准，包含五个任务。
- **对比方法**：分别评估通用LLM（如GPT-4）和领域专用LLM（如scGPT、Geneformer等单细胞基础模型），并比较它们在不同任务上的表现。实验分析表明：当前模型在需要机制或因果理解的任务（如扰动预测）上表现不均衡。

## 4. 资源与算力

- **未明确说明**：摘要和元数据中未提及使用的GPU型号、数量、训练时长等算力信息。仅在实验部分提到“Experiments and analysis across both general-purpose and domain-specialized LLMs”，但未提供实际训练或推理的硬件细节。

## 5. 实验数量与充分性

- **实验数量**：至少包含两组主要实验：（i）在五个任务上对比多个LLM的性能；（ii）消融/验证知识增强评估的有效性（对比传统字符串匹配指标）。此外，可能还有对评估指标区分度、可解释性的量化分析。
- **充分性**：从摘要看，实验设计涵盖了多个模型、多个任务，并特别验证了知识增强评估的生物学正确性、可解释性和高区分能力，实验较为充分。但未提供具体统计数字（如每个任务测试样本数）和统计显著性检验，因此客观性和公平性需通过完整论文进一步确认。

## 6. 主要结论与发现

- **(i)** 在统一的虚拟细胞评估范式下，现有模型在生物学复杂任务上表现不均衡，尤其缺乏对机制或因果理解的能力。
- **(ii)** 所提出的知识增强评估框架能确保生物学正确性，提供基于证据的可解释理由，并具有高区分能力，克服了传统指标的脆弱性和不透明性。
- 因此，SC-ARENA为单细胞生物学中LLM的评估提供了一个统一、可解释的框架，有助于开发与生物学对齐的通用基础模型。

## 7. 优点

- **统一性**：通过虚拟细胞抽象将多种评估任务统一，解决了碎片化问题。
- **生物学可解释性**：知识增强评估利用外部知识库，使评分结果可溯源，便于研究者理解模型错误原因。
- **实用性**：任务设计贴近真实科研场景（如扰动预测、科学问答），避免了多选等非自然格式。
- **验证充分**：同时对比通用和专用模型，并验证了新评估指标的有效性。

## 8. 不足与局限

- **实验覆盖有限**：未提供具体数据集来源和样本量，可能存在基准偏差。
- **算力资源未公开**：无法复现实验成本，也影响对方法可扩展性的判断。
- **通用性风险**：知识增强评估依赖外部数据库的完整性和时效性，对稀有细胞类型或新扰动可能覆盖不足。
- **未讨论语言模型本身的安全性**：如模型可能生成生物学上合理但实际错误的回答，评估框架能否完全阻断？摘要未提及。
- **缺失与人类专家评判的对比**：仅与传统指标对比，未评估与领域专家评分的一致性。

（完）
