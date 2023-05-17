# Pinecone

此页面介绍如何在LangChain中使用Pinecone生态系统。 
它分为两部分：安装和设置以及特定Pinecone包装器的参考。

## 安装和设置
- 使用`pip install pinecone-client`安装Python SDK 

## 包装器

### VectorStore

存在一个Pinecone索引的包装器，允许您将其用作向量存储，
无论是用于语义搜索还是示例选择。

要导入此向量存储：
```python
from langchain.vectorstores import Pinecone
```
要详细了解Pinecone包装器，请参阅[此笔记本](../modules/indexes/vectorstores/examples/pinecone.ipynb)。