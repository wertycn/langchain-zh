# SearxNG搜索API

本页面介绍如何在LangChain中使用SearxNG搜索API。它分为两个部分：安装和设置，以及特定SearxNG API包装器的参考。

## 安装和设置

虽然可以将包装器与[公共searx实例](https://searx.space/)一起使用，但这些实例经常不允许API访问（请参见下面有关输出格式的注释），并且对请求的频率有限制。建议选择自托管实例。

### 自托管实例：

请参考[此页面](https://searxng.github.io/searxng/admin/installation.html)了解安装说明。

在安装SearxNG时，默认情况下唯一激活的输出格式是HTML格式。要使用API，需要激活“json”格式。可以通过将以下行添加到`settings.yml`文件来完成：
```yaml
search:
    formats:
        - html
        - json
```
您可以通过向API端点发出curl请求来确保API正在工作：

`curl -kLX GET --data-urlencode q='langchain' -d format=json http://localhost:8888`

这应该返回一个带有结果的JSON对象。


## 包装器

### 实用工具

为了使用包装器，我们需要向创建实例时传递SearxNG实例的主机，可以使用以下两种方法之一：
    1. 使用命名参数`searx_host`创建实例。
    2. 导出环境变量`SEARXNG_HOST`。

您可以使用包装器从SearxNG实例中获取结果。
```python
from langchain.utilities import SearxSearchWrapper
s = SearxSearchWrapper(searx_host="http://localhost:8888")
s.run("what is a large language model?")
```
### 工具

您也可以将此包装器作为工具加载（用于与代理一起使用）。

您可以使用以下方法完成此操作：
```python
from langchain.agents import load_tools
tools = load_tools(["searx-search"],
                    searx_host="http://localhost:8888",
                    engines=["github"])
```
请注意，我们可以选择性地传递自定义引擎以供使用。

如果您想要获得包含元数据的结果，例如*json*格式，您可以使用：
```python
tools = load_tools(["searx-search-results-json"],
                    searx_host="http://localhost:8888",
                    num_results=5)
```
如需更多工具相关信息，请参见[此页面](../modules/agents/tools/getting_started.md)。