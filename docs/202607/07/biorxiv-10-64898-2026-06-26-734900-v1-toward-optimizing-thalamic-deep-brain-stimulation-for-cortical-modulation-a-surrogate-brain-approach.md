---
title: "Toward Optimizing Thalamic Deep Brain Stimulation for Cortical Modulation: A Surrogate Brain Approach"
title_zh: 优化丘脑深部脑刺激以实现皮层调节：一种替代大脑方法
authors: "Ahmed, R., Feng, Y., Roe, A. W., Chen, Z. S."
date: 2026-07-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.26.734900v1.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 神经扰动推断，用于刺激优化的替代脑方法
tldr: 针对丘脑深部脑刺激（DBS）优化皮层调控的问题，本文提出基于替代脑的神经扰动推断（NPI）方法，通过拟合静息态fMRI数据的非线性动态模型估计受试者特异性丘脑皮质有效连接（EC）。引入tSNR加权损失和多尺度一致性损失改进训练，在合成基准和两个独立数据集（猕猴和人类）上验证了位点特异性EC结构，并构建约束线性控制问题优化稀疏刺激靶点。该方法为个性化DBS参数优化提供了计算框架。
source: biorxiv
selection_source: fresh_fetch
motivation: 实现丘脑DBS精确皮层调控需受试者特异性有效连接估计和优化框架，现有方法难以满足高分辨率要求。
method: 扩展NPI至360皮层区域和442丘脑体素网络，采用tSNR加权损失和跨尺度一致性损失训练非线性动态模型，推断有效连接。
result: 在合成数据和两个数据集（MacStim、HumanTC）上验证，预测的EC结构与已知神经解剖学一致，实现位点特异性皮层激活模式。
conclusion: 该工作为个性化丘脑DBS优化提供了可推广的计算途径，适用于人类和非人灵长类。
---

## 摘要
丘脑是一个中央枢纽，与广泛的皮层和皮层下节点相连接。丘脑深部脑刺激（DBS）为分布式皮层调节提供了一种原则性策略：由于不同的丘脑核团投射到空间上分离的皮层区域，刺激单个丘脑部位可以影响多个皮层节点。实现这一潜力需要准确的受试者特异性丘脑皮层有效连接（EC）估计，以及一个用于优化刺激参数以实现所需皮层反应的计算框架。在这里，我们使用神经扰动推理（NPI）来应对这两个挑战，这是一种替代大脑方法，通过对拟合到静息态fMRI数据的非线性动力学模型施加虚拟扰动来估计EC。我们将NPI扩展到一个高分辨率丘脑皮层网络，该网络包含360个皮层区域和覆盖12个核团的442个丘脑体素。我们在训练中引入了两项创新：（i）考虑信号异质性的时间信噪比（tSNR）加权损失函数，以及（ii）正则化模型复杂度的多分辨率、跨尺度一致性损失。这些策略在不同tSNR条件下的合成基准测试中提高了性能。利用推断出的受试者特异性EC，我们进一步构建了一个约束线性控制问题，以识别能够实现所需皮层激活模式的稀疏丘脑刺激靶点。我们在两个独立数据集上验证了推断的EC结构：MacStim数据集（包含两只接受内侧枕核红外神经刺激的猕猴）和HumanTC静息态fMRI数据集（包含十二名人类受试者）。我们的结果揭示了部位特异性的丘脑皮层EC特征，产生了与已知真实结构一致的可解释预测。总之，这项工作为人类和非人灵长类动物中丘脑DBS的个性化优化建立了一条计算基础路径。

## Abstract
The thalamus is a central hub that interfaces with widespread cortical and subcortical nodes. Thalamic deep brain stimulation (DBS) offers a principled strategy for distributed cortical modulation: since distinct thalamic nuclei project to spatially segregated cortical territories, stimulation at a single thalamic site can influence multiple cortical nodes. Realizing this potential requires accurate subject-specific estimates of directed thalamocortical effective connectivity (EC) and a computational framework for optimizing stimulation parameters that achieve desired cortical responses. Here, we address both challenges using Neural Perturbational Inference (NPI), a surrogate-brain approach that estimates EC by applying virtual perturbations to a nonlinear dynamical model fitted to resting-state fMRI data. We extend NPI to a high-resolution thalamocortical network comprising 360 cortical regions and 442 thalamic voxels spanning 12 nuclei. We introduce two innovations in training: (i) a temporal signal-to-noise ratio (tSNR)-weighted loss accounting for signal heterogeneity, and (ii) a multi-resolution, cross-scale consistency loss that regularizes model complexity. These strategies yield improved performance in synthetic benchmarks across varying tSNR regimes. Leveraging the inferred subject-specific EC, we further formulate a constrained linear control problem to identify sparse thalamic stimulation targets that achieve desired cortical activation patterns. We validate the inferred EC structure on two independent datasets: the MacStim dataset comprising two macaque monkeys with infrared neural stimulation on medial pulvinar, and the HumanTC resting-state fMRI dataset comprising twelve human subjects. Our results reveal site-specific thalamocortical EC profiles, producing interpretable predictions that align with known ground-truth structures. Together, this work establishes a computationally grounded pathway toward personalized optimization of thalamic DBS in both human and nonhuman primates.