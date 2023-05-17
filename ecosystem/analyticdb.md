# AnalyticDB

本页介绍如何在LangChain中使用AnalyticDB生态系统。

### VectorStore

在LangChain中，存在一个封装了AnalyticDB的向量存储库，使您能够将其用作向量库，无论是用于语义搜索还是示例选择。

您可以通过以下方式导入此向量存储库：
```python
from langchain.vectorstores import AnalyticDB
```
如果您需要更详细的步骤指导，可以参考[这个notebook](../modules/indexes/vectorstores/examples/analyticdb.ipynb)，其中包含有关AnalyticDB包装器的详细介绍。