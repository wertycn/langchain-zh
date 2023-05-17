# CerebriumAI

本页面介绍如何在LangChain中使用CerebriumAI生态系统。它分为两个部分：安装和设置，以及特定CerebriumAI包装器的引用。

## 安装和设置
- 通过`pip install cerebrium`命令进行安装。
- 获取一个CerebriumAI api密钥，并将其设置为环境变量（`CEREBRIUMAI_API_KEY`）

## 包装器

### LLM

CerebriumAI提供了一个LLM包装器，您可以使用以下命令访问：
```python
from langchain.llms import CerebriumAI
```
