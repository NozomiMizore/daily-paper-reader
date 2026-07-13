---
title: "OCellus: A Language-Model Framework for Single-Cell, Spatial, and Perturbation Biology with Natural-Language Reasoning"
title_zh: OCellus：面向单细胞、空间和扰动生物学并具备自然语言推理能力的语言模型框架
authors: "Zhang, C., Sun, J., Xu, Z., Liao, R., Yin, A., Gao, H., Liu, E., Bao, Y., Zhao, L., Wang, G."
date: 2026-07-12
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.08.737248v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 直接涉及虚拟细胞模型和扰动响应预测
tldr: "当前细胞基础模型专用于单细胞或空间任务，缺乏统一框架，且扰动预测依赖人工知识库。OCellus基于9B参数语言模型微调，通过EvenClock将空间坐标编码为文本、基因嵌入替代GO注释、Agent自然语言接口，统一解决三类任务。在空间任务上达77-96%准确率，扰动预测Pearson 0.945，22项任务平均72.6%，超越基线57个百分点。该模型首个支持自然语言推理和解释的虚拟细胞框架，将开源。"
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737248-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1629, \"height\": 2320, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737248-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 519, \"height\": 521, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737248-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1524, \"height\": 1063, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737248-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1432, \"height\": 1780, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737248-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1527, \"height\": 1394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737248-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1519, \"height\": 1309, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737248-v1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1551, \"height\": 854, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737248-v1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1513, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737248-v1/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1507, \"height\": 1572, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-08-737248-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1634, \"height\": 112, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-08-737248-v1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1712, \"height\": 1888, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-08-737248-v1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1714, \"height\": 1344, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-08-737248-v1/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1713, \"height\": 905, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-08-737248-v1/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1713, \"height\": 1083, \"label\": \"Table\"}]"
motivation: 现有模型无法统一处理单细胞、空间和扰动任务，且扰动预测依赖人工知识库，泛化能力差。
method: 基于Qwen3.5-9B微调，用EvenClock文本化空间坐标、基因语言模型嵌入替代GO注释、Agent Planner-Router-Verifier接口。
result: "空间邻域准确率77%，细胞通讯96%，扰动Pearson 0.945，线性探针95.1%，22项任务平均72.6%。"
conclusion: OCellus首个统一单细胞、空间与扰动推理的语言模型，具备自然语言解释能力，推动虚拟细胞建模。
---

## 摘要
细胞行为的计算建模——虚拟细胞——已成为人工智能与生物学交叉领域公认的重大挑战，然而现有基础模型仍存在局限性：单细胞模型仅处理解离的转录组，空间模型需要专用的空间感知架构，扰动预测则依赖人工整理的知识库，这限制了其泛化能力。本文提出OCellus，一个基于共享主干通过三项协同技术贡献同时解决上述三个局限的九十亿参数语言模型（Qwen3.5-9B），在二十二项生物学任务上进行了微调。第一，EvenClock将二维空间坐标编码为十八个钟面区域的文本，使得普通语言模型无需架构修改即可进行空间推理；在十项空间转录组学任务中，OCellus达到了77%的空间邻域准确率、96%的空间细胞通讯准确率以及空间解卷积0.70的比例余弦相似度，且未使用任何空间感知架构组件。第二，基于每个基因的语言模型嵌入替代了GEARS所依赖的基因本体注释，在Replogle 2022扰动基准测试中，对457个完全未见过的敲除基因实现了0.945的皮尔逊相关系数，而GEARS为0.84。第三，OCellus-Agent提供了一个规划器-路由器-验证器自然语言接口，在80个多任务查询上达到了75%的流水线准确率。移除语言模型嵌入后，扰动任务的皮尔逊相关系数骤降至0.06，证实了驱动性能提升的是学习到的功能表示而非图拓扑结构。作为细胞类型编码器，OCellus在四项基准数据集的线性探测准确率中以95.1%位列十四个基础模型之首，在二十二项评估的生物学任务中平均达到72.6%——相比最强基线配置绝对提升了57个百分点。作为语言模型，OCellus独特地生成了其预测的自然语言解释，这是所有竞争方法都不具备的能力。代码、预训练模型权重、图神经网络模块和智能体系统将在论文发表后公开。

