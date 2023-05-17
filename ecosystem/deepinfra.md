# DeepInfra

本页面介绍如何在LangChain中使用DeepInfra生态系统。它分为两个部分：安装和设置，以及对特定DeepInfra包装器的引用。

## 安装和设置
- 从[这里](https://deepinfra.com/)获取你的DeepInfra API密钥。
- 获取DeepInfra API密钥，并将其设置为环境变量(`DEEPINFRA_API_TOKEN`)

## 包装器

### LLM

存在一个DeepInfra LLM包装器，您可以通过以下方式访问：
```python
from langchain.llms import DeepInfra
```
