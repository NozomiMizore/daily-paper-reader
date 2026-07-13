---
title: Tokenizing single-cell transcriptomes as a native language for large language models
title_zh: 将单细胞转录组标记为大语言模型的母语
authors: "Xiao, C., Ding, Y., Bian, H., Chen, Y., Wei, L., Zhang, X."
date: 2026-07-11
pdf: "https://www.biorxiv.org/content/10.1101/2025.10.22.684047v2.full.pdf"
tags: ["query:virtual-cell"]
score: 6.0
evidence: 将单细胞转录组标记化为LLM可处理的形式，可能用于扰动响应预测
tldr: 大语言模型需将数据表示为离散token才能处理，但单细胞转录组是连续高维分子谱，难以直接融入LLM。本研究提出CellTok，将转录组转换为紧凑的细胞token序列，嵌入预训练LLM词汇表，使细胞、文本、群体等能在同一自回归框架中处理。CellTok在细胞识别、群体解释、疾病状态推断、细胞通讯预测、发育轨迹建模和细胞状态生成等任务中表现优异，且提供上下文能提升性能。该方法将单细胞转录组转化为LLM的原生语言，为细胞与生物学知识的统一建模建立了新接口。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-22-684047-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1509, \"height\": 1404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-22-684047-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1503, \"height\": 891, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-22-684047-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1500, \"height\": 717, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-22-684047-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1174, \"height\": 730, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-22-684047-v2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1499, \"height\": 565, \"label\": \"Figure\"}]"
motivation: 单细胞转录组作为连续高维数据，无法被大语言模型直接处理，需要转化为离散token形式以融入LLM范式中。
method: CellTok将转录组表达谱编码为紧凑的细胞token序列，纳入预训练LLM词汇表，实现细胞、文本和群体数据的联合自回归建模。
result: CellTok在细胞识别、群体解释、疾病状态推断、细胞通讯预测、发育轨迹建模和状态生成等任务中均有效，且上下文提示能提升性能。
conclusion: 单细胞转录组可被转化为LLM的原生语言，为细胞数据与生物知识的统一接口奠定了基础。
---

## 摘要
大语言模型（LLM）能够处理多种形式的信息，只需将它们表示为共享序列空间中的标记。然而，单细胞转录组对LLM而言仍然是一种陌生的模态，因为它们是连续的高维分子图谱，而非离散的语言单元。在此，我们提出CellTok，一种标记化的单细胞语言建模方法，可将转录组图谱转换为紧凑的细胞标记序列，并将其整合到预训练LLM的词表中。通过将细胞表示为原生标记，CellTok使得细胞测量、文本指令、生物学背景以及多细胞群体能够在相同的自回归建模框架内共同处理。在多种任务中，CellTok使LLM能够识别单个细胞、解读同质和异质细胞群体、推断疾病相关细胞状态、预测细胞间通讯、建模发育轨迹以及生成细胞状态。此外，基于提示的实验表明，提供适当的生物学背景可提升性能，表明CellTok能够利用LLM知识和上下文推理来支持细胞数据解读。这些结果表明，单细胞转录组可以从一种陌生的分子模态转变为LLM的母语，从而在共享标记空间中建立用于建模细胞、群体和生物学知识的统一接口。

## Abstract
Large language models (LLMs) can process diverse forms of information once they are represented as tokens in a shared sequence space. However, single-cell transcriptomes remain a foreign modality to LLMs because they are continuous, high-dimensional molecular profiles rather than discrete linguistic units. Here, we propose CellTok, a tokenized single-cell language modeling approach that converts transcriptomic profiles into compact cellular token sequences and incorporates them into the vocabulary of a pretrained LLM. By representing cells as native tokens, CellTok enables cellular measurements, textual instructions, biological context, and multi-cell populations to be jointly processed within the same autoregressive modeling framework. Across diverse tasks, CellTok enable LLMs to recognize individual cells, interpret homogeneous and heterogeneous cell populations, infer disease-associated cellular states, predict cell-cell communication, model developmental trajectories, and generate cellular states. Moreover, prompt-based experiments show that providing appropriate biological context improves performance, indicating that CellTok can leverage LLM knowledge and contextual reasoning to support cellular data interpretation. These results demonstrate that single-cell transcriptomes can be transformed from a foreign molecular modality into a native language for LLMs, establishing a unified interface for modeling cells, populations, and biological knowledge in a shared token space.