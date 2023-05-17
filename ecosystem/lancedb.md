# LanceDB

本页面介绍如何在LangChain中使用[LanceDB](https://github.com/lancedb/lancedb)。
它分为两部分：安装设置，以及特定LanceDB包装的引用。

## 安装和设置

- 使用 `pip install lancedb` 安装Python SDK

## 包装器

### VectorStore

有一个LanceDB数据库的包装器，允许您将其用作向量存储，
无论是用于语义搜索还是示例选择。

为了导入此向量存储：
```python
from langchain.vectorstores import LanceDB
```
要了解LanceDB包装器的更详细的步骤，请参见[此笔记本](../modules/indexes/vectorstores/examples/lancedb.ipynb)。