# Weaviate

本页面介绍如何在LangChain中使用Weaviate生态系统。

什么是Weaviate？

**Weaviate简介：**
- Weaviate是一种开源的类型为向量搜索引擎的数据库。
- Weaviate允许您以类似于类属性的方式存储JSON文档，同时将机器学习向量附加到这些文档中，以在向量空间中表示它们。
- Weaviate可以独立使用（即带上您的向量），也可以使用各种模块为您进行向量化并扩展核心功能。
- Weaviate有一个GraphQL-API，可以轻松访问您的数据。
- 我们旨在将您的向量搜索设置投入生产，以便在短短的毫秒内进行查询（查看我们的[开源基准测试](https://weaviate.io/developers/weaviate/current/benchmarks/)，以确定Weaviate是否适合您的用例）。
- 在五分钟内了解Weaviate的[基础入门指南](https://weaviate.io/developers/weaviate/current/core-knowledge/basics.html)。
Weaviate是一个低延迟的向量搜索引擎，支持不同的媒体类型（文本，图像等），提供语义搜索、问答提取、分类、可定制模型（PyTorch/TensorFlow/Keras）等功能。 Weaviate是使用Go从头开始构建的，可以存储对象和向量，并允许将向量搜索与结构化过滤和云原生数据库的容错性相结合。可以通过GraphQL、REST和各种客户端编程语言访问它。

## 安装和设置
- 使用`pip install weaviate-client`安装Python SDK。
## 封装器

### VectorStore

存在一个围绕Weaviate索引的封装器，允许您将其用作向量存储，
用于语义搜索或示例选择。

导入此向量存储：
```python
from langchain.vectorstores import Weaviate
```
如需更详细的Weaviate封装说明，请参阅[此notebook](../modules/indexes/vectorstores/examples/weaviate.ipynb)。