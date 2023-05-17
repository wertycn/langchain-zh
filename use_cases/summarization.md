# 概述

> [概念指南](https://docs.langchain.com/docs/use-cases/summarization)


概述是指创建多个长文档的较小摘要。这对于将长文档浓缩为核心信息非常有用。

使用摘要链快速入门的推荐方式为：
```python
from langchain.chains.summarize import load_summarize_chain
chain = load_summarize_chain(llm, chain_type="map_reduce")
chain.run(docs)
```
以下资源可供使用：
- [摘要笔记本](../modules/chains/index_examples/summarize.ipynb)：演示如何完成此任务的笔记本。

其他相关资源包括：
- [文档处理工具](../reference/utils.rst)：指南介绍几个实用工具，包括文本分割器（用于分割长文档）等，将对此任务有所帮助。