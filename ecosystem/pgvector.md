# PGVector

本页面介绍如何在LangChain中使用Postgres [PGVector](https://github.com/pgvector/pgvector)生态系统。
它分为两部分：安装和设置，并提供了特定PGVector包装器的参考。

## 安装
- 使用`pip install pgvector`命令安装Python包。

## 设置
1. 第一步是创建一个已安装`pgvector`扩展的数据库。 

    按照[PGVector Installation Steps](https://github.com/pgvector/pgvector#installation)的步骤安装数据库和扩展。使用Docker镜像最方便。

## 包装器

### VectorStore

存在一个Postgres向量数据库的包装器，允许您将其用作向量存储，无论是用于语义搜索还是用于示例选择。

导入此向量存储：
```python
from langchain.vectorstores.pgvector import PGVector
```
### 使用说明

若需进一步了解PGVector Wrapper，请查看[该notebook](../modules/indexes/vectorstores/examples/pgvector.ipynb)以获取更详细的操作步骤。