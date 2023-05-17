# 复制

本页面介绍如何在LangChain内使用Replicate运行模型。

## 安装和设置
- 创建[Replicate](https://replicate.com)账户。获取您的API密钥并将其设置为环境变量(`REPLICATE_API_TOKEN`)
- 使用`pip install replicate`命令安装[Replicate python客户端](https://github.com/replicate/replicate-python)。

## 调用模型

在[Replicate explore页面](https://replicate.com/explore)中查找模型，然后将模型名称和版本粘贴在此格式中： `owner-name/model-name:version`

例如，对于[此dolly模型](https://replicate.com/replicate/dolly-v2-12b)，单击API选项卡。模型名称/版本将是：`"replicate/dolly-v2-12b:ef0e1aefc61f8e096ebe4db6b2bacc297daf2ef6899f0f7e001ec445893500e5"`。

只需要 `model` 参数即可，但也可以使用格式`input={model_param:value,...}`传入任何其他模型参数。

例如，如果我们正在运行稳定的扩散并且想要更改图像尺寸：
```
Replicate(model="stability-ai/stable-diffusion:db21e45d3f7023abc2a46ee38a23973f6dce16bb082a930b0c49861f96d1e5bf", input={'image_dimensions': '512x512'})
```
请注意：模型只会返回第一个输出。
从这里，我们可以初始化我们的模型：
```python
llm = Replicate(model="replicate/dolly-v2-12b:ef0e1aefc61f8e096ebe4db6b2bacc297daf2ef6899f0f7e001ec445893500e5")
```
然后运行它：
```python
prompt = """
Answer the following yes/no question by reasoning step by step.
Can a dog drive a car?
"""
llm(prompt)
```
我们可以使用以下语法调用任何Replicate模型（不仅限于LLMs）。例如，我们可以调用[稳定扩散](https://replicate.com/stability-ai/stable-diffusion):
```python
text2image = Replicate(model="stability-ai/stable-diffusion:db21e45d3f7023abc2a46ee38a23973f6dce16bb082a930b0c49861f96d1e5bf", input={'image_dimensions':'512x512'})

image_output = text2image("A cat riding a motorcycle by Picasso")
```
