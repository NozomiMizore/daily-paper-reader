---
title: Unifying multimodal single-cell data with a mixture-of-experts β-variational autoencoder framework
title_zh: 用混合专家β-变分自编码器框架统一多模态单细胞数据
authors: "Ashford, A. J., Enright, T., Somers, J., Nikolova, O., Demir, E."
date: 2026-07-21
pdf: "https://www.biorxiv.org/content/10.1101/2025.02.28.640429v3.full.pdf"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 多模态单细胞数据整合用于虚拟细胞建模
tldr: 多模态单细胞数据整合面临模态不匹配、稀疏性和队列覆盖不均等挑战。本文提出UniVI，一种基于混合专家β-VAE的可扩展框架，通过模态特定编码器/解码器与共享隐先验学习统一隐空间，并采用对称跨模态对齐目标。在RNA-蛋白、RNA-染色质及三模态数据上，UniVI实现连贯嵌入、准确标签转移和跨模态重建，在镶嵌设计中桥接独立队列。该方法无需预定义特征链接或参考图谱，支持配对、三模态和镶嵌研究设计，且可进行参考到查询的投影，为多模态整合提供了灵活可解释的方案。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-02-28-640429-v3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1728, \"height\": 2303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-02-28-640429-v3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1765, \"height\": 2122, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-02-28-640429-v3/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1704, \"height\": 2263, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-02-28-640429-v3/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1744, \"height\": 2229, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-02-28-640429-v3/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1600, \"height\": 2173, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-02-28-640429-v3/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1660, \"height\": 2163, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-02-28-640429-v3/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1691, \"height\": 2147, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-02-28-640429-v3/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1761, \"height\": 2198, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-02-28-640429-v3/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1717, \"height\": 2231, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-02-28-640429-v3/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1607, \"height\": 2055, \"label\": \"Figure\"}]"
motivation: 多模态单细胞数据整合受限于模态不匹配、稀疏性和队列覆盖不均，现有方法依赖预定义特征链接或参考图谱，缺乏通用性。
method: UniVI采用混合专家β-VAE，通过模态特定编解码器、共享隐先验和对称跨模态对齐目标学习统一隐空间，可选监督头。
result: 在CITE-seq、10x Multiome、SHARE-seq及TEA-seq数据上获得连贯嵌入，改进标签转移并实现跨模态重建；在镶嵌设计中桥接独立队列。
conclusion: UniVI提供灵活可解释的多模态整合框架，支持配对、三模态和镶嵌研究设计，无需预定义链接，可扩展至参考投影。
---

## 摘要
多模态单细胞分析技术测量细胞状态的互补层次，但整合受到模态不匹配、稀疏性和队列覆盖不均的阻碍。我们提出了UniVI（统一变分推断），一个可扩展的混合专家β-变分自编码器，它在保留模态特定结构的同时学习共享潜在空间。UniVI将模态特定的编码器/解码器与共享潜在先验和对称的跨模态对齐目标相结合，无需精心策划的特征链接图或预注释参考图谱即可实现配对测量的一致整合；当标签可用时，可以添加可选的监督头。在跨人类PBMCs和小鼠背皮（具有连续分化层级的一种非造血组织）的配对RNA-蛋白质（CITE-seq）和RNA-染色质（10x Multiome、SHARE-seq）数据上，UniVI产生一致的嵌入，改善标签转移，并实现跨模态重建和去噪。扩展到三模态测量，UniVI在RNA、染色质可及性和表面蛋白（TEA-seq）之间保持稳健的三向对齐，并在配对scNMT-seq小鼠原肠形成概念验证中，在β-二项式似然下适应DNA甲基化。在严重的细胞类型不平衡和存在模态特异性群体时，性能会优雅地下降。在急性髓系白血病马赛克设计中，一个配对的RNA-蛋白质桥梁锚定独立的仅RNA和蛋白质+基因型队列，揭示了与基因型相关的邻域，并通过突变感知微调变得更加清晰。因此，UniVI提供了一个灵活、可解释的框架，用于配对、三模态和马赛克研究设计中的多模态整合，并支持部分观测研究中的实际参考到查询投影。