## Abstract
Computational modeling of cellular behavior - the virtual cell - has emerged as a stated grand challenge at the intersection of artificial intelligence and biology, yet existing foundation models remain specialized: single-cell models process dissociated transcriptomes only, spatial models require dedicated spatial-aware architectures, and perturbation predictors depend on manually curated knowledge bases that cap generalization. Here we introduce OCellus, a single nine-billion-parameter language model (Qwen3.5-9B) fine-tuned on twenty-two biological tasks that simultaneously addresses all three limitations through three coordinated technical contributions on a shared backbone. First, EvenClock encodes two-dimensional spatial coordinates as eighteen clockface sectors of text, enabling spatial reasoning on a vanilla language model without architectural modification; on ten spatial transcriptomics tasks OCellus attains 77 percent spatial-neighborhood accuracy, 96 percent spatial-cellchat accuracy, and 0.70 proportion-cosine similarity on spatial deconvolution, all without any spatial-aware architectural components. Second, per-gene language-model embeddings replace the Gene Ontology annotations that GEARS depends on, achieving Pearson correlation 0.945 on the Replogle 2022 perturbation benchmark versus 0.84 for GEARS across 457 completely unseen knockout genes. Third, OCellus-Agent provides a Planner-Router-Verifier natural-language interface that achieves 75 percent pipeline accuracy on eighty multi-task queries. Removing language-model embeddings collapses perturbation Pearson to 0.06, confirming that learned functional representations - not graph topology - drive the gain. As a cell-type encoder, OCellus ranks first among fourteen foundation models in linear-probe accuracy at 95.1 percent across four benchmark datasets, and reaches 72.6 percent average across twenty-two evaluated biological tasks - a 57-percentage-point absolute gain over the strongest baseline configuration. As a language model, OCellus uniquely generates natural-language explanations of its predictions, a capability absent from all competing methods. Code, pre-trained model weights, the graph-neural-network module, and the agent system will be made available upon publication.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

现有单细胞、空间转录组学和扰动预测的基础模型存在三个关键局限：  
- **模态碎片化**：单细胞模型（如scGPT、Geneformer）只能处理解离转录组，无法融入空间上下文；空间模型（如SToFM、HEIST）需要专用空间感知架构，无法与单细胞模型共享参数，导致没有一个模型能同时统一三种任务。  
- **扰动泛化依赖人工知识库**：GEARS等扰动预测模型依赖人工整理的Gene Ontology（GO）注释，但GO对于许多基因不完整，导致泛化能力受限（在Replogle 2022基准上方向准确率仅54.6%）。  
- **黑箱不透明**：所有现有模型只输出数值预测，不能给出生物学推理解释，限制了科学发现和临床信任。

**整体含义**：本文旨在构建一个统一的“虚拟细胞”框架，通过一个共享的九亿参数语言模型（Qwen3.5-9B）同时解决上述三个问题，使模型既能进行单细胞、空间、扰动预测，又能生成自然语言解释，从而推动计算生物学从专用模型走向通用、可解释的虚拟细胞。

---

### 2. 论文提出的方法论：核心思想、关键技术细节

**核心思想**：利用多任务语言模型微调获得基因的功能性嵌入，通过三个协调技术（EvenClock、GNN、Agent）将空间、扰动和可解释性整合到同一骨干网络上，无需修改架构。

**关键技术细节**：

- **OCellus框架**：基于Qwen3.5-9B，通过LoRA（秩64，缩放因子64，dropout 0.05，目标所有注意力和MLP投影）在22项生物学任务上微调。训练分为四阶段：  
  - Stage 1：预训练（7个表示学习任务）  
  - Stage 2：适配器合并得到OCellus-Pretrain  
  - Stage 3：多任务指令微调（22项任务，实际训练26项，其中4项未评估）  
  - Stage 4：最终合并得到OCellus  
  总训练时间35.5小时（4×A800-80GB GPU），最终损失0.6649。

- **EvenClock空间编码**：将二维连续坐标离散化为18个钟面扇区（6个时钟方向×3个距离环：sec/min/hr），相邻细胞的基因列表作为文本前缀附加到中心细胞的基因句中，使普通语言模型无需架构修改即可处理空间信息。距离环半径按数据集的中位最近邻距离归一化，空扇区自动省略。

