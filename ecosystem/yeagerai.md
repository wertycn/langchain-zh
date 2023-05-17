# Yeager.ai

本页面介绍如何使用[ Yeager.ai ](https://yeager.ai) 生成LangChain 工具和代理。

## 什么是Yeager.ai？
Yeager.ai是一个旨在简化创建人工智能代理和工具过程的生态系统。

它具有yAgents，一个无代码LangChain代理创建器，使用户能够轻松构建、测试和部署人工智能解决方案。利用LangChain框架，yAgents可以无缝集成各种语言模型和资源，适用于各个应用程序的开发人员、研究人员和人工智能爱好者。

## yAgents
低代码生成代理，旨在帮助您轻松构建、原型设计和部署Langchain工具。

### 如何使用？
```
pip install yeagerai-agent
yeagerai-agent
```
转换后的中文翻译如下：

前往 http://127.0.0.1:7860

此操作将安装必要的依赖项并在您的系统上设置yAgents。首次运行后，yAgents将创建一个 .env 文件，在其中您可以输入您的OpenAI API密钥。您也可以直接在Gradio界面的“设置”选项卡下完成此操作。

`OPENAI_API_KEY=<your_openai_api_key_here>`

我们推荐使用GPT-4，但如果问题分解得足够细，则该工具也可以与GPT-3一起使用。

### 使用yAgents创建和执行工具
yAgents使得创建和执行基于AI的工具变得轻而易举。以下是一个简要的流程概述：
1. 创建一个工具：要创建一个工具，请向yAgents提供一个自然语言提示。该提示应清楚地描述工具的目的和功能。例如：
`创建一个工具，返回第n个质数`
2. 将工具加载到工具包中：要将工具加载到yAgents中，请向yAgents提供一个命令。例如：
`将你刚刚创建的工具加载到你的工具包中`
3. 执行工具：要运行工具或代理，只需向yAgents提供包括工具名称和任何必需参数的命令即可。例如：`生成第50个质数`。

您可以在[此处](https://www.youtube.com/watch?v=KA5hCM3RaWE)查看它的演示视频。

随着您对yAgents的熟悉程度越来越高，您可以创建更高级的工具和代理来自动化您的工作并提高生产力。

更多信息，请参见[yAgents的Github](https://github.com/yeagerai/yeagerai-agent)或我们的[文档](https://yeagerai.gitbook.io/docs/general/welcome-to-yeager.ai)。