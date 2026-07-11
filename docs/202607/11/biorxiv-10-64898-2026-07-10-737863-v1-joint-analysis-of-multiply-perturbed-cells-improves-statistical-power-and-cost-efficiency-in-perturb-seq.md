---
title: Joint analysis of multiply perturbed cells improves statistical power and cost efficiency in Perturb-seq
title_zh: 多个扰动细胞的联合分析提高了Perturb-seq的统计功效和成本效率
authors: "Yeung, J., Tan, J., Wang, L., Wu, D., Melo Carlos, S., Kageyama, J., Kamm, J., Chu, B. B., Mayba, O., Forrest, W. F., Xie, S."
date: 2026-07-11
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.10.737863v1.full.pdf"
tags: ["query:virtual-cell"]
score: 8.0
evidence: 分析Perturb-seq中多次扰动细胞的扰动响应
tldr: "传统Perturb-seq设计每个细胞单个导引，成本高且丢弃多重导引细胞，浪费数据。本文发现多重导引细胞存在应激和细胞周期抑制，但开发PerturbMatch框架可准确分析其信号。双联体和三联体恢复扰动响应最准确，纳入它们使成本降低81%，信息损失仅与技术重复相当。推荐有意混合单导引、双联体和三联体，以提升统计功效并降低成本。"
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-10-737863-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1020, \"height\": 1120, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-10-737863-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 859, \"height\": 1209, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-10-737863-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1020, \"height\": 1031, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-10-737863-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1005, \"height\": 1341, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-10-737863-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 998, \"height\": 1145, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-10-737863-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 877, \"height\": 1208, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-10-737863-v1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1010, \"height\": 1348, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-10-737863-v1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1001, \"height\": 1217, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-10-737863-v1/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1011, \"height\": 874, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-10-737863-v1/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 930, \"height\": 1256, \"label\": \"Figure\"}]"
motivation: Perturb-seq传统设计丢弃多重导引细胞，导致成本高、数据利用率低，需量化其影响并开发分析方法。
method: 开发PerturbMatch统计框架，系统性分析单、双、三及高阶多重导引细胞的信号恢复与信息损失。
result: "双联体和三联体恢复效果最接近单导引；在三个筛选中成本降81%，信息损失在1.5倍内；纳入丢弃数据后可用细胞增、统计功效升。"
conclusion: 推荐包含单导引、双联体和三联体的设计，在保证信号恢复前提下显著提高成本效率。
---

## 摘要
Perturb-seq可大规模测量对遗传扰动的转录组反应，但传统设计富集每个细胞一个向导RNA，仍然资源密集。标准分析丢弃携带多个向导的细胞，进一步限制了每个实验的可用产量。在这里，我们描述了纳入这些向导多重态如何影响信号恢复、信息损失和成本降低。在最高向导负荷下，细胞表现出压力增加和细胞周期进程受到抑制。我们开发了PerturbMatch，一个可扩展的统计框架来分析向导多重态。在不同类别的向导多重态中，双联体和三联体比对高阶多重态更准确地恢复了扰动反应。在三个5000基因Perturb-seq筛选（具有增加的向导负载）中，每个细胞的成本降低了高达81%，而信息损失仍保持在技术重复之间观察到的损失的1.5倍以内。在现有的全基因组Perturb-seq数据中，纳入先前丢弃的向导多重态增加了可用细胞数量并提高了统计功效。与单态保留集相比，添加向导多重态使信号恢复更接近理论预期的可重复性。总体而言，我们建议有意包含单向导细胞、向导双联体和向导三联体的设计，以提高成本效率，同时保持信号恢复。

## Abstract
Perturb-seq measures transcriptomic responses to genetic perturbations at scale, but conventional designs that enrich for one guide RNA per cell remain resource-intensive. Standard analyses discard cells carrying multiple guides, further limiting the usable yield from each experiment. Here, we characterize how incorporating these guide multiplets affects signal recovery, information loss, and cost reduction. At the highest guide burden, cells showed increased stress and suppressed cell-cycle progression. We develop PerturbMatch, a scalable statistical framework to analyze guide multiplets. Among different classes of guide multiplets, doublets and triplets recovered perturbation responses more accurately than higher-order multiplets. Across three 5000-gene Perturb-seq screens with increasing guide loading, per-cell costs decreased by up to 81% while information loss remained within 1.5-fold of the loss observed between technical replicates. In existing genome-wide Perturb-seq data, incorporating previously discarded guide multiplets increased usable cell numbers and improved statistical power. Compared with a singlet holdout set, adding guide multiplets moved signal recovery closer to the theoretical expected reproducibility. Overall, we recommend a design that intentionally includes single-guide cells, guide doublets, and guide triplets to improve cost efficiency while preserving signal recovery.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- 传统 Perturb-seq 实验设计富集每个细胞一个向导 RNA（sgRNA），资源密集且成本高昂。
- 标准分析流程直接丢弃携带多个向导 RNA 的细胞（即“多重导引细胞”），导致大量数据被浪费，进一步限制了每个实验的可用细胞产量。
- 亟需量化纳入这些多重导引细胞对信号恢复、信息损失和成本降低的影响，并开发相应的分析方法，以提升统计功效和成本效率。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：不完全丢弃多重导引细胞，而是将其纳入分析，通过统计框架准确恢复扰动信号，同时大幅降低每个细胞的实验成本。
- **核心方法：PerturbMatch 框架**  
  - 是一个可扩展的统计框架，专门用于分析向导多重态（guide multiplets）。
  - 针对不同阶数的多重导引细胞（双联体、三联体、高阶多重态）评估其扰动响应恢复的准确性。
  - 通过对比单态（singlet，单导引细胞）的扰动信号，量化多重态的信号恢复程度和信息损失。
