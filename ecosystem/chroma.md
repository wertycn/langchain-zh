# Chroma

本页介绍如何在LangChain中使用Chroma生态系统。
它分为两个部分：安装和设置以及特定Chroma包装器的引用。

## 安装和设置
- 使用 `pip install chromadb` 安装Python包

## 包装器

### VectorStore

存在一个围绕Chroma向量数据库的包装器，可以将其用作向量库，无论是用于语义搜索还是示例选择。

要导入此向量库:
```python
from langchain.vectorstores import Chroma
```
针对更详细的 Chroma 包装器介绍，您可以参考[此笔记本](../modules/indexes/vectorstores/getting_started.ipynb)。