# 自主智能体

自主智能体是设计为更长时间运行的智能体。您可以为它们设定一个或多个长期目标，它们会独立地执行这些目标。这些应用程序结合了工具使用和长期记忆。

目前，自主智能体还比较实验性，基于其他开源项目进行开发。通过在LangChain基元中实现这些开源项目，我们可以获得LangChain的好处，比如方便地切换和尝试多个LLMs，使用不同的矢量存储作为内存，和使用LangChain的工具集。

## Baby AGI（[原始仓库](https://github.com/yoheinakajima/babyagi)）

- [Baby AGI](autonomous_agents/baby_agi.ipynb)：作为LLM链实现BabyAGI的笔记本
- [带有工具的Baby AGI](autonomous_agents/baby_agi_with_agent.ipynb)：在上述笔记本的基础上构建，此示例将代理程序及其工具作为执行工具替代，使其能够实际采取行动。
## AutoGPT ([原始仓库](https://github.com/Significant-Gravitas/Auto-GPT))
- [AutoGPT](autonomous_agents/autogpt.ipynb): 在LangChain原语中实现AutoGPT的笔记本
- [WebSearch Research Assistant](autonomous_agents/marathon_times.ipynb): 展示如何使用AutoGPT加上特定工具作为研究助手，能够使用网络。

## MetaPrompt ([原始仓库](https://github.com/ngoodman/metaprompt))
- [Meta-Prompt](autonomous_agents/meta_prompt.ipynb): 在LangChain原语中实现Meta-Prompt的笔记本