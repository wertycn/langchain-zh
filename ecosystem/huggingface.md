# Hugging Face

本页面介绍了如何在LangChain中使用Hugging Face生态系统（包括[Hugging Face Hub](https://huggingface.co)）。该页面分为两部分：安装和设置，以及与特定Hugging Face封装的相关引用。

## 安装与设置

如果您想使用Hugging Face Hub：
- 使用`pip install huggingface_hub`安装Hub客户端库
- 创建一个Hugging Face账户（免费！）
- 创建一个[访问令牌](https://huggingface.co/docs/hub/security-tokens)并将其设置为环境变量(`HUGGINGFACEHUB_API_TOKEN`)

如果您想使用Hugging Face Python库：
- 使用`pip install transformers`安装模型和tokenizer
- 使用`pip install datasets`安装数据集

## 封装器

### LLM

存在两个Hugging Face LLM封装器，一个用于本地管道，另一个用于在Hugging Face Hub托管的模型。
请注意，这些包装器仅适用于支持以下任务的模型: [`text2text-generation`](https://huggingface.co/models?library=transformers&pipeline_tag=text2text-generation&sort=downloads)，[`text-generation`](https://huggingface.co/models?library=transformers&pipeline_tag=text-classification&sort=downloads)。

要使用本地管道包装器：
```python
from langchain.llms import HuggingFacePipeline
```
使用Hugging Face Hub上托管的模型包装器:
```python
from langchain.llms import HuggingFaceHub
```
更为详细的Hugging Face Hub包装器教程，请参考[this notebook](../modules/models/llms/integrations/huggingface_hub.ipynb)


### 嵌入（Embeddings）

Hugging Face提供了两个嵌入包装器，一个用于本地模型，另一个用于在Hugging Face Hub上托管的模型。
请注意，这些包装器仅适用于[`sentence-transformers` 模型](https://huggingface.co/models?library=sentence-transformers&sort=downloads)。

要使用本地pipeline包装器，请：
```python
from langchain.embeddings import HuggingFaceEmbeddings
```
使用托管在Hugging Face Hub上的模型的包装器：
```python
from langchain.embeddings import HuggingFaceHubEmbeddings
```
若想了解更详细的内容，请查看[此笔记本](../modules/models/text_embedding/examples/huggingfacehub.ipynb)。

### 分词器

您可以通过`transformers`包使用此处提供的分词器。默认情况下，它用于所有LLM的标记计数。

您还可以在使用分割文档时使用它来计数标记。
```python
from langchain.text_splitter import CharacterTextSplitter
CharacterTextSplitter.from_huggingface_tokenizer(...)
```
有关更详细的说明，请参见[这个笔记本](../modules/indexes/text_splitters/examples/huggingface_length_function.ipynb)。

### 数据集

Hugging Face Hub有许多丰富的[数据集](https://huggingface.co/datasets)，可用于评估您的LLM链。

有关如何使用它们进行评估的详细说明，请参见[此笔记本](../use_cases/evaluation/huggingface_datasets.ipynb)。