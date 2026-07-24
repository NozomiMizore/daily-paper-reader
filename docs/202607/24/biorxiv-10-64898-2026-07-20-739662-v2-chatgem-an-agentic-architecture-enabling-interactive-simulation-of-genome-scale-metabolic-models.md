---
title: "ChatGEM: An Agentic Architecture Enabling Interactive Simulation of Genome-Scale Metabolic Models"
title_zh: ChatGEM：一种支持基因组规模代谢模型交互式模拟的智能体架构
authors: "Chowdhury, N., George, A., Purohit, S., Contolesi, A., Bredeweg, E. L., Czajka, J., Stratton, K. G., Gao, Y., Stephenson, M., Elmore, J. R., Scott, A., Leach, D. T., Jerger, A., Lemmon, T., Piehowski, P., Tate, K., Fulcher, J. M., Beliaev, A., Burnum-Johnson, K., Rigor, P., Bardhan, J."
date: 2026-07-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.20.739662v2.full.pdf"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 支持交互式模拟基因组规模代谢模型作为虚拟细胞
tldr: 基因组规模代谢模型（GEM）预测能力强但需专业知识。ChatGEM基于多智能体ADEPT框架，集成COBRApy与RAG，支持自然语言交互模拟。RAG使性能评分从2.63提升至4.20，执行时间大幅降低；在酶约束GEM上准确预测琥珀酸过量生产的最佳菌株。该工具降低了建模门槛，加速科学发现。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739662-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1533, \"height\": 790, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739662-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1733, \"height\": 1237, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739662-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1723, \"height\": 1346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739662-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1725, \"height\": 1969, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-20-739662-v2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1757, \"height\": 1626, \"label\": \"Table\"}]"
motivation: 降低GEM使用门槛，让无计算背景研究者也能通过自然语言进行复杂代谢模拟。
method: 基于ADEPT多智能体框架，集成COBRApy与RAG，通过专业智能体协调代码生成与执行。
result: RAG提升性能评分从2.63到4.20，显著减少执行时间；在ecGEM上准确识别琥珀酸过量生产的最佳菌株。
conclusion: ChatGEM通过自然语言交互民主化代谢建模，加速科学发现。
---

## 摘要
基因组规模代谢模型（GEMs）是预测细胞表型和指导微生物菌株工程的有力工具，但由于需要计算专业知识，其广泛采用仍具挑战。为克服这一障碍，我们提出了ChatGEM，一个通过自然语言实现GEM交互式模拟的智能体平台。基于多智能体ADEPT框架，ChatGEM将COBRApy集成在检索增强生成（RAG）架构中，通过专门智能体协调代码生成与执行。在三个复杂度递增的任务上的基准测试表明，启用RAG的代码生成将平均总体性能评分从2.63提升至4.20，并且从常规任务到复杂任务，执行时间显著减少。使用酶约束GEM（ecGEM）对四种工程改造的恶臭假单胞菌KT2440菌株应用ChatGEM，通过琥珀酸泄漏指数——一个实验观测到的预测指标——识别出组成型菌株为琥珀酸过量生产的最佳底盘。因此，ChatGEM通过使无计算专业知识的研究人员能够通过自然语言执行基于GEM的复杂分析，从而民主化了代谢建模，进而加速科学发现。

## Abstract
Genome-scale metabolic models (GEMs) are powerful tools for predicting cellular phenotypes and guiding microbial strain engineering, yet broad adoption remains challenging due to the computational expertise required. To overcome that, we present ChatGEM, an agentic platform that enables interactive GEM simulation through natural language. Built on the multi-agent ADEPT framework, ChatGEM integrates COBRApy within a retrieval-augmented generation (RAG) architecture that coordinates code generation and execution through specialized agents. Benchmarking across three tasks of increasing complexity showed that RAG-enabled code generation improved the mean overall performance score from 2.63 to 4.20 while reducing the execution time significantly starting from routine to complex tasks. Application of ChatGEM using an enzyme-constrained GEM (ecGEM) for four engineered Pseudomonas putida KT2440 strains identified the constitutive strain as the optimal chassis for succinate overproduction using a succinate leakage index - a prediction observed experimentally. Therefore, ChatGEM democratizes metabolic modeling by enabling researchers without computational expertise to perform sophisticated GEM-based analyses through natural language, and, hence, accelerating scientific discovery.

