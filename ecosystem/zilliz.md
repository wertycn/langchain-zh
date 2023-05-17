# Zilliz

本页面介绍如何在LangChain中使用Zilliz Cloud生态系统。Zilliz使用Milvus集成。它分为两个部分：安装和设置，以及特定Milvus包装器的引用。

## 安装和设置
- 使用 `pip install pymilvus` 安装Python SDK

## 包装器
### VectorStore
存在一个Zilliz索引的包装器，允许您将其用作矢量库，无论是用于语义搜索还是示例选择。

要导入此矢量库，请使用以下代码：
```python
from langchain.vectorstores import Milvus
```
如果您需要更详细的Miluvs包使用说明，请查看[此笔记本](../modules/indexes/vectorstores/examples/zilliz.ipynb)。