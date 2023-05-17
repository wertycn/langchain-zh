# Docugami

本页面介绍了如何在LangChain中使用[Docugami](https://docugami.com)。

## 什么是Docugami？

Docugami将商业文档转换为Document XML Knowledge Graph，生成表示整个文档的XML语义树的森林。这是包含文档中各个块的语义和结构特征的丰富表示形式，作为一个XML树。

## 快速开始

1. 创建 Docugami 工作区：http://www.docugami.com  （提供免费试用版）
2. 添加您的文档（PDF、DOCX或DOC），并允许 Docugami 将它们摄入并将其聚类成一组相似的文档，例如 NDA、租赁协议和服务协议。该系统不支持固定的文档类型集，创建的聚类取决于您的特定文档，并且您可以稍后[更改文档集分配](https://help.docugami.com/home/working-with-the-doc-sets-view)。
3. 在开发者游乐场为您的工作区创建访问令牌。详细说明请参见：https://help.docugami.com/home/docugami-api
4. 在 https://api-docs.docugami.com/ 上探索 Docugami API，以获取您已处理的文档集 ID 的列表，或者仅获取特定文档集的文档 ID。
6. 使用 [此笔记本](../modules/indexes/document_loaders/examples/docugami.ipynb) 中详述的 DocugamiLoader，为您的文档获取丰富的语义块。
7. 可选地，构建并发布一个或多个报告或摘要以帮助 Docugami 根据您的偏好改进基于标签的语义 XML，这些标签随后作为元数据添加到 DocugamiLoader 输出中。使用诸如 [self-querying retriever](https://python.langchain.com/en/latest/modules/indexes/retrievers/examples/self_query_retriever.html) 的技术进行高精度文档 QA。

# 与其他块化技术的优势
对于从文档中检索信息而言，适当的文本分块至关重要。有许多文本分块技术，其中简单的方法基于空格，或基于字符长度进行递归的分块拆分等。Docugami提供了一种不同的方法：

1. **智能分块：** Docugami将每个文档分解成一个分层的语义XML树，包括各种大小的块，从单词或数字值到整个部分。这些块遵循文档的语义轮廓，提供比任意长度或简单基于空格的分块更有意义的表示。
2. **结构化表示：** 此外，XML树使用属性来表示所有文档的结构轮廓，使用标头、段落、列表、表格等常见元素，并在支持的所有文档格式（如扫描的PDF或DOCX文件）中保持一致。它适当地处理长篇文档的特性，如页眉/页脚或多列流以进行干净的文本提取。

3. **语义注释：** 块被注释为语义标签，这些标签在整个文档集中是连贯的，即使它们是以不同的方式编写和格式化的，也能够方便地执行一致的分层查询。例如，在租赁协议集中，您可以轻松地确定关键规定，如房东、租户或续约日期，以及更复杂的信息，例如任何子租赁规定的措辞或特定司法管辖区是否在终止条款中具有例外部分。
4. **附加元数据：** 如果用户一直使用Docugami，还可以在块上注释额外的元数据。这些附加的元数据可以用于高精度的文档质量保证，无需上下文窗口限制。参见[此笔记本](../modules/indexes/document_loaders/examples/docugami.ipynb)中的详细代码演示。