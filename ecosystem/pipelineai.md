# PipelineAI

本页面介绍如何在LangChain中使用PipelineAI生态系统。
它分为两个部分：安装和设置，然后是特定的PipelineAI包装器参考。

## 安装和设置
- 通过 `pip install pipeline-ai` 命令进行安装
- 获取Pipeline Cloud API密钥并将其设置为环境变量 (`PIPELINE_API_KEY`)

## 包装器
### LLM
存在一个PipelineAI LLM包装器，您可以使用它进行访问
```python
from langchain.llms import PipelineAI
```