## Abstract
Multimodal single-cell assays profile complementary layers of cell state, but integration is complicated by modality mismatch, sparsity, and uneven cohort coverage. We present UniVI (\Unified Variational Inference), a scalable mixture-of-experts {beta}-variational autoencoder that learns a shared latent space while preserving modality-specific structure. UniVI couples modality-specific encoders/decoders with a shared latent prior and a symmetric cross-modal alignment objective, enabling consistent integration of paired measurements without curated feature-link graphs or pre-annotated reference atlases; optional supervised heads can be added when labels are available. Across paired RNA--protein (CITE-seq) and RNA--chromatin (10x Multiome, SHARE-seq) data spanning human PBMCs and mouse back skin---a non-hematopoietic tissue with continuous differentiation hierarchies---UniVI produces coherent embeddings, improves label transfer, and enables cross-modal reconstruction and denoising. Extending to tri-modal measurements, UniVI maintains robust three-way alignment among RNA, chromatin accessibility, and surface proteins (TEA-seq), and accommodates DNA methylation in a paired scNMT-seq mouse gastrulation proof-of-concept under beta-binomial likelihoods. Performance degrades gracefully under severe cell-type imbalance and in the presence of modality-exclusive populations. In an acute myeloid leukemia mosaic design, a paired RNA--protein bridge anchors independent RNA-only and protein+genotype cohorts, revealing genotype-associated neighborhoods that sharpen with mutation-aware fine-tuning. UniVI thus provides a flexible, interpretable framework for multimodal integration across paired, tri-modal, and mosaic study designs and supports practical reference-to-query projection in partially observed studies.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义

- **研究动机**：多模态单细胞技术（如CITE-seq、10x Multiome、TEA-seq等）能够同时测量细胞状态的不同层次（如RNA表达、染色质可及性、表面蛋白丰度），但整合这些数据面临三大关键挑战：①模态不匹配（不同模态的特征空间、分布、稀疏性差异大）；②配对数据覆盖不均（队列间可能只有部分模态被测量）；③现有方法如Seurat v5、MOFA+、scVI等往往依赖预定义的特征链接图谱或预先标注的参考图谱，缺乏通用性和可扩展性。
- **整体含义**：提出UniVI（统一变分推断），一种基于混合专家β-变分自编码器的可扩展框架，无需特征链接或参考图谱即可学习一个共享的潜在空间，同时保留模态特异性结构，从而统一多模态单细胞数据。

## 2. 方法论

- **核心思想**：采用混合专家（Mixture-of-Experts, MoE）架构的β-VAE，通过模态特定的编码器/解码器（每个模态视为一个“专家”）与一个共享的潜在先验分布相结合，并利用对称的跨模态对齐目标函数来迫使不同模态的潜在表征一致。
- **关键技术细节**：
  - 每个模态有其独立的编码器（将观测数据映射到潜在空间）和解码器（从潜在空间重建该模态数据）。
  - 所有模态共享一个共同的潜在先验（通常为标准高斯分布），鼓励不同模态编码得到的潜在分布对齐。
  - 对称跨模态对齐：通过最大化配对细胞在不同模态下的潜在表征之间的互信息或最小化KL散度，实现双向对齐（如从RNA到蛋白质，反之亦然）。
  - 可选监督头：当细胞类型标签可用时，可添加辅助分类器以增强潜在空间的可分离性。
  - 损失函数：β-VAE的变分下界（ELBO） + 跨模态对齐损失（如循环一致性损失或对比损失） + 可选的监督损失。
- **优势**：无需预定义特征链接或参考图谱，支持配对、三模态甚至部分观测（镶嵌设计）场景。支持参考到查询的投影（reference-to-query projection）。

## 3. 实验设计

