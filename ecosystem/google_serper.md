# Google Serper 包装器

本页面介绍如何在LangChain中使用[Serper](https://serper.dev) Google搜索API。 Serper是一个低成本的Google搜索API，可用于从Google搜索中添加答案框、知识图和有机搜索结果数据。本教程将分为两个部分：设置和特定Google Serper包装器的引用。

## 设置

- 打开[serper.dev](https://serper.dev) 并注册一个免费账号 
- 获取API密钥并将其设置为环境变量 (`SERPER_API_KEY`)

## 包装器

### 工具

提供了一个GoogleSerperAPIWrapper工具来包装这个API。导入此工具的方法如下：
```python
from langchain.utilities import GoogleSerperAPIWrapper
```
您可以将它作为Self Ask链的一部分使用：
```python
from langchain.utilities import GoogleSerperAPIWrapper
from langchain.llms.openai import OpenAI
from langchain.agents import initialize_agent, Tool
from langchain.agents import AgentType

import os

os.environ["SERPER_API_KEY"] = ""
os.environ['OPENAI_API_KEY'] = ""

llm = OpenAI(temperature=0)
search = GoogleSerperAPIWrapper()
tools = [
    Tool(
        name="Intermediate Answer",
        func=search.run,
        description="useful for when you need to ask with search"
    )
]

self_ask_with_search = initialize_agent(tools, llm, agent=AgentType.SELF_ASK_WITH_SEARCH, verbose=True)
self_ask_with_search.run("What is the hometown of the reigning men's U.S. Open champion?")
```
#### 输出
```
Entering new AgentExecutor chain...
 Yes.
Follow up: Who is the reigning men's U.S. Open champion?
Intermediate answer: Current champions Carlos Alcaraz, 2022 men's singles champion.
Follow up: Where is Carlos Alcaraz from?
Intermediate answer: El Palmar, Spain
So the final answer is: El Palmar, Spain

> Finished chain.

'El Palmar, Spain'
```
如需更详细的封装指南，请参阅[此笔记本](../modules/agents/tools/examples/google_serper.ipynb)。

### 工具

您还可以轻松地将此封装程序加载为工具（用于与代理一起使用）。
您可以使用以下方法实现：
```python
from langchain.agents import load_tools
tools = load_tools(["google-serper"])
```
更多信息，请参见[此页面](../modules/agents/tools/getting_started.md)。