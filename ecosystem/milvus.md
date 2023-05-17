# Milvus


本页面介绍如何在LangChain中使用Milvus生态系统。它分为两个部分：安装设置和特定的Milvus包装器库引用。

## 安装和设置
- 使用`pip install pymilvus`安装Python SDK

## 包装器库

### VectorStore

存在一个围绕Milvus索引的包装器库，使您可以将它用作矢量存储，无论是用于语义搜索还是示例选择。

要导入此矢量存储：
```python
from langchain.vectorstores import Milvus
```
更详细教程，请参考 [此notebook](../modules/indexes/vectorstores/examples/milvus.ipynb) 关于 Miluvs 包装器的使用。