# Llama.cpp

本文档介绍如何在LangChain中使用[llama.cpp](https://github.com/ggerganov/llama.cpp)。 它分为两个部分：安装和设置，以及对特定Llama-cpp包装器的引用。

## 安装和设置
- 使用 `pip install llama-cpp-python` 命令安装Python包。
- 根据[说明](https://github.com/ggerganov/llama.cpp)中的指示，下载其中一个[支持的模型](https://github.com/ggerganov/llama.cpp#description)并将其转换为llama.cpp格式。

## 包装器

### LLM

存在一个名为 LlamaCpp LLM 的包装器，您可以通过以下方式进行访问：
```python
from langchain.llms import LlamaCpp
```
更详细的步骤请参见 [此 Notebook](../modules/models/llms/integrations/llamacpp.ipynb)

### 嵌入

LlamaCpp 提供了一个嵌入（Embeddings）包装器，您可以通过以下方式进行访问：
```python
from langchain.embeddings import LlamaCppEmbeddings
```
如需更详细的介绍，请参阅[此笔记本](../modules/models/text_embedding/examples/llamacpp.ipynb)。