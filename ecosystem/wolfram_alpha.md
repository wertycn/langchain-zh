# Wolfram Alpha API包装器

本页面介绍如何在LangChain中使用Wolfram Alpha API。分为两个部分：安装和设置，以及引用特定的Wolfram Alpha包装器。

## 安装和设置
- 使用`pip install wolframalpha`安装所需的库
- 前往wolfram alpha网站，并注册开发者账户[点击这里](https://developer.wolframalpha.com/)
- 创建一个应用程序，并获取您的APP ID
- 将您的APP ID设置为环境变量`WOLFRAM_ALPHA_APPID`

## 包装器

### 实用工具

有一个WolframAlphaAPIWrapper实用程序可以包装这个API。要导入此实用程序：
```python
from langchain.utilities.wolfram_alpha import WolframAlphaAPIWrapper
```
如果您需要更详细的说明，请查看[此notebook](../modules/agents/tools/examples/wolfram_alpha.ipynb)。

### 工具

您还可以将此封装器作为工具轻松加载（用于与代理程序一起使用）。通过以下方式即可实现：
```python
from langchain.agents import load_tools
tools = load_tools(["wolfram-alpha"])
```
要了解更多信息，请访问[此页面](../modules/agents/tools/getting_started.md)。