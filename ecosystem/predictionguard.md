# 预测保护

本页面介绍如何在LangChain中使用预测保护生态系统。
它分为两个部分:安装和设置,以及特定预测保护封装的参考。

## 安装和设置
- 使用 `pip install predictionguard` 安装Python SDK
- 获取一个Prediction Guard访问令牌(如上述[文档](https://docs.predictionguard.com/)所述)，并将其设置为环境变量(`PREDICTIONGUARD_TOKEN`)

## LLM封装器

存在一个Prediction Guard LLM封装器，您可以使用以下方式进行访问
```python
from langchain.llms import PredictionGuard
```
当初始化LLM时，您可以通过提供Prediction Guard“代理”的名称作为参数来实现：
```python
pgllm = PredictionGuard(name="your-text-gen-proxy")
```
或者，您可以使用Prediction Guard的默认代理访问最先进的语言模型（SOTA LLMs）:
```python
pgllm = PredictionGuard(name="default-text-gen")
```
您也可以直接将您的访问令牌作为一个参数提供：
```python
pgllm = PredictionGuard(name="default-text-gen", token="<your access token>")
```
## 示例用法

LLM（LangChain Language Model）包装器的基本用法：
```python
from langchain.llms import PredictionGuard

pgllm = PredictionGuard(name="default-text-gen")
pgllm("Tell me a joke")
```
使用Prediction Guard包装器实现基本LLM（Language Model）串联：


```python
from langchain import PromptTemplate, LLMChain
from langchain.llms import PredictionGuard

template = """Question: {question}

Answer: Let's think step by step."""
prompt = PromptTemplate(template=template, input_variables=["question"])
llm_chain = LLMChain(prompt=prompt, llm=PredictionGuard(name="default-text-gen"), verbose=True)

question = "What NFL team won the Super Bowl in the year Justin Beiber was born?"

llm_chain.predict(question=question)
```
