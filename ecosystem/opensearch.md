# OpenSearch

本页面介绍如何在LangChain内使用OpenSearch生态系统。
包括两个部分：安装和设置，以及对特定OpenSearch包装器的引用。

## 安装和设置
- 使用 `pip install opensearch-py` 命令安装Python包。

## 包装器

### VectorStore

提供了一个围绕OpenSearch向量数据库的包装器，使您可以将其用作语义搜索的向量存储库。支持使用Lucene、nmslib和faiss引擎进行近似向量搜索，或者使用痛点脚本和脚本评分函数进行暴力向量搜索。

要导入此向量存储库：
```python
from langchain.vectorstores import OpenSearchVectorSearch
```
如果需要更详细的OpenSearch封装步骤，请参考 [此notebook](../modules/indexes/vectorstores/examples/opensearch.ipynb)。