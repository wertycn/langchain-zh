# OpenAI

本页面介绍如何在LangChain中使用OpenAI生态系统。
它分为两个部分：安装和设置，以及特定OpenAI包装器的引用。

## 安装和设置
- 使用`pip install openai`命令安装Python SDK。
- 获取OpenAI API密钥并将其设置为环境变量(`OPENAI_API_KEY`)。
- 如果您想使用OpenAI的tokenizer(仅适用于Python 3.9+)，请使用`pip install tiktoken`进行安装。

## 包装器

### LLM

存在一个OpenAI LLM包装器，您可以使用以下命令进行访问：
```python
from langchain.llms import OpenAI
```
如果您正在使用在Azure上托管的模型，则应该使用不同的封装程序：
```python
from langchain.llms import AzureOpenAI
```
要详细了解Azure封装的步骤，请参见[此notebook](../modules/models/llms/integrations/azure_openai_example.ipynb)。

### 嵌入

有一个OpenAI嵌入包装器，您可以通过以下方式访问：
```python
from langchain.embeddings import OpenAIEmbeddings
```
如果您需要更详细的介绍，请参阅[此notebook](../modules/models/text_embedding/examples/openai.ipynb)


### 分词器

您可以在多个地方使用`tiktoken`分词器。默认情况下，它用于计算OpenAI LLMs的令牌数。

您还可以在拆分文档时使用它来计算令牌数。
```python
from langchain.text_splitter import CharacterTextSplitter
CharacterTextSplitter.from_tiktoken_encoder(...)
```
如果您需要更详细的步骤，请参阅[此笔记本](../modules/indexes/text_splitters/examples/tiktoken.ipynb)

### 内容审核
您也可以使用以下方式访问OpenAI内容审核终端：
```python
from langchain.chains import OpenAIModerationChain
```
有关更详细的操作步骤，请参阅 [此笔记本](../modules/chains/examples/moderation.ipynb)。