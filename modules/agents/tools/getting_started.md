# 入门指南

工具是智能体与世界进行交互的功能。这些工具可以是通用实用工具（例如搜索），其他链，甚至是其他智能体。

目前，可以使用以下代码片段加载工具：
```python
from langchain.agents import load_tools
tool_names = [...]
tools = load_tools(tool_names)
```
有些工具（如 chains、agents）可能需要一个基础的LLM来初始化使用。
在这种情况下，你可以传递一个LLM：

```python
from langchain.agents import load_tools
tool_names = [...]
llm = ...
tools = load_tools(tool_names, llm=llm)
```
下面是所有支持的工具及相关信息的列表：

- 工具名称：LLM用于指代该工具的名称。
- 工具描述：传递给LLM的工具描述。
- 注意事项：不传递给LLM的工具的注意事项。
- 需要LLM：此工具是否需要初始化LLM。
- （可选）额外参数：初始化此工具所需要的额外参数。

## 工具列表

**python_repl**

- 工具名称：Python REPL
- 工具描述：Python shell。用于执行Python命令。输入应为有效的Python命令。如果您期望输出，则应该将其打印出来。
- 注意事项：维护状态。
- 需要LLM：否

**serpapi**

- 工具名称：搜索引擎
- 工具描述：搜索引擎。在需要回答关于当前事件的问题时非常有用。输入应为搜索查询。
- 注意事项：调用Serp API，然后解析结果。
- 需要LLM：否

**wolfram-alpha**

- 工具名称：Wolfram Alpha
- 工具描述：Wolfram Alpha搜索引擎。可用于回答有关数学、科学、技术、文化、社会和日常生活的问题。输入应该是一个搜索查询。
- 注意事项：调用Wolfram Alpha API，然后解析结果。
- 需要LLM：否
- 额外参数： "wolfram_alpha_appid"：Wolfram Alpha应用程序ID。

**requests**

- 工具名称：请求
- 工具描述：访问互联网的门户。当您需要从网站获取特定内容时，请使用此选项。输入应该是一个特定的URL，输出将是该页面上的所有文本。
- 注意事项：使用Python requests模块。
- 需要LLM：否

**终端**

- 工具名称：终端
- 工具描述：在终端中执行命令。输入应该是有效的命令，输出将是运行该命令时的任何输出。
- 注意事项：使用子进程执行命令。
- 需要LLM：否

**PAL-MATH**

- 工具名称：PAL-MATH
- 工具介绍：一种优秀的语言模型，能够解决复杂的单词数学问题。输入应该是一个完整的单词化难度较大的数学问题。
- 备注：基于 [这篇论文](https://arxiv.org/pdf/2211.10435.pdf)。
- 需要LLM：是

**pal-colored-objects**

- 工具名称：PAL-COLOR-OBJ
- 工具介绍：一种奇妙的语言模型，能够理解对象的位置和颜色属性。 输入应该是一个完整的难度较大的推理问题。确保包含所有关于对象和您想回答的最终问题的信息。
- 备注：基于[这篇论文](https://arxiv.org/pdf/2211.10435.pdf)。
- 需要LLM：是

**llm-math**

- 工具名称：计算器
- 工具介绍：用于回答数学问题。
- 备注：`LLMMath`链的一个实例。
- 需要LLM：是

**open-meteo-api**

- 工具名称：Open Meteo API
- **open-meteo-api**

  - 工具描述：当您想从OpenMeteo API获取天气信息时非常有用。输入应为该API可以回答的自然语言问题。
  - 注意事项：是与 Open Meteo API（`https://api.open-meteo.com/`）建立自然语言连接，具体地说是 `/v1/forecast` 终端点。
  - 需要LLM：是

- **news-api**

  - 工具名称：新闻API
  - 工具描述：当您想获取当前新闻故事的头条信息时，请使用此工具。输入应为该API可以回答的自然语言问题。
  - 注意事项：是与 News API（`https://newsapi.org`）建立自然语言连接，具体地说是 `/v2/top-headlines` 终端点。
  - 需要LLM：是
  - 额外参数：`news_api_key`（您的API密钥以访问此终端点）

- **tmdb-api**

  - 工具名称：TMDB API
  - 工具描述：当您想从The Movie Database获取信息时非常有用。输入应为该API可以回答的自然语言问题。
- 注意事项：连接到 TMDB API (`https://api.themoviedb.org/3`) 的自然语言接口，具体包括 `/search/movie` 终端节点。
- 需要 LLM：是
- 额外参数：`tmdb_bearer_token`（用于访问此终端节点的 Bearer Token，注意这与 API 密钥不同）

**google-search**

- 工具名称：搜索
- 工具描述：Google 搜索的封装器。当您需要回答有关当前事件的问题时非常有用。输入应该是一个搜索查询。
- 注意事项：使用 Google 自定义搜索 API。
- 需要 LLM：否
- 额外参数：`google_api_key`，`google_cse_id`
- 有关更多信息，请参见 [此页面](../../../ecosystem/google_search.md)。

**searx-search**

- 工具名称：搜索
- 工具描述：SearxNG 元搜索引擎的封装器。输入应该是一个搜索查询。
- 注意事项：SearxNG 很容易部署自托管。它是 Google 搜索的一个良好的隐私友好的替代品。使用 SearxNG API。
- 需要 LLM：否
- 额外参数：`searx_host`

**google-serper**
- 工具名称：搜索
- 工具描述：一种低成本的Google搜索API。 当您需要回答关于时事的问题时非常有用。 输入应为搜索查询。
- 注意：调用[serper.dev](https://serper.dev) Google搜索API，然后解析结果。
- 需要LLM：否
- 额外参数：`serper_api_key`
- 有关更多信息，请参见[此页面](../../../ecosystem/google_serper.md)

**维基百科**

- 工具名称：维基百科
- 工具描述：维基百科的封装。 当您需要回答关于人物、地点、公司、历史事件或其他主题的一般问题时非常有用。 输入应为搜索查询。
- 注意：使用[wikipedia](https://pypi.org/project/wikipedia/) Python包调用MediaWiki API，然后解析结果。
- 需要LLM：否
- 额外参数：`top_k_results`

**播客API**

- 工具名称：播客API
- 工具描述：使用Listen Notes Podcast API搜索所有播客或剧集。输入应该是一个自然语言问题，该API可以回答。
- 备注：与Listen Notes Podcast API（`https://www.PodcastAPI.com`）的自然语言连接，特别是`/search/`终点。
- 需要LLM：是
- 额外参数：`listen_api_key`（访问此终点的API密钥）

**openweathermap-api**

- 工具名称：OpenWeatherMap
- 工具描述：OpenWeatherMap API的包装器。用于获取指定位置的当前天气信息。输入应该是一个位置字符串（例如London,GB）。
- 备注：连接到OpenWeatherMap API（https://api.openweathermap.org），特别是`/data/2.5/weather`终点。
- 需要LLM：否
- 额外参数：`openweathermap_api_key`（访问此终点的API密钥）