---

## 论文详细总结（自动生成）

# 中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：基因组规模代谢模型（GEMs）是系统生物学中预测细胞表型、指导菌株工程的重要工具，但其应用广泛依赖计算专业知识（如COBRApy、Python/Matlab编程），导致多数生物学家、代谢工程师难以直接使用，形成“分析潜力与实际采用”之间的鸿沟。
- **整体含义**：为降低这一编程壁垒，论文提出ChatGEM——一个基于多智能体框架ADEPT、集成检索增强生成（RAG）和COBRApy的对话式平台，让用户通过自然语言即可完成GEM仿真、菌株设计、酶约束建模等复杂任务，从而民主化代谢建模，加速科学发现。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：构建一个LLM驱动的多智能体系统，通过自然语言输入自动生成并执行GEM相关的Python代码，实现从简单到复杂的代谢建模任务。
- **关键技术细节**：
  - 基于**ADEPT**多智能体框架：包含安全网关（Keycloak）、中央编排服务（PostgreSQL存储对话）、无状态MCP工具服务器（支持BLAST、UniProt、PubChem、HPC、沙箱代码执行等）。
  - 集成**COBRApy**、**StrainDesign**、**Gurobi**等专用工具。
  - 支持**RAG**（检索增强生成）：通过自动将52个人工精选的Python脚本（涵盖FBA到ecOptMDFPathway）摄入向量数据库（ChromaDB），在生成代码时检索相关文档。
  - 默认LLM为**o4-mini**（轻量推理模型），通过YAML配置支持多模型（OpenAI、Anthropic、Ollama等）。
  - 代码生成的**评价指标**：Coding Accuracy（1-5，生物输出正确性）、Code Completeness（1-5，结构质量、API使用、文档）；综合为**OPS = 0.7 × Accuracy + 0.3 × Completeness**。
- **算法流程**（文字说明）：
  1. 用户通过Streamlit聊天界面输入自然语言查询。
  2. ADEPT的Scientific Workflow Agent调度各智能体。
  3. 若启用RAG，检索相关示例脚本。
  4. LLM生成Python代码（调用COBRApy等库）。
  5. 代码在沙箱容器中执行（支持Gurobi求解器）。
  6. 输出结果返回给用户，并由独立LLM裁判（Claude Sonnet 4.6）评分。

## 3. 实验设计：使用了哪些数据集/场景，benchmark是什么，对比了哪些方法
- **数据集/场景**：
  - 基准测试：使用**P. putida KT2440**的GEM（iJN1463），在三个复杂度递增的任务上测试：
    1. **FBA with targeted reaction knockouts**（低复杂度）
    2. **OptKnock strain design**（高复杂度）
    3. **ecOptMDFPathway**（酶约束+热力学路径优化，更高复杂度）
  - 案例研究：四种工程菌株（wild-type KT2440、Landing Pad、Constitutive dCas12a、Inducible dCas12a），生长在葡萄糖为唯一碳源的条件下，采样12h和24h，收集蛋白质组学和琥珀酸分泌数据。
- **Benchmark**：
  - 代码质量通过OPS评分（由Claude Sonnet 4.6评估）。
  - 时间效率对比：手动编码 vs. ChatGEM编码+人工检查 vs. ChatGEM编码单独执行。
- **对比方法**：
  - 主要对比**RAG启用 vs. 无RAG**。
  - 额外比较LLM模型：**o4-mini vs. GPT-4.1**（通用前沿模型）。

## 4. 资源与算力
- 论文中**未明确说明**具体的GPU型号、数量或训练时长。
- 仅提到：
  - ADEPT部署在AWS EC2实例及内部HPC系统上。
  - 使用Gurobi作为求解器（商业许可）。
  - 默认LLM为o4-mini（成本较低），未提及训练ChatGEM模型，而是基于现有LLM进行推理。
- 因此，算力需求是推理阶段而非训练阶段，且未被量化。

