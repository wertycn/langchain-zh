# Tair

本页面介绍如何在LangChain中使用Tair生态系统。

## 安装与设置

使用`pip install tair`命令安装Tair Python SDK。

## 包装器

### VectorStore

TairVector现在已经支持了一个包装器，可以作为向量存储使用，用于语义搜索或示例选择。

要导入这个向量存储：
```python
from langchain.vectorstores import Tair
```
要了解更详细的Tair封装包操作步骤，请参见[此笔记本](../modules/indexes/vectorstores/examples/tair.ipynb)。