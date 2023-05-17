# Deep Lake

本页介绍如何在LangChain中使用Deep Lake生态系统。

## 为什么使用Deep Lake？
- 不仅是一个（多模态）向量存储。您还可以使用数据集对自己的LLM模型进行微调。
- 不仅存储嵌入，还存储具有自动版本控制的原始数据。
- 真正的无服务器。不需要其他服务，可与主要云提供商（AWS S3、GCS等）一起使用。

## 更多资源
1. [LangChain＆Deep Lake的终极指南：构建ChatGPT以回答有关您的金融数据的问题](https://www.activeloop.ai/resources/ultimate-guide-to-lang-chain-deep-lake-build-chat-gpt-to-answer-questions-on-your-financial-data/)
2. [Twitter the-algorithm codebase analysis with Deep Lake](../use_cases/code/twitter-the-algorithm-analysis-deeplake.ipynb)
3. 这是Deep Lake的[白皮书](https://www.deeplake.ai/whitepaper)和[学术论文](https://arxiv.org/pdf/2209.10785.pdf)
4. 以下是一些额外资源供您查阅：[Deep Lake](https://github.com/activeloopai/deeplake)、[入门指南](https://docs.activeloop.ai/getting-started)和 [教程](https://docs.activeloop.ai/hub-tutorials)

## 安装和设置
- 使用 `pip install deeplake` 命令安装Python包

## 包装器

### VectorStore

存在一个围绕Deep Lake的包装器，它是一个用于深度学习应用的数据湖，允许您将其用作向量存储（暂时），无论是用于语义搜索还是示例选择。

要导入这个vectorstore：
```python
from langchain.vectorstores import DeepLake
```
更详细的 Deep Lake 包装器介绍请查看 [此笔记本](../modules/indexes/vectorstores/examples/deeplake.ipynb)。