## 5. 实验数量与充分性
- **基准测试实验**：3个任务 × 2种条件（RAG启用/无RAG） = 6组代码生成实验；额外加上o4-mini vs GPT-4.1的对比（3任务 × 2条件 × 2模型 = 12组），但报告的主体是6组。
- **案例研究**：构建了8个ecGEM（4菌株 × 2时间点），计算了酶分配、生长率、琥珀酸外排率、SLI等，并与实验测定的琥珀酸滴度对比。
- **充分性分析**：
  - **充分**：三个任务覆盖从简单到复杂的典型GEM应用；时间对比涵盖了手动、半自动、全自动三种模式；模型对比给出了两种主流LLM的表现；案例研究有生化实验验证。
  - **客观/公平**：代码质量通过独立LLM裁判评分（Claude Sonnet 4.6），避免作者主观偏差；时间对比中手动编码由专家完成（但未明确说明专家数量或经验水平，可能存在偏差）。
  - **局限性**：基准测试任务数量较少（3个），且仅限于P. putida模型；未在其他物种或更大规模问题上验证泛化性。

## 6. 论文的主要结论与发现
- **RAG显著提升代码质量**：无RAG时平均OPS为2.63（o4-mini），启用RAG后提升至4.20（+60%），且执行时间大幅减少（FBA任务65倍加速，OptKnock和ecOptMDFPathway从>1天降至数十秒至数分钟）。
- **RAG能弥合模型差距**：无RAG时o4-mini优于GPT-4.1（2.63 vs 2.18），但有RAG时两者均达到4.20，说明域知识支持比推理能力更重要。
- **案例研究验证实用性**：ChatGEM成功重建8个准确ecGEM，预测的生长速率与生理范围一致，蛋白质组与iBAQ相关r=0.50；识别出EDD、GLCDpp、ACONTa为主要蛋白消耗节点；通过**琥珀酸泄漏指数**（SLI）预测组成型菌株为最佳底盘，实验滴度一致。
- **结论**：ChatGEM通过自然语言交互，使无计算背景的研究者能够执行专业级GEM分析，压缩原本需要数天的工作流为一次对话。

## 7. 优点：方法或实验设计上的亮点
- **创新性**：首个提供完整GEM仿真栈（FBA、OptKnock、ecGEM重建）的对话式AI平台，涵盖从代码生成到执行解释的全流程。
- **RAG架构**：通过注入领域特定示例脚本，大幅提升代码正确性和健壮性，且能弥补不同LLM之间的能力差距。
- **多智能体与安全设计**：基于ADEPT框架，支持沙箱执行、权限管理、持久化对话、多工具集成（COBRApy、StrainDesign、Gurobi、BLAST等），兼具可扩展性和安全性。
- **实用验证**：不仅在模拟基准上测试，还用真实菌株的蛋白质组数据构建ecGEM，并与实验琥珀酸产量对比，验证了预测能力。
- **开源**：代码和模型（ecGEMs、RAG脚本）均在GitHub公开，促进复现和社区扩展。

## 8. 不足与局限
- **实验覆盖有限**：仅使用单一种类模型（P. putida KT2440）和三个特定任务；未在其他生物（如大肠杆菌、酵母）上验证泛化性，也未测试更多类型的GEM分析（如基因必需性、通量耦合等）。
- **代码评估主观性**：OPS评分由LLM作为裁判，虽然一致性好，但LLM可能对代码的生物正确性理解存在偏差，尤其对复杂域知识（如ecGEM约束）的评分可信度未与人类专家对比验证。
- **未与其他类似工具对比**：论文提到了BioAgents、CellWhisperer、D2Cell等，但未在同一任务上直接对比性能，仅讨论概念差异。
- **未报告手动编码的专家经验**：手动编码的时间来自“专家”，但未说明专家水平或代码复杂度是否可比，时间对比可能存在不公平因素。
- **案例研究依赖蛋白质组数据**：ecGEM重建需要高质量的iBAQ和kcat数据，对缺乏这些数据的组织或菌株可能不适用。
- **算力资源未明确**：无具体GPU型号、耗时等，不利于其他团队评估部署成本。
- **潜在偏差**：RAG脚本是由作者人工精选的，可能偏向于作者熟悉的库和求解方法，若社区有其他优秀库（如cameo），可能影响代码生成偏好。

（完）
