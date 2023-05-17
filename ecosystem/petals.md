# Petals

本页面介绍如何在LangChain中使用Petals生态系统。
它分为两个部分：安装和设置，以及特定Petals包装的参考。

## 安装和设置
- 使用 `pip install petals` 安装。
- 获取一个Hugging Face api密钥并将其设置为环境变量 (`HUGGINGFACE_API_KEY`)。

## 包装器

### LLM

有一个Petals LLM包装器可用，您可以通过以下方式访问它：
```python
from langchain.llms import Petals
```
