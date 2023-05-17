# SerpAPI

本页介绍如何在LangChain中使用SerpAPI搜索API。
它分为两部分：安装和设置，以及对特定SerpAPI包装器的引用。

## 安装和设置
- 使用`pip install google-search-results`命令安装所需的依赖项。
- 获取SerpAPI API密钥，并将其设置为环境变量(`SERPAPI_API_KEY`)。

## 包装器

### 实用工具

存在一个SerpAPI实用程序，可以包装此API。要导入此实用程序：
```python
from langchain.utilities import SerpAPIWrapper
```
如需更详细的包装器说明，请参阅[此笔记本](../modules/agents/tools/examples/serpapi.ipynb)。

### 工具

您还可以将此包装器作为工具轻松加载（与代理一起使用）。
您可以这样做：
```python
from langchain.agents import load_tools
tools = load_tools(["serpapi"])
```
更多信息请查看[此页面](../modules/agents/tools/getting_started.md)。