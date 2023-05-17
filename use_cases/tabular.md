# 查询表格数据

> [概念指南](https://docs.langchain.com/docs/use-cases/qa-tabular)


大量的数据和信息存储在表格数据中，无论是csv，Excel工作表还是SQL表。
本页面涵盖了LangChain可用于处理此格式数据的所有资源。

## 加载文档
如果您有存储在表格格式中的文本数据，您可能希望将数据加载到文档中，然后像处理其他文本/非结构化数据一样对其进行索引。
为此，您应该使用类似[CSVLoader](../modules/indexes/document_loaders/examples/csv.ipynb)的文档加载器，
然后您应该[创建索引](../modules/indexes.rst)并[使用这种方式查询](../modules/chains/index_examples/vector_db_qa.ipynb)。

## 查询
如果您有更多的数字表格数据，或者有大量数据并且不想对其进行索引，您应该查看我们用于处理这些数据的各种链和代理。

### 链
如果您刚开始使用LangChain，并且有相对较小/简单的表格数据，那么您应该使用 chains 来入门。
chains 是一系列预定步骤，可以帮助您更好地掌握并控制正在发生的事情。

- [SQL 数据库 Chains](../modules/chains/examples/sqlite.ipynb)

### Agents

Agents 更加复杂，需要对LLM进行多个查询才能理解要做什么。
Agents 的缺点是您的控制力更少。优点是它们更加强大，
可以用于更大的数据库和更复杂的模式。

- [SQL Agent](../modules/agents/toolkits/examples/sql_database.ipynb)
- [Pandas Agent](../modules/agents/toolkits/examples/pandas.ipynb)
- [CSV Agent](../modules/agents/toolkits/examples/csv.ipynb)