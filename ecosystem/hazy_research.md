# Hazy Research

本页面介绍如何在LangChain中使用Hazy Research生态系统。
它分为两部分：安装和设置，以及对特定Hazy Research封装的引用。

## 安装和设置
- 要使用`manifest`，请使用`pip install manifest-ml`进行安装

## 封装器

### LLM

Hazy Research的`manifest`库中存在一个LLM封装。
`manifest`是一个python库，它本身包装了许多模型提供商，并添加了缓存、历史记录等功能。

要使用这个封装器：
```python
from langchain.llms.manifest import ManifestWrapper
```
