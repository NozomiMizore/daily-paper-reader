---
title: "Weak form Scientific Machine Learning for Systems Biology: A Tutorial on WENDy"
title_zh: 系统生物学的弱形式科学机器学习：WENDy教程
authors: "Heitzman-Breen, N., Lyons, R., Jain, P., Jolly, M. K., Bortz, D. M."
date: 2026-07-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.02.735880v1.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 细胞状态转变ODE模型的参数估计
tldr: 系统生物学中常采用机械ODE模型，但参数估计受限于噪声和稀疏数据。WENDy方法通过弱形式将模型方程与紧支撑检验函数积分，转化为协方差校正的回归问题，避免正向求解器。在逻辑方程背景和两个实际系统（糖酵解振荡器、上皮-间质细胞转换模型）上应用，成功估计了可解释的生物学参数及其不确定性。该方法为处理噪声和稀疏实验数据提供了高效鲁棒的参数估计工具。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-02-735880-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1348, \"height\": 866, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-02-735880-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1319, \"height\": 1044, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-02-735880-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1350, \"height\": 489, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-02-735880-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1229, \"height\": 563, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-02-735880-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1239, \"height\": 1007, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-02-735880-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1346, \"height\": 309, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-02-735880-v1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1424, \"height\": 1051, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-02-735880-v1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1497, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-02-735880-v1/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1277, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-02-735880-v1/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1291, \"height\": 501, \"label\": \"Table\"}]"
motivation: 现有ODE参数估计依赖正向求解器，对噪声和稀疏数据敏感，亟需无求解器方法。
method: 利用弱形式积分模型方程与紧支撑检验函数，并引入协方差校正以处理噪声，构建回归问题。
result: 在糖酵解振荡器和上皮-间质细胞转换模型上，从噪声稀疏数据中估计出可解释参数及不确定性。
conclusion: WENDy方法无需正向求解器即可稳健估计参数，适用于系统生物学实验数据。
---

## 摘要
机理常微分方程模型广泛应用于系统生物学中，用于表示生化网络、群体动力学、细胞状态转变及其他生物过程；然而，其预测价值关键取决于从含噪声且通常稀疏的实验数据中准确估计参数。在本教程中，我们介绍弱形式非线性动力学估计（WENDy）方法，这是一种无需前向求解器的方法，通过将模型方程与紧支撑测试函数积分，将参数估计重新表述为协方差校正的弱形式回归问题。我们通过熟悉的逻辑斯谛方程视角介绍该方法的背景，并通过两个系统生物学实例展示该方法在真实实验数据上的应用：一个具有相对密集时间过程数据的糖酵解振荡器，以及一个具有多个实验重复的稀疏上皮-间充质细胞状态转变模型。最终，利用WENDy，我们为具有含噪声且有时稀疏可用实验数据的系统估计了带有不确定性的可解释生物参数。

## Abstract
Mechanistic ordinary differential equation models are widely used in systems biology to represent biochemical networks, population dynamics, cell-state transitions, and other biological processes; however, their predictive value depends critically on accurate parameter estimation from noisy and often sparse experimental data. In this tutorial, we present the Weak-form Estimation of Nonlinear Dynamics (WENDy) method as a forward-solver-free approach that reformulates parameter estimation as a covariance-corrected weak-form regression problem by integrating the model equations against compactly supported test functions. We present the background on the methodology through the lens of the familiar logistic equation, and we demonstrate applications of the method on real experimental data through two systems biology examples: a glycolytic oscillator with relatively dense time-course data and a sparse epithelial-mesenchymal cellstate transition model with multiple experimental replicates. Ultimately, using WENDy, we estimate interpretable biological parameters with uncertainty for systems with noisy and sometimes sparse available experimental data.