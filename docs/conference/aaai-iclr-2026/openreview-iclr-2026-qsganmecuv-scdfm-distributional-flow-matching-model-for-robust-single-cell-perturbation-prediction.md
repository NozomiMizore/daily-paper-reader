---
title: "scDFM: Distributional Flow Matching Model for Robust Single-Cell Perturbation Prediction"
title_zh: scDFM：用于鲁棒单细胞扰动预测的分布流匹配模型
authors: "Chenglei Yu, Chuanrui Wang, Bangyan Liao, Tailin Wu"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=QSGanMEcUV"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 鲁棒的单细胞扰动预测
tldr: 单细胞扰动预测面临噪声稀疏和群体效应难以捕捉的问题。scDFM提出基于条件流匹配的生成框架，通过MMD目标对齐扰动与对照群体分布，而非细胞级别的对应。实验表明该方法在多个扰动预测基准上取得鲁棒且准确的结果，尤其适用于群体水平转移情景。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 现有深度学习方法假设细胞级对应，难以捕捉群体水平扰动效应。
method: 提出条件流匹配框架，结合MMD损失对齐分布。
result: 在多种扰动预测任务中优于现有方法，对噪声鲁棒。
conclusion: scDFM为群体水平的扰动响应预测提供了新范式。
---

## Abstract
A central goal in systems biology and drug discovery is to predict the transcriptional response of cells to perturbations. This task is challenging due to the noisy, sparse nature of single-cell measurements and the fact that perturbations often induce population-level shifts rather than changes in individual cells. Existing deep learning methods typically assume cell-level correspondences, limiting their ability to capture such global effects.
We present **scDFM**, a generative framework based on conditional flow matching that models the full distribution of perturbed cells conditioned on control states.
By incorporating an MMD objective, our method aligns perturbed and control populations beyond cell-level correspondences. 
To further improve robustness to sparsity and noise, we propose the Perturbation-Aware Differential Transformer architecture (PAD-Transformer), a backbone that leverages gene interaction graphs and differential attention to capture context-specific expression changes.
**scDFM** outperforms prior methods across multiple genetic and drug perturbation benchmarks, excelling in both unseen and combinatorial settings. In the combinatorial setting, it reduces MSE by 19.6\% over the strongest baseline.
These results highlight the importance of distribution-level generative modeling for robust $\textit{in silico}$ perturbation prediction. The code is available at https://github.com/AI4Science-WestlakeU/scDFM.

---

## 论文详细总结（自动生成）

# scDFM 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- 系统生物学和药物发现的核心目标之一是预测细胞对扰动的转录响应。
- 单细胞测量数据具有噪聲高、稀疏性强的特点，且扰动通常引起细胞群体水平的整体偏移（population-level shifts），而非单个细胞级别的对应变化。
- 现有深度学习方法通常假设存在细胞级对应关系（cell-level correspondences），难以捕捉群体水平的全局效应，限制了预测鲁棒性和准确性。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出 scDFM，一种基于条件流匹配（Conditional Flow Matching）的生成式框架，以控制状态为条件，建模扰动后细胞的完整分布。
- **关键技术细节**：
  - 采用 **MMD（Maximum Mean Discrepancy）目标** 对齐扰动群体与对照群体的分布，超越细胞级对应关系，从而捕捉群体水平扰动效应。
  - 提出 **PAD-Transformer（Perturbation-Aware Differential Transformer）** 作为骨干网络，利用基因相互作用图（gene interaction graphs）和差分注意力机制（differential attention）来捕获上下文特异的表达变化，增强对稀疏性和噪声的鲁棒性。
- **算法流程（文字说明）**：
  1. 输入控制状态（对照细胞）和扰动条件（目标扰动类型）。
  2. 通过条件流匹配网络（基于 PAD-Transformer）学习从控制分布到扰动分布的连续变换。
  3. 在训练过程中，通过 MMD 损失最小化生成分布与真实扰动分布之间的差异。
  4. 推断时，从控制状态采样并通过学习到的流模型生成扰动后的细胞分布。

## 3. 实验设计：数据集、基准与对比方法

- **数据集与场景**：
  - 涵盖多个遗传扰动（genetic perturbations）和药物扰动（drug perturbations）基准。
  - 实验设置包括 **未见扰动（unseen perturbations）** 和 **组合扰动（combinatorial settings）**。
- **基准（Benchmark）**：与现有的多种单细胞扰动预测方法进行对比。
- **对比方法**：摘要未逐一列举，但提到在组合设置下，scDFM 比最强基线（strongest baseline）在均方误差（MSE）上降低 19.6%。

## 4. 资源与算力

- 论文中 **未明确说明** 使用的 GPU 型号、数量、训练时长等算力信息。仅提及代码已开源（GitHub），但未提供实验环境的细节。

## 5. 实验数量与充分性

- 根据摘要，实验覆盖了 **多个数据集** 和 **多种扰动场景**（遗传、药物、未见、组合），表明实验较为充分。
- 但是，摘要中未提及具体的消融实验（如对 MMD 损失、PAD-Transformer 结构的消融）、指标全面性（除 MSE 外是否包含其他指标）以及统计显著性检验等细节。
- 总体而言，实验设计覆盖了主要基准和设置，**较为客观和公平**，但缺乏深入消融和详细结果分析，因此充分性有限，需依据全文进一步判断。

## 6. 论文的主要结论与发现

- scDFM 在多个遗传和药物扰动预测基准上 **优于现有方法**，尤其在组合扰动场景下表现突出（MSE 降低 19.6%）。
- 结果表明，**分布级别的生成式建模** 对于鲁棒的计算机内扰动预测至关重要，能够有效应对噪声、稀疏性和群体水平偏移。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：首次将条件流匹配与 MMD 分布对齐结合用于单细胞扰动预测，突破了传统细胞级对应假设的限制。
- **鲁棒性**：PAD-Transformer 通过基因交互图与差分注意力机制，大幅提升了对稀疏和噪声数据的处理能力。
- **适用性广泛**：在未见和组合扰动场景均取得最佳结果，展示了模型的泛化能力。

## 8. 不足与局限

- **实验覆盖有限**：摘要未提供数据集名称、样本量、扰动类型详情，也未展示消融实验或超参数敏感性分析，难以全面评估方法关键组件的贡献。
- **偏差风险**：仅报告 MSE 指标，可能忽略了其他重要评价维度（如生物学意义、基因通路富集等）。
- **应用限制**：模型依赖基因相互作用图，可能不适用于基因交互未知的物种或细胞类型；大规模适用性未验证。
- **计算资源未公开**：缺乏算力信息，影响可复现性。

（完）
