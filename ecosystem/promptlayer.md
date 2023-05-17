# PromptLayer

本页面介绍如何在LangChain中使用[PromptLayer](https://www.promptlayer.com)。
包含两个部分：安装和设置，以及特定的PromptLayer包装器的引用。

## 安装和设置

如果您想使用PromptLayer：
- 安装promptlayer python库 `pip install promptlayer`
- 创建一个PromptLayer账户
- 创建一个API密钥，并将其设置为环境变量 (`PROMPTLAYER_API_KEY`)

## 包装器

### LLM

存在一个PromptLayer OpenAI LLM包装器，您可以使用下面的代码来访问。
```python
from langchain.llms import PromptLayerOpenAI
```
在初始化LLM时，如果要对您的请求进行标记，请使用参数 `pl_tags`。
```python
from langchain.llms import PromptLayerOpenAI
llm = PromptLayerOpenAI(pl_tags=["langchain-requests", "chatbot"])
```
如需获取PromptLayer请求的ID，需在实例化LLM时使用`return_pl_id`参数。
```python
from langchain.llms import PromptLayerOpenAI
llm = PromptLayerOpenAI(return_pl_id=True)
```
这将在使用`.generate`或`.agenerate`生成文本时，在`Generation`返回值的`generation_info`字段中加入PromptLayer请求ID。

例如：
```python
llm_results = llm.generate(["hello world"])
for res in llm_results.generations:
    print("pl request id: ", res[0].generation_info["pl_request_id"])
```
您可以使用PromptLayer请求ID向您的请求添加提示、分数或其他元数据。[在这里阅读更多相关信息](https://magniv.notion.site/Track-4deee1b1f7a34c1680d085f82567dab9)。

这个LLM与[OpenAI LLM](./openai.md)完全相同，不同之处在于：
- 所有您的请求都会记录在您的PromptLayer帐户中
- 您可以在初始化时添加`pl_tags`来标记您在PromptLayer上的请求
- 您可以在初始化时添加`return_pl_id`以返回PromptLayer请求ID，以便在[跟踪请求](https://magniv.notion.site/Track-4deee1b1f7a34c1680d085f82567dab9)时使用。

PromptLayer还为[`PromptLayerChatOpenAI`](../modules/models/chat/integrations/promptlayer_chatopenai.ipynb)和`PromptLayerOpenAIChat`提供了本地包装器。