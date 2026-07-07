---
title: "V3Cell: A Vision-Guided Virtual 3D Cell Framework for Phenotypic Modeling and Perturbation Prediction"
title_zh: V3Cell：一种面向表型建模和扰动预测的视觉引导虚拟3D细胞框架
authors: "Lu, Y., Xun, D., chenke, X., Xiaobo, Z., Zhigang, Z., Pengyu, C., Xiwen, Y., Zhengzheng, Y., Jiahua, R., Huili, H., Jianying, H., Pengwei, H."
date: 2026-06-24
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.23.734130v1.full.pdf"
tags: ["query:virtual-cell"]
score: 9.0
evidence: 虚拟细胞模型用于扰动预测
tldr: 现有虚拟细胞模型局限于单细胞静态预测，无法捕捉类器官的组织架构和动态发育。V3Cell基于无标记明场显微镜构建虚拟3D类器官，通过前景感知模型生成跨谱系的静态虚拟细胞，并引入时序模块从少量早期帧预测发育命运及扰动响应轨迹。在结肠、胃、肺类器官上，虚拟细胞在分布指标、微纹理和形态测量上接近真实样本，效应量小。该框架无需组学或荧光标记，为类器官尺度的扰动预测建立非侵入性明场范式。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有虚拟细胞模型仅预测单细胞静态终点，缺乏对类器官组织级架构和连续发育动力学的模拟。
method: 提出V3Cell框架，利用无标记明场图像通过前景感知模型构建静态虚拟3D细胞，并使用时序模块预测发育命运和扰动响应轨迹。
result: 虚拟细胞在分布指标、微纹理和谱系形态测量上高度匹配真实样本，时序预测准确且能复现真实扰动响应。
conclusion: V3Cell实现了无需组学或荧光标记的非侵入式类器官扰动预测，为疾病建模和药物发现提供新范式。
---

## 摘要
预测类器官对化学扰动的反应是疾病建模和药物发现的核心。现有的虚拟细胞模型在单细胞水平上运行，通过破坏性检测产生静态终点预测。这就在类器官尺度上留下了一个关键空白，因为生物特性是由组织水平的结构和连续的发育动力学定义的，而不是单细胞特征。在这里，我们介绍V3Cell，一个视觉引导的框架，直接从非侵入性的明场显微镜构建类器官的计算机模拟替代品。一个前景感知模型构建了跨结肠、胃和肺类器官谱系的静态虚拟3D细胞。这些虚拟3D细胞在分布度量、微纹理和谱系特异性形态测量方面与真实样本紧密匹配，大多数描述符的效应量较小。一个时间模块进一步从仅六个早期帧观测中预测发育命运，并模拟命运条件下的时空轨迹，这些轨迹密切再现了真实的扰动响应。V3Cell不需要组学分析或荧光标记，建立了一种基于非侵入性明场的类器官尺度扰动预测范式。我们的代码和数据公开在https://github.com/Laineyoulu/V3Cell。

## Abstract
Predicting how organoids respond to chemical perturbations is central to disease modeling and drug discovery. Existing virtual cell models operate at the single-cell level, producing static endpoint predictions from destructive assays. This leaves a critical gap at the organoid scale, where biological identity is defined by tissue-level architecture and continuous developmental dynamics rather than single-cell features. Here we introduce V3Cell, a vision-guided framework that constructs in silico surrogates of organoids directly from non-invasive bright-field microscopy. A foreground-aware model constructs static virtual 3D cells across colon, stomach, and lung organoid lineages. These virtual 3D cells closely match real samples across distributional metrics, micro-texture, and lineage-specific morphometrics, with small effect sizes for most descriptors. A temporal module further predicts developmental fate from as few as six early-frame observations and models fate-conditioned spatiotemporal trajectories that closely recapitulate real perturbation responses. V3Cell requires no omics profiling or fluorescent labeling, establishing a non-invasive brightfield-based paradigm for organoid-scale perturbation prediction. Our code and data are publicly available at https://github.com/Laineyoulu/V3Cell.