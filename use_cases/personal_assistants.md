# Agents

> [概念指南](https://docs.langchain.com/docs/use-cases/personal-assistants)

代理人可以用于各种任务。代理人结合了语言模型的决策能力和工具，以创建一个可以代表您执行和实现解决方案的系统。
在继续阅读之前，强烈建议您阅读`agent`模块中的文档，以更好地了解与代理人相关的概念。
特别地，在继续阅读之前，您应该熟悉`agent`、`tool`和`agent executor`抽象。

- [代理人文档](../modules/agents.rst)（用于与外部世界交互）

## 创建您自己的代理人

阅读完上述文档后，您应该准备创建自己的代理人了。那具体涉及到什么？

以下是我们推荐的创建自己代理人的步骤：

### 步骤 1：创建工具

代理人的功能很大程度上由它们可以使用的工具来定义。
如果您希望代理执行特定任务，您必须让它具备正确的工具。
我们在LangChain中提供了许多本地工具，因此您首先应该查看它们是否满足您的需求。
但是，我们还可以轻松定义自定义工具，因此如果您需要自定义工具，绝对应该这样做。

### （可选）第二步：修改代理

内置的LangChain代理类型是为在通用情况下良好运作而设计的，
但您可以通过修改代理实现来提高性能。您可以使用以下几种方法：

1. 修改基本提示。这可用于向代理提供更多上下文，以指示代理如何行事，等等。
2. 修改输出解析器。如果代理无法解析语言模型输出，则必须进行修改。

### （可选）第三步：修改代理执行器

通常不需要执行此步，因为这是相当通用的逻辑。
您想要修改这一步的原因可能包括添加不同的停止条件或处理错误
## 示例

一些典型的代理人示例包括：

- [AI插件](agents/custom_agent_with_plugin_retrieval.ipynb)：一个能够使用所有AI插件的代理人实现。
- [Plug-and-PlAI（插件数据库）](agents/custom_agent_with_plugin_retrieval_using_plugnplai.ipynb)：一个能够从PlugNPlAI检索并使用所有AI插件的代理人实现。
- [Wikibase代理人](agents/wikibase_agent.ipynb)：一个与Wikibase交互的代理人实现。
- [销售GPT](agents/sales_agent_with_context.ipynb)：这个笔记演示了一个上下文感知的AI销售代理人的实现。
- [多模态输出代理人](agents/multi_modal_output_agent.ipynb）：一个能够生成文本和图像的多模态输出代理人实现。