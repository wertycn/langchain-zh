# AtlasDB

本页面涵盖了如何在LangChain中使用Nomic的Atlas生态系统的内容。
它分为两个部分：安装和设置，然后是对特定Atlas包装器的引用。

## 安装和设置
- 使用 `pip install nomic` 命令安装Python包。
- Nomic也包含在langchain poetry extras的`poetry install -E all` 中。

## 包装器

### VectorStore

存在一个围绕Atlas神经数据库的包装器，允许您将其用作向量存储器。
这个向量存储器还为您提供了对底层AtlasProject对象的完全访问，使您可以使用各种Atlas地图交互，例如批量标记和自动主题建模。
请查看[Atlas文档](https://docs.nomic.ai/atlas_api.html)以获取更详细的信息。

要导入此向量存储器：
```python
from langchain.vectorstores import AtlasDB
```
如需更详细的AtlasDB包装器使用说明，请参阅[此笔记本](../modules/indexes/vectorstores/examples/atlas.ipynb)。