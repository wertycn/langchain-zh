# Qdrant

本页面说明如何在LangChain中使用Qdrant生态系统。
它分为两个部分：安装和设置，以及对特定Qdrant包装器的引用。

## 安装和设置
- 使用`pip install qdrant-client`安装Python SDK。

## 包装器

### VectorStore

存在一个围绕Qdrant索引的包装器，使您可以将其用作矢量存储，无论是用于语义搜索还是示例选择。

要导入此vectorstore：
```python
from langchain.vectorstores import Qdrant
```
想要更加详细地了解Qdrant包装器的使用，请参考[此笔记本](../modules/indexes/vectorstores/examples/qdrant.ipynb)。