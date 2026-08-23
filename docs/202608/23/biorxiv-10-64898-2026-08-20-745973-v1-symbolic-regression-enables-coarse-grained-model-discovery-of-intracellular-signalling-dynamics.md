---
title: Symbolic regression enables coarse-grained model discovery of intracellular signalling dynamics
title_zh: 符号回归使细胞内信号动力学的粗粒化模型发现成为可能
authors: "de Pomereu, T., Fröhlich, F."
date: 2026-08-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.20.745973v1.full.pdf"
tags: ["query:virtual-cell"]
score: 7.0
evidence: 符号回归自动发现细胞内信号动态粗粒化模型，与扰动建模和虚拟细胞密切相关
tldr: 细胞信号通路常因癌症失调，需动力学建模，但数据有限促使粗粒化降维。本文提出用符号回归数据驱动地检验系统能否在观测变量上紧凑粗粒化，并推断可解释模型。在合成酶系统中恢复米氏动力学，数据退化时简化为有效速率律。应用于ERK磷酸化数据，识别出癌症相关基因过表达情境下的紧凑速率律。该方法可判断何时需要紧凑粗粒化描述，并生成假设或指导新测量。
source: biorxiv
selection_source: fresh_fetch
motivation: 经典粗粒化建模依赖强假设，难以判断部分实验观测是否支持低维系统描述。
method: 利用符号回归从数据中自动发现粗粒化动力学模型，并通过稀疏神经ODE基线对照评估可学习性。
result: 恢复米氏动力学，在ERK数据中识别出癌症相关过表达下的紧凑速率律；SR失败时动力学更复杂。
conclusion: 符号回归能检验紧凑粗粒化描述是否成立，促进假设生成与实验测量设计。
---

## 摘要
细胞通过蛋白质网络响应其环境，这些网络通常在癌症中失调，因此动力学建模至关重要。实验数据和计算资源的局限性促使人们采用粗粒化方法来构建低维描述。然而，经典的粗粒化建模方法依赖于强假设，使得部分实验观测何时能支持系统动力学的简化描述尚不清楚。在此我们表明，符号回归(SR)提供了一种数据驱动的方式，用于检验信号系统在测量变量上的动力学是否以及如何紧凑地粗粒化，并在可行时推断出具有机理解释性的模型。在合成酶系统中，SR恢复了两步机制和三步扩展下的Michaelis-Menten动力学。随着数据质量下降，SR简化为有效的动力学定律，同时保持正确的理论极限。将SR应用于已发表的随时间分辨的ERK磷酸化数据，SR在选定的癌症相关基因过表达背景下识别出紧凑的磷酸化ERK速率定律，产生可解释的动力学效应。一个稀疏神经ODE基线在SR成功时需要少量输入，但在SR失败时平均需要更多输入，这表明在可学习简化模型的情况下，SR失败与简单数学模型无法描述的更复杂动力学相关。总之，这些发现确立了符号回归作为一种测试何时需要紧凑粗粒化描述的方法，在存在紧凑描述时产生假设，在不存在时激发潜在的新测量。

## Abstract
Cells respond to their environment through protein networks often dysregulated in cancer, making dynamical modelling crucial. Limitations in experimental data and computational resources motivate coarse-graining methods to build low-dimensional descriptions. Yet classical approaches to coarse-grained modelling rely on strong assumptions, leaving it unclear when partial experimental observations support reduced descriptions of system dynamics. Here we show that symbolic regression (SR) provides a data-driven way to test whether, and how compactly, the dynamics of a signalling system coarse-grain over the measured variables, and, when they do, infers mechanistically interpretable models. In synthetic enzyme systems, SR recovers Michaelis-Menten kinetics for the two-step mechanism and under three-step extensions. As data quality is degraded, SR simplifies toward effective kinetic laws while preserving correct theoretical limits. Applied to published time-resolved ERK phosphorylation data, SR identifies compact phospho-ERK rate laws in selected cancer-relevant gene overexpression contexts, yielding interpretable kinetic effects. A sparse neural ODE baseline requires few inputs where SR succeeds, but on average more where it fails, indicating that, where a reduced model is learnable at all, SR failure is associated with more complex dynamics that a simple mathematical model cannot describe. Together, these findings establish symbolic regression as a way to test when a compact coarse-grained description is warranted, generating hypotheses where one holds and motivating potential new measurements where it does not.