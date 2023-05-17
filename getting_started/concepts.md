# 概念

这些是开发LLM应用程序时常用的概念和术语。
其中列出了引入这些概念的外部论文或来源，
以及LangChain中使用这些概念的地方。

## 思考链

`思考链（CoT）`是一种提示技术，旨在鼓励模型生成一系列中间推理步骤。
一个更不正式的方法是在提示中包含“让我们逐步思考”。

- [Chain-of-Thought 论文](https://arxiv.org/pdf/2201.11903.pdf)
- [Step-by-Step 论文](https://arxiv.org/abs/2112.00114)

## 行动计划生成

`行动计划生成`是一种使用语言模型生成要执行的行动的提示技术。
这些行动的结果可以反馈回语言模型，生成随后的行动。

- [WebGPT 论文](https://arxiv.org/pdf/2112.09332.pdf)
- [SayCan 论文](https://say-can.github.io/assets/palm_saycan.pdf)

## ReAct
`ReAct` 是一种结合思路链提示和行动计划生成的提示技术。它促使模型考虑要采取的行动，然后采取相应的行动。

- [论文](https://arxiv.org/pdf/2210.03629.pdf)
- [LangChain 示例](../modules/agents/agents/examples/react.ipynb)

## 自问自答技术

`自问自答技术` 是在思路链提示的基础上构建的一种提示方法。在这种方法中，模型明确地通过外部搜索引擎询问自己的跟进问题，然后得到答案。

- [论文](https://ofir.io/self-ask.pdf)
- [LangChain 示例](../modules/agents/agents/examples/self_ask_with_search.ipynb)

## 提示链

`提示链` 是将多个LLM调用结合起来，将每一步的输出作为下一步的输入。

- [PromptChainer 论文](https://arxiv.org/pdf/2203.06566.pdf)
- [Language Model Cascades](https://arxiv.org/abs/2207.10342)
- [ICE Primer 书籍](https://primer.ought.org/)
- [Socratic Models](https://socraticmodels.github.io/)

## 文化密码技术
`Memetic Proxy` 会鼓励 LLM 在特定情境下给出某种回应。例如，在学生和教师之间的对话中。

- [论文（英文）](https://arxiv.org/pdf/2102.07350.pdf)

## 自我一致性

`自我一致性` 是一种解码策略，它采样多种推理路径，并选择最一致的答案。与`链式思考提示`结合使用时效果最佳。

- [论文（英文）](https://arxiv.org/pdf/2203.11171.pdf)


## Inception 

`Inception`，又称`第一人称指导`，通过包含模型响应的开头来鼓励模型以某种方式思考。

- [示例（英文）](https://twitter.com/goodside/status/1583262455207460865?s=20&t=8Hz7XBnK1OF8siQrxxCIGQ)


## MemPrompt

`MemPrompt` 维护错误和用户反馈的记忆，并使用它们来防止重复错误。

- [论文（英文）](https://memprompt.com/)