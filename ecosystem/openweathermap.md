# OpenWeatherMap API

本页面介绍如何在LangChain中使用OpenWeatherMap API。
它分为两个部分：安装和设置，以及对特定的OpenWeatherMap API包装器的引用。

## 安装和设置

- 使用 `pip install pyowm` 安装必要的要求
- 前往 OpenWeatherMap 并注册一个账户，以获取API密钥[在此处](https://openweathermap.org/api/)
- 将您的API密钥设置为`OPENWEATHERMAP_API_KEY`环境变量

## 包装器

### Utility

存在一个OpenWeatherMapAPIWrapper实用程序，可包装这个API。要导入此实用程序：
```python
from langchain.utilities.openweathermap import OpenWeatherMapAPIWrapper
```
如需了解此包装程序的更详细说明，请参阅 [此笔记本](../modules/agents/tools/examples/openweathermap.ipynb)。

### 工具

您还可以轻松地将此包装程序作为工具加载（与代理一起使用）。
您可以使用以下命令完成此操作：
```python
from langchain.agents import load_tools
tools = load_tools(["openweathermap-api"])
```
有关更多信息，请参见[此页面](../modules/agents/tools/getting_started.md)。