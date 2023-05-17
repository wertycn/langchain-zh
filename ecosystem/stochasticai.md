# StochasticAI

本页面将介绍如何在LangChain中使用StochasticAI生态系统。分为两部分：安装和设置，以及对特定StochasticAI包装器的引用。

## 安装和设置
- 使用 `pip install stochasticx` 进行安装
- 获取StochasticAI api密钥并将其设置为环境变量(`STOCHASTICAI_API_KEY`)

## 包装器

### LLM

存在一个StochasticAI LLM包装器，您可以使用以下方式进行访问：
```python
from langchain.llms import StochasticAI
```
