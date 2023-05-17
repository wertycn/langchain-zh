# 香蕉

本页介绍如何在LangChain中使用香蕉生态系统。内容分为两部分：安装和设置，以及具体的香蕉包装器参考。

## 安装和设置

- 使用 `pip install banana-dev` 安装
- 获取一个香蕉API密钥并将其设置为环境变量（`BANANA_API_KEY`）

## 定义您的香蕉模板

如果您想使用一个可用的语言模型模板，您可以在[此处](https://app.banana.dev/templates/conceptofmind/serverless-template-palmyra-base)找到一个。
此模板使用[Writer](https://writer.com/product/api/)的Palmyra-Base模型。您可以在[此处](https://github.com/conceptofmind/serverless-template-palmyra-base)查看一个香蕉示例存储库。

## 构建香蕉应用

香蕉应用必须在json返回中包含“output”键。存在严格的响应结构。
```python
# Return the results as a dictionary
result = {'output': result}
```
一个例子推理函数如下：
```python
def inference(model_inputs:dict) -> dict:
    global model
    global tokenizer

    # Parse out your arguments
    prompt = model_inputs.get('prompt', None)
    if prompt == None:
        return {'message': "No prompt provided"}

    # Run the model
    input_ids = tokenizer.encode(prompt, return_tensors='pt').cuda()
    output = model.generate(
        input_ids,
        max_length=100,
        do_sample=True,
        top_k=50,
        top_p=0.95,
        num_return_sequences=1,
        temperature=0.9,
        early_stopping=True,
        no_repeat_ngram_size=3,
        num_beams=5,
        length_penalty=1.5,
        repetition_penalty=1.5,
        bad_words_ids=[[tokenizer.encode(' ', add_prefix_space=True)[0]]]
        )

    result = tokenizer.decode(output[0], skip_special_tokens=True)
    # Return the results as a dictionary
    result = {'output': result}
    return result
```
您可以在[这里](https://github.com/conceptofmind/serverless-template-palmyra-base/blob/main/app.py)找到一个完整的Banana应用程序示例。

## 包装器

### 语言模型

LangChain提供了一个Banana语言模型的包装器，您可以使用以下命令进行访问：
```python
from langchain.llms import Banana
```
您需要提供仪表板中的模型密钥：
```python
llm = Banana(model_key="YOUR_MODEL_KEY")
```