- **扰动预测GNN**：使用STRING v12蛋白质互作网络（15,309节点，416,518边，置信度≥0.70）。冻结OCellus的基因嵌入（4,096维）作为节点特征，加上敲除基因和基线表达基因的二进制指示符，通过3层图卷积网络（隐藏层128维，LayerNorm，ReLU，dropout 0.1）和MLP预测连续log2 fold-change。总参数约58.3万，训练30个epoch，损失函数为MSE（仅对前20个差异表达基因）。对比实验：用随机向量替代嵌入后Pearson降至0.06，证明语言模型嵌入是关键。

- **OCellus-Agent**：由Coordinator（训练好的Planner LoRA、规则Router、三层Verifier）、五种专家角色（Data Loader、Annotator、Perturbation、Spatial、Explainer，通过动态LoRA切换实现）和一个包含15个工具的Tool Registry组成。Planner将自然语言查询分解为可执行有向无环图，Verifier进行JSON模式检查、工具级合理性检查、Critic LoRA（训练在2000个接受/拒绝对）三层验证。成功率为75%（80次试验），比flat ReAct循环提升23.7个百分点。

---

### 3. 实验设计：使用的数据集、基准、对比方法

- **多任务基准**：22项生物任务（12项单细胞+10项空间），包括细胞类型注释、组织区域分割、细胞-细胞通讯推断、邻域预测、基因插补、密度分类、反卷积、空间可变基因检测、空间域识别、细胞类型特化标记预测、扰动预测（简化版）、基因相互作用分类（合成致死、表型相互作用）、基因-疾病关联、细胞标记识别、药物敏感性、跨物种细胞类型注释、发育阶段预测（小鼠E9.5–E16.5，人CS12–CS23）、蛋白质-蛋白质相互作用分类（STRING v12）、药物治疗细胞状态转换预测等。对比三种Qwen3.5-9B配置：基础模型、OCellus-Pretrain、完整OCellus。主要度量：平衡准确率（分类）、基因集召回率（排序/生成）、比例余弦相似度（反卷积）。

- **细胞表示质量基准**：与13个基础模型对比（scGPT, Geneformer, scFoundation, UCE, CellPLM, Nicheformer, scVI, PCA等），在4个数据集（胰腺、肺、PBMC、主动脉）共73,655细胞、52种细胞类型上评估线性探测准确率、kNN准确率、NMI。

- **扰动预测基准**：Replogle 2022 K562数据集，1,830个训练敲除基因 vs 457个未见测试敲除基因。对比GEARS、scGPT、CPA（数值取自文献）。度量：Pearson相关系数、方向准确率。

- **Agent基准**：80次自然语言查询试验（20个查询×4个数据集），对比flat ReAct循环。此外进行消融（无Critic、无Verifier、无LoRA切换、无Coordinator）。

---

### 4. 资源与算力

- **GPU型号与数量**：4×NVIDIA A800-80GB，NVLink互连。  
- **训练时长**：四阶段总墙钟时间约35.5小时（其中多任务微调为主）。最终训练损失0.6649。  
- **内存优化**：使用Liger Kernel，每GPU内存减少38GB（降幅58%），加速11%。未使用FlashAttention（与混合注意力架构不兼容）。  
- **嵌入层冻结**：因冻结仅损失1.8个百分点准确率但节省45GB内存，故选择冻结。

---

### 5. 实验数量与充分性

- **实验数量**：  
  - 多任务评估：22项任务，3种模型配置，生成热图。  
  - 细胞表示：4个数据集，14个模型对比，包含线性探测、kNN、NMI。  
  - 扰动预测：独立测试集457个敲除×20个响应基因，与GEARS、scGPT、CPA对比，含消融（随机嵌入对照）。  
  - Agent：80次试验，含5种消融配置（无Critic、无Verifier、无LoRA切换、flat ReAct）。  
  - 消融实验：嵌入替换、GNN训练曲线、Agent组件消融。  
  - 空间EvenClock：10项空间任务，全切片细胞类型预测（MOSTA E12.5，23,640细胞）。  
  - 跨域任务：跨物种（2,000细胞10类，87%准确率）、发育阶段（92.2%）、PPI（92.4%）、基因-疾病（89.0%）。  
  - 可解释性：50个预测由三位专家评分（平均4.2/5）。  
