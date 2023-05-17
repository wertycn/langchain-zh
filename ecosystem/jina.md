# Jina

本页介绍如何在LangChain中使用Jina生态系统。
它分为两个部分：安装和设置，以及特定Jina包装器的参考。

## 安装和设置
- 使用 `pip install jina` 安装Python SDK
- 从 [此处](https://cloud.jina.ai/settings/tokens) 获取Jina AI Cloud授权令牌，并将其设置为环境变量(`JINA_AUTH_TOKEN`)

## 包装器

### 嵌入

存在一个Jina嵌入包装器，您可以使用以下命令访问：
```python
from langchain.embeddings import JinaEmbeddings
```
如需更详细的步骤说明，请参阅[此笔记本](../modules/models/text_embedding/examples/jina.ipynb)。