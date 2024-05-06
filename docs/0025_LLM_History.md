---
Title | LLM History
-- | --
Created @ | `2024-05-06T09:10:41Z`
Updated @| `2024-05-06T09:10:41Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/csc/issues/25)

---
# 发展历程

- SLM 统计语言模型主要被用于（或辅助用于）解决一些特定任务，主要以信息检索、文本分类、语音识别等传统任务为主。
- NLM 神经语言模型专注于学习任务无关的语义表征，旨在减少人类特征工程的工作量，可以大范围扩展语言模型可应用的任务。
- PLM 预训练语言模型加强了语义表征的上下文感知能力，并且可以通过下游任务进行微调，能够有效提升下游任务（主要局限于自然语言处理任务）的性能。
- LLM 大语言模型的任务求解能力有了显著提升，能够不再依靠下游任务数据的微调进行通用任务的求解。

![image](https://github.com/junxnone/csc/assets/2216970/02f05c68-252d-424d-98c7-8184e109fde8)

## SLM

- 1990s SLM - `Statistical Language Model` - 统计语言模型
- 使用 `马尔可夫假设 Markov Assumption` 建立语言序列的预测模型
- `n-gram` n 元 语言模型随着 n 的增加，需要估计的转移概率项数会指数级增长，面临 `维数灾难(Curse of Dimensionality)`  
  - 引出语言模型平滑策略
    - 回退估计 `Back-off Estimation`
    - 古德-图灵估计 `Good-Turing Estimation`
- 对于高阶上下文刻画能力弱，无法精确建模复杂高阶语义关系

## NLM

- 2013 NLM - `Neural Language Model` 神经语言模型
- RNN - `Recurrent Neural Networks` 循环神经网络
- `Distributed Word Representation` -> Word Embedding 词嵌入
- word2vec


## PLM

- 2018 PLM - `Pre-Trained Language Model` 预训练语言模型
- ELMo -> biLSTM
- Transformer -> BERT/GPT



## LLM
- Large Language Model 大语言模型
- Scaling Law 扩展法则 - 增加模型参数规模或数据规模会带来下游任务的模型性能提升
- Emergent Abilities 涌现能力 - 大模型具有小模型不具有的能力 GPT2 -> GPT3
- 复杂任务的求解
