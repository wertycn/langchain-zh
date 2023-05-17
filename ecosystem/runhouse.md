# Runhouse

本页面介绍如何在LangChain中使用[Runhouse](https://github.com/run-house/runhouse)生态系统，分为三个部分: 安装和设置、LLMs和嵌入式.

## 安装和设置
- 使用`pip install runhouse`安装Python SDK。
- 如果您想使用按需群集，在执行`sky check`命令之前请检查您的云凭据。

## 自托管LLMs
对于基本的自托管LLMs，可以使用`SelfHostedHuggingFaceLLM`类。对于更自定义的LLMs，您可以使用`SelfHostedPipeline`父类。
```python
from langchain.llms import SelfHostedPipeline, SelfHostedHuggingFaceLLM
```
要了解更详细的自托管LLM操作指南，请参阅 [此笔记本](../modules/models/llms/integrations/runhouse.ipynb)

## 自托管嵌入

通过Runhouse，您可以使用多种方式将自托管嵌入与LangChain配合使用。

对于来自Hugging Face Transformers模型的基本自托管嵌入，您可以使用`SelfHostedEmbedding`类。
```python
from langchain.llms import SelfHostedPipeline, SelfHostedHuggingFaceLLM
```
如果您需要更详细地了解自托管嵌入式应用，请参阅[此笔记本](../modules/models/text_embedding/examples/self-hosted.ipynb)。