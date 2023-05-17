# Google搜索包装器

本页面介绍如何在LangChain中使用Google搜索API。它分为两部分：安装和设置，以及特定的Google搜索包装器的参考。

## 安装和设置
- 使用`pip install google-api-python-client`安装所需的依赖项。
- 按照[这些说明](https://stackoverflow.com/questions/37083058/programmatically-searching-google-in-python-using-custom-search)设置自定义搜索引擎。
- 从上一步中获取API密钥和自定义搜索引擎ID，并将它们分别设置为环境变量`GOOGLE_API_KEY`和`GOOGLE_CSE_ID`。

## 包装器

### 使用工具类

存在一个名为GoogleSearchAPIWrapper的实用工具类，它包装了该API。要导入此实用程序：
```python
from langchain.utilities import GoogleSearchAPIWrapper
```
若需更详细的操作步骤，请查看[此notebook](../modules/agents/tools/examples/google_search.ipynb)。

### 工具

您也可以轻松地将此包装器加载为工具（与Agent一起使用）。
您可以使用以下命令完成此操作：
```python
from langchain.agents import load_tools
tools = load_tools(["google-search"])
```
更多信息，请参阅 [这个页面](../modules/agents/tools/getting_started.md)。