# 文档问答

> [概念指南](https://docs.langchain.com/docs/use-cases/qa-docs)

这里所说的文档问答是指在您的文档数据上进行的问答。对于其他类型的数据的问答，请查看其他来源的文档，例如[SQL数据库问答](./tabular.md)或[与API进行交互](./apis.md)。

对于多个文档的问答，您几乎总是希望在数据上创建一个索引。这可以用于聪明地访问与给定问题最相关的文档，从而避免将所有文档传递给LLM（节省您的时间和金钱）。

请参见 [此笔记本](../modules/indexes/getting_started.ipynb)以获取更详细的介绍，但是对于一个超级快速的入门，涉及的步骤如下：

**加载文档**
```python
from langchain.document_loaders import TextLoader
loader = TextLoader('../state_of_the_union.txt')
```
更多有关如何开始加载文档的信息，请参见[这里](../modules/indexes/document_loaders.rst)。

**创建索引**
```python
from langchain.indexes import VectorstoreIndexCreator
index = VectorstoreIndexCreator().from_loaders([loader])
```
目前最好且最受欢迎的索引方式是VectorStore索引。

**查询您的索引**
```python
query = "What did the president say about Ketanji Brown Jackson"
index.query(query)
```
或者，使用`query_with_sources`函数来获取涉及到的源代码。
```python
query = "What did the president say about Ketanji Brown Jackson"
index.query_with_sources(query)
```
同样地，这些高级接口隐藏了许多底层的细节，因此请参考[这个notebook](../modules/indexes/getting_started.ipynb)以获得更低级别的介绍。

## 文档问答

问答涉及检索多个文档，然后针对这些文档提出问题。基于文档的内容，LLM响应将包含您问题的答案。

使用问答链的推荐方法是：
```python
from langchain.chains.question_answering import load_qa_chain
chain = load_qa_chain(llm, chain_type="stuff")
chain.run(input_documents=docs, question=query)
```
以下资源可用：

- [问答笔记本](../modules/chains/index_examples/question_answering.ipynb)：通过笔记本演示如何完成此任务。
- [VectorDB问答笔记本](../modules/chains/index_examples/vector_db_qa.ipynb)：逐步演示如何在向量数据库上进行问答。这通常非常有用，特别是当您拥有大量文档时，您不想将它们全部传递给LLM，而是首先想通过嵌入进行一些语义搜索。

## 添加来源

还有一种变体，除了回答问题外，语言模型还将引用它使用的来源文件（例如，传递的文件中使用了哪些文件）。

使用具有源代码的问答链的推荐方式是：
```python
from langchain.chains.qa_with_sources import load_qa_with_sources_chain
chain = load_qa_with_sources_chain(llm, chain_type="stuff")
chain({"input_documents": docs, "question": query}, return_only_outputs=True)
```
以下资源可供使用：

- [QA With Sources Notebook](../modules/chains/index_examples/qa_with_sources.ipynb)：演示如何完成这个任务的笔记本。
- [VectorDB QA With Sources Notebook](../modules/chains/index_examples/vector_db_qa_with_sources.ipynb)：演示如何使用向量数据库进行带源问答。当你拥有大量文档时，并且不想将所有文档传输到LLM（语言模型）中，而是首先想要对嵌入空间进行语义搜索时，此示例通常非常有用。

## 其他相关资源

其他相关资源包括：

- [文档处理工具](/modules/utils/how_to_guides.rst)：介绍了几个对于本任务将非常有用的实用工具，包括文本分割器（用于分割长文档）、嵌入和向量存储器（适用于上述向量数据库示例）。
- [合并文档链](/modules/indexes/combine_docs.md)：介绍了可以完成这个任务的特定类型的链式结构的概念概述。

## 端到端的示例

要了解以端到端方式完成的示例，请参阅以下资源：

- [使用Sources Notebook在团队聊天中进行语义搜索](question_answering/semantic-search-over-chat.ipynb)：一份笔记本，可通过语义搜索查找团队聊天记录。