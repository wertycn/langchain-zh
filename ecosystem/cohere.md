# Cohere

本页面介绍如何在LangChain中使用Cohere生态系统，主要分为两个部分：安装和设置，以及特定Cohere封装的引用。

## 安装和设置
- 使用 `pip install cohere` 安装Python SDK。
- 获取Cohere API密钥，并将其设置为环境变量（`COHERE_API_KEY`）。

## 封装
### LLM
LangChain中存在Cohere LLM封装，可以通过以下方式访问：
```python
from langchain.llms import Cohere
```
### 嵌入

LangChain已经提供了一个Cohere Embeddings的包装器，您可以使用以下方式访问：
```python
from langchain.embeddings import CohereEmbeddings
```
如需更详细的步骤，请参见 [此notebook](../modules/models/text_embedding/examples/cohere.ipynb) 。