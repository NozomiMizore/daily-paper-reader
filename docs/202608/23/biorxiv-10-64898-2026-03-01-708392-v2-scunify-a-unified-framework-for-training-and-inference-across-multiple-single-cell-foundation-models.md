---
title: "scUnify: a unified framework for training and inference across multiple single-cell foundation models"
title_zh: scUnify：一个用于跨多个单细胞基础模型训练与推理的统一框架
authors: "KIM, D., Hong, A., Jeong, K., KIM, K."
date: 2026-08-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.01.708392v2.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 面向多个单细胞基础模型的统一训练与推理框架，可支撑扰动响应等下游任务
tldr: 单细胞基础模型在软件需求、下游任务表现和适应策略上差异显著，导致系统比较与复用困难。为此提出scUnify框架，它在保留各模型所需数据处理流程的同时，将模型专属训练器、下游任务与参数高效微调等适应策略解耦为可复用组件。在五个scFM上，scUnify复现了原始推理和训练流程，并为模型原生任务接入多种PEFT方法；还通过新实现的可训练任务连接多个骨干和适应策略，验证了可扩展性。这使研究者能在统一工作流中系统比较不同组合，并将自定义任务推广到异构单细胞基础模型。
source: biorxiv
selection_source: fresh_fetch
motivation: 单细胞基础模型在软件需求和下游任务性能上差异大，阻碍系统比较与复用。
method: 提出scUnify框架，保留各骨干所需处理，将训练器、下游任务与适应策略解耦为可复用组件。
result: 在五个scFM上复现原始推理与训练流程，支持多种PEFT方法，并验证了自定义任务连接多骨干的可扩展性。
conclusion: 使研究者能在统一工作流中系统比较异构scFM组合，并扩展自定义任务。
---

## 摘要
单细胞基础模型（scFM）在软件要求以及跨下游任务和适配策略的性能上存在差异，使得比较和复用变得复杂。我们提出了scUnify，一个在保留每个骨干网络所需处理流程的同时，将模型专属训练器、下游任务和适配策略分离为可复用组件的框架。在五个scFM上，scUnify复现了原始推理和训练工作流，通过多种参数高效微调方法扩展了模型原生任务，并通过将新实现的自定义可训练任务连接到多个骨干网络和适配策略来展示其可扩展性。这些能力共同使研究人员能够在统一工作流中系统比较这些组合，并在异构scFM之间扩展自定义任务。

## Abstract
Single-cell foundation models (scFMs) differ in software requirements and performance across downstream tasks and adaptation strategies, complicating comparison and reuse. We present scUnify, a framework that preserves each backbone's required processing while separating model-specific trainers, downstream tasks, and adaptation strategies as reusable components. Across five scFMs, scUnify reproduced original inference and training workflows, extended model-native tasks with multiple parameter-efficient fine-tuning methods, and demonstrated extensibility by connecting a newly implemented custom trainable task to multiple backbones and adaptation strategies. Together, these capabilities enable researchers to systematically compare these combinations and extend custom tasks across heterogeneous scFMs within a common workflow.