- **充分性与公正性**：  
  - 多任务使用平衡准确率，避免类别不平衡偏差。  
  - 扰动预测严格保证测试基因与训练无重叠。  
  - 对比使用官方GEARS实现并采用相同评估协议。  
  - 元数据中提到“score:9.0”，但实验设计整体较全面，消融充分。  
  - 不足：部分对比方法（scGPT、CPA）的指标取自文献，可能评估协议不完全一致；Agent只与flat ReAct对比，未与CellAgent、scAgents在完全相同查询上对比；空间编码未与其他替代方案（固定网格、极坐标、图像patch）公平比较。

---

### 6. 论文的主要结论与发现

1. **统一框架可行性**：一个九亿参数语言模型通过多任务微调和插件组件，可同时胜任单细胞编码、空间推理、扰动预测，并生成自然语言解释，平均22项任务准确率72.6%，超越最强基线57个百分点。  
2. **EvenClock有效**：无需架构修改即可实现空间推理，空间邻域准确率77.2%，细胞通讯95.6%，反卷积余弦相似度0.70。  
3. **语言模型嵌入优于GO注释**：在扰动预测中，以语言模型嵌入作为GNN节点特征，Pearson相关系数达0.945（GEARS为0.84），随机嵌入替代后跌至0.06，证实学习到的功能表示是主要驱动力。  
4. **跨物种、跨发育阶段**：跨物种细胞类型识别87.0%，发育阶段预测92.2%，表明模型学习到基因功能的普遍性。  
5. **可解释性**：OCellus可生成连接预测结果与已知生物学机制的自然语言解释（如TP53敲除后MDM2/CDKN1A下调、SERPINE1上调的补偿机制），这是其他方法不具备的。  
6. **智能体实用**：OCellus-Agent在80次查询中75%的流水线成功率，通过规划-路由-验证架构有效提升可靠性。

---

### 7. 优点：方法或实验设计上的亮点

- **方法创新**：  
  - EvenClock用文本表示空间，无需修改语言模型架构，保持主干统一。  
  - 语言模型嵌入替代人工知识库，既提升性能又减少偏见。  
  - 动态LoRA切换使得同一个骨干网担任编码器、预测器、解释器三种角色，参数效率高。  
- **工程完备**：  
  - 详细数据预处理（校正管家基因污染、跨数据库ID协调、自适应质控、胚胎期标签解析），并公开预处理管线。  
  - 四阶段训练策略合理，消融证实嵌入冻结等权衡。  
  - Verifier三层设计（模式检查、工具级合理性、Critic LoRA）有效减少幻觉和错误。  
- **实验全面**：覆盖22+4项任务、14个基础模型对比、多种消融、跨物种/发育、智能体组件消融、专家评估解释质量。  
- **可解释性**：自然语言解释是重大突破，使模型从“预测引擎”变为“科学推理伙伴”。  
- **开源承诺**：代码、权重、GNN模块、Agent系统将在发表后公开。

---

### 8. 不足与局限

- **实验覆盖**：  
  - 部分对比方法（scGPT、CPA）的数值取自文献（scPerturBench），评估协议可能与本文不完全一致（如使用的差异表达基因子集不同）。  
  - EvenClock未与固定网格、极坐标、图像块等其他空间编码方案在同一规模下公平比较。  
  - Agent只与flat ReAct基线对比，未在相同查询上与CellAgent、scAgents等进行直接对比（提及将留作未来工作）。  
  - 蛋白质-蛋白质相互作用分类的负样本通过随机采样（而非度匹配负样本），可能高估准确性（作者承认已推迟度匹配负样本）。  
- **偏差风险**：  
  - 模型主要基于Qwen3.5-9B，更大架构可能进一步提升，但未探索。  
  - GNN使用静态STRING图，未考虑动态条件特异性网络（如不同细胞类型或疾病状态下互作网络可能变化）。  
  - 空间编码的18个扇区半径基于全局中位距离，可能不适用于极度异质性组织。  
- **应用限制**：  
  - 智能体工具库封闭（15个工具），无法直接扩展第三方工具（计划通过MCP协议实现）。  
  - 模型大小（9B参数）虽通过LoRA节省显存，但整个Agent仍需约22GB GPU显存，仍有一定硬件门槛。  
  - 自然语言解释的质量评估仅由三位专家对50个预测评分（Likert 4.2/5），样本量较小，且可能存在专家主观偏差。  
  - 扰动预测仅测试了K562细胞系（Replogle 2022），未在多细胞系或体内环境中验证泛化性。  
- **开放性**：代码、权重尚未开源，当前仅提供流程描述，可重复性待发表后验证。

---

（完）