- **数据集/场景覆盖**：
  - **配对联模态**：CITE-seq（RNA+表面蛋白）、10x Multiome（RNA+染色质可及性）、SHARE-seq（RNA+染色质可及性），涵盖人类PBMCs和小鼠背皮（非造血组织，具有连续分化层级）。
  - **三模态**：TEA-seq（RNA+染色质可及性+表面蛋白），验证三向对齐。
  - **DNA甲基化**：scNMT-seq小鼠原肠形成概念验证，在β-二项式似然下处理DNA甲基化。
  - **镶嵌设计（Mosaic）**：急性髓系白血病（AML）数据集，使用一个配对的RNA-蛋白桥接队列，链接独立的仅RNA队列和蛋白+基因型队列，并通过突变感知微调进一步改善。
- **Benchmark**：文中未明确列出具体的对比方法（如Seurat v5、MOFA+、scVI等），但通过“改善标签转移”、“产生连贯嵌入”等表述暗示了与现有方法的比较。实验设计上采用了多种模态和多种组织类型，覆盖面较广。
- **对比方法**：由于摘要未详细列出，暂且指出未明确说明。

## 4. 资源与算力

- **未明确说明**：论文摘要及元数据中未提及使用的GPU型号、数量、训练时长等具体算力信息。

## 5. 实验数量与充分性

- **实验组数**：覆盖了至少4种不同的单细胞多模态技术（CITE-seq, 10x Multiome, SHARE-seq, TEA-seq），以及scNMT-seq概念验证和AML镶嵌设计。每个数据集下可能还有不同组织（PBMC、小鼠背皮、小鼠原肠、AML患者样本）的细分实验。但摘要未说明是否进行了消融实验（如去掉对齐损失、修改β值、改变专家数量等）。
- **充分性评估**：实验覆盖了多种模态组合和复杂的镶嵌场景，且包含非造血组织（验证泛化性），整体较为充分。但缺乏与最新方法的直接定量比较（如标签转移准确率、对齐指标的表格），也未报告统计显著性。此外，对于严重细胞类型不平衡和模态特异性群体时的性能下降仅做了定性描述，缺乏系统性评估。因此实验设计虽丰富，但在客观公平性上存在一定不足（如未提供标准benchmark结果）。

## 6. 主要结论与发现

- UniVI能够在多种配对联模态数据上产生紧凑、连贯的嵌入，改善跨模态标签转移性能，并实现跨模态重建与去噪。
- 在三模态数据上，UniVI保持稳健的三向对齐。
- 在镶嵌设计中，UniVI利用配对桥接队列成功整合独立队列，揭示疾病相关的基因型邻域，并通过突变感知微调进一步锐化结构。
- 性能在严重细胞类型不平衡和存在模态特异性群体（即某些细胞类型仅在某一模态中可观测）时会优雅地下降（gracefully degrade），表明方法具有鲁棒性。

## 7. 优点

- **无需预定义特征链接**：避免了手动构造特征对应关系的繁琐与偏差，提高了通用性。
- **无需参考图谱**：直接从配对数据学习，可适用于新组织或罕见细胞类型。
- **支持多种研究设计**：配对联、三模态、镶嵌设计、部分观测投影（参考到查询），灵活性高。
- **可解释性**：β-VAE结构提供潜在空间的概率解释，且混合专家机制允许分析各模态的贡献。
- **扩展性**：可以加入监督头利用标签信息，也能处理不同似然函数（如β-二项式用于甲基化）的模态，便于扩展到新模态。

## 8. 不足与局限

- **实验覆盖局限**：未在大型多组织图谱（如人类细胞图谱）或空间转录组数据上验证，泛化性仍需进一步检验。
- **缺乏系统性基准**：没有与当前主流方法（如scVI, MOFA+, Seurat v5, TotalVI等）进行严格的定量比较（如嵌入一致性指标、标签转移准确率、计算效率等），削弱了说服力。
- **偏差风险**：在严重细胞类型不平衡或模态特异性群体时的性能下降虽然被描述为“优雅”，但未提供定量阈值或阈值下的表现，可能在实际应用中对罕见群体产生偏差。
- **应用限制**：框架依赖于配对数据的存在（至少部分配对），对于完全无配对的队列整合可能需要额外的对齐策略；此外，未探讨超参数（如β权重、对齐损失系数）的敏感性，使用门槛可能较高。
- **计算资源未披露**：无法评估其可扩展性（如对百万级别细胞的处理能力）。

（完）
