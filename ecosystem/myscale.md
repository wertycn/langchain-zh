# MyScale

本页介绍如何在LangChain中使用MyScale向量数据库。它分为两个部分: 安装和设置，以及对特定MyScale封装的引用。

使用MyScale，您可以管理结构化和非结构化（矢量化）数据，并使用SQL对两种类型的数据进行联合查询和分析。此外，MyScale的云本地OLAP架构，建立在ClickHouse之上，即使在大规模数据集上也能进行闪电般快速的数据处理。

## 介绍

[MyScale和高性能向量搜索概览](https://docs.myscale.com/en/overview/)

您现在可以在我们的SaaS上注册并 [开始一个集群](https://docs.myscale.com/en/quickstart/)！

如果您还对我们如何集成SQL和向量感兴趣，请参阅 [此文档](https://docs.myscale.com/en/vector-reference/) 以获取进一步的语法参考。
同时，我们还提供了[huggingface空间](https://huggingface.co/myscale)，并且有现场演示！他们能在瞬间内搜索数百万向量！

## 安装和设置
- 通过 `pip install clickhouse-connect` 安装Python SDK

### 设置环境变量

有两种设置myscale索引参数的方法：

1. 环境变量

    在运行应用程序之前，请使用`export`命令设置环境变量:
    `export MYSCALE_URL='<your-endpoints-url>' MYSCALE_PORT=<your-endpoints-port> MYSCALE_USERNAME=<your-username> MYSCALE_PASSWORD=<your-password> ...`

    您可以在我们的SaaS上轻松找到您的帐户、密码和其他信息。有关详细信息，请参阅[此文档](https://docs.myscale.com/zh/cluster-management/)
    `MyScaleSettings`下的每个属性都可以使用前缀`MYSCALE_`设置，大小写不敏感。

2. 使用参数创建`MyScaleSettings`对象
    ```python
    from langchain.vectorstores import MyScale, MyScaleSettings
    config = MyScaleSetting(host="<your-backend-url>", port=8443, ...)
    index = MyScale(embedding_function, config)
    index.add_documents(...)
    ```
## 封装器
支持的函数：
- `add_texts`
- `add_documents`
- `from_texts`
- `from_documents`
- `similarity_search`
- `asimilarity_search`
- `similarity_search_by_vector`
- `asimilarity_search_by_vector`
- `similarity_search_with_relevance_scores`

### VectorStore

存在一个包装器用于将 MyScale 数据库作为向量数据库来使用，无论是用于语义搜索还是示例检索。

要导入此 VectorStore：
```python
from langchain.vectorstores import MyScale
```
若要深入了解MyScale包装器，请参阅[此笔记本](../modules/indexes/vectorstores/examples/myscale.ipynb)。