- **关键技术细节**（根据摘要和元数据推断）：
  - 分析了不同向导负载下细胞的生物学状态：发现最高向导负荷时细胞应激增加、细胞周期进程抑制。
  - 使用技术重复间的信息损失作为参考基准，评估多重态引入的信息损失（控制在 1.5 倍以内）。
  - 提出推荐设计：有意混合单导引细胞、双联体和三联体，以平衡信号恢复与成本效率。

## 3. 实验设计
- **数据集/场景**：
  - 三个独立的 5000 基因 Perturb-seq 筛选，具有递增的向导负载（guide loading）。
  - 现有全基因组 Perturb-seq 数据，用于验证纳入丢弃的多重导引细胞后的效果。
- **基准（benchmark）**：
  - 以单态（单向导管）的扰动信号恢复作为基准。
  - 以技术重复之间的信息损失作为衡量“可接受损失”的参考。
- **对比方法**：
  - 传统方法：丢弃所有多重导引细胞，只保留单态（singlet-only）。
  - 本文提议方法：纳入双联体、三联体甚至部分高阶多重态。
  - 比较信号恢复准确性、信息损失倍数、成本降低比例以及统计功效提升。

## 4. 资源与算力
- 论文摘要和元数据中未明确提及所使用的 GPU 型号、数量、训练时长等计算资源信息。
- 推测作者可能使用标准的高性能计算集群进行统计分析和模拟，但具体细节未公开。

## 5. 实验数量与充分性
- **实验数量**：
  - 包含三个不同向导负载的 5000 基因筛选实验（相当于三个主数据集）。
  - 外加一个已有全基因组 Perturb-seq 数据的验证实验。
  - 对不同阶数多重态（双联体、三联体、高阶）分别进行了评估。
- **充分性**：
  - 实验覆盖了多重态的主要类型和不同负载条件，并且在实际全基因组数据中进行了验证。
  - 使用了技术重复作为内部对照，比较了信息损失倍数，客观性较好。
  - 但仍缺乏独立实验室的重复验证，且仅基于几种特定筛选条件，推广性需进一步确认。

## 6. 主要结论与发现
- 双联体和三联体能够最准确地恢复扰动响应，高阶多重态恢复效果较差。
- 在三个 5000 基因筛选实验中，每个细胞的成本降低高达 81%，而信息损失仅维持在技术重复间损失的 1.5 倍以内。
- 纳入之前丢弃的多重导引细胞后，可用细胞数量增加，统计功效显著提升。
- 与仅保留单态相比，添加多重态使信号恢复更接近理论预期的可重复性。
- 推荐有意包含单向导细胞、双联体、三联体的实验设计，可在保证信号恢复的前提下大幅提高成本效率。

## 7. 优点
- **方法论创新**：提出 PerturbMatch 统计框架，首次系统量化多重导引细胞的价值，并给出了明确的设计建议。
- **成本效益突出**：最高 81% 的成本降低，对大规模 Perturb-seq 项目具有实际经济价值。
- **信号损失可控**：信息损失控制在技术重复范围内的 1.5 倍，可接受性强。
- **数据利用率提升**：将原本丢弃的数据重新利用，提高统计功效，减少实验浪费。
- **实用导向**：提供了具体的设计指导（包含双联体和三联体），易于研究者采纳。

## 8. 不足与局限
- **实验覆盖有限**：仅基于 5000 基因筛选和特定全基因组数据，未测试其他规模（如更小或更大）的文库，以及不同细胞类型/扰动类型。
- **高阶多重态处理不完整**：高阶多重态恢复效果差，论文未提出针对它们的有效分析策略，建议直接丢弃可能仍有改进空间。
- **资源消耗未量化**：文中未提及 PerturbMatch 框架的计算资源需求，可能在高通量数据上存在计算瓶颈。
- **生物学偏差风险**：高压向导负载下细胞出现应激和周期抑制，可能引入系统性偏差，但论文未深入讨论如何校正这些额外效应。
- **缺乏独立重复验证**：所有分析均由同一团队在内部数据上完成，外部独立数据集验证缺失。

（完）
