---
title: "EBD-DTI: Episodic Bridge Diffusion for Zero-Shot Cold-Start Drug-Target Interaction Prediction"
title_zh: "EBD-DTI: 用于零样本冷启动药物-靶标相互作用预测的情景桥接扩散"
authors: "Liu, J., Le, J., Wei, C., Liu, M., Yin, Z."
date: 2026-07-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.14.738384v1.full.pdf"
tags: ["query:virtual-cell"]
score: 7.0
evidence: 针对未见实体的零样本药物-靶标相互作用预测
tldr: "药物-靶标相互作用预测面临冷启动挑战：完全未见药物或蛋白质无法利用任何已知交互。现有序列方法忽略拓扑，图方法需依赖全局扩散或少量样本。本文提出EBD-DTI，通过情景式冷启动训练（每轮随机掩码实体作为伪冷启）结合桥接条件局部子图与多跳扩散，为冷实体提供近邻关系上下文。在BioSNAP、BindingDB和DrugBank上严格零样本评估，AUC提升最高12%，实现了纯归纳图模型的高效零样本预测。"
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738384-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1769, \"height\": 781, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738384-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1759, \"height\": 581, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-14-738384-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 874, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-14-738384-v1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1797, \"height\": 527, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-14-738384-v1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1793, \"height\": 524, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-14-738384-v1/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 500, \"height\": 414, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-14-738384-v1/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 588, \"height\": 806, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-14-738384-v1/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1428, \"height\": 353, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-14-738384-v1/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 833, \"height\": 469, \"label\": \"Table\"}]"
motivation: 现有图DTI模型无法有效处理零样本冷启动，常需全局扩散或已知交互样本，亟需无需任何测试交互即可推理的图方法。
method: EBD-DTI采用情景式冷启动训练，随机掩码训练实体逼真模拟冷启；通过桥接条件局部子图与多跳扩散注入最近邻关系上下文。
result: "在三个基准数据集上严格零样本评估，AUC最高提升12%，性能媲美甚至超越需要已知交互的少样本方法。"
conclusion: EBD-DTI首次实现纯归纳图模型零样本DTI预测，为冷启动药物发现提供有效新范式。
---

## 摘要
预测完全未见药物或蛋白质的药物-靶标相互作用（DTI）——冷启动问题——仍然是计算药物发现中的关键挑战。虽然基于序列的方法天然支持零样本泛化，但它们常常忽略关系拓扑，而现有的基于图的方法要么依赖全局扩散（这模糊了归纳与转导评估的边界），要么在测试时需要少量已知相互作用样本（小样本）。我们提出了EBD-DTI，这是一个在基于图的DTI模型中实现零样本推理的框架，不需要未知实体的任何已知相互作用。关键创新在于情景冷启动训练：在每个epoch，随机选择一部分训练实体进行掩码并视为伪冷启动，迫使模型通过显式梯度监督学习冷启动推理。桥接条件局部子图结合多跳扩散，为冷实体提供来自最近观测邻居的关系上下文。在三个基准（BioSNAP、BindingDB和DrugBank）上的实验表明，在严格的零样本评估下，EBD-DTI与最先进方法相比取得了竞争性或更优的性能，情景训练将AUC提升了高达12%。

## Abstract
Predicting drug-target interactions (DTI) for entirely unseen drugs or proteins---the cold-start problem---remains a critical challenge in computational drug discovery. While sequence-based methods naturally support zero-shot generalization, they often ignore relational topology, and existing graph-based approaches either rely on global diffusion that blurs the boundary between inductive and transductive evaluation or require a few known interaction samples at test time (few-shot). We present EBD-DTI, a framework that enables zero-shot inference in graph-based DTI models without requiring any known interactions for unseen entities. The key innovation is episodic cold-start training: at each epoch, a random subset of training entities is masked and treated as pseudo-cold, forcing the model to learn cold-start inference with explicit gradient supervision. A bridge-conditioned local subgraph, together with multi-hop diffusion, provides cold entities with relational context from their nearest observed neighbors. Experiments on three benchmarks (BioSNAP, BindingDB, and DrugBank) demonstrate that EBD-DTI achieves competitive or superior performance compared to state-of-the-art methods under strict zero-shot evaluation, with episodic training improving AUC by up to 12%.