# GooseAI

本页介绍如何在LangChain中使用GooseAI生态系统。
它分为两个部分：安装和设置，以及特定GooseAI包装器的引用。

## 安装和设置
- 使用`pip install openai`安装Python SDK。
- 从 [这里](https://goose.ai/) 获取您的GooseAI API密钥。
- 设置环境变量 (`GOOSEAI_API_KEY`)。
```python
import os
os.environ["GOOSEAI_API_KEY"] = "YOUR_API_KEY"
```
## 包装器

### LLM

GooseAI提供了LLM包装器，您可以通过以下方式访问：
```python
from langchain.llms import GooseAI
```
