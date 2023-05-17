# RWKV-4

本页介绍如何在LangChain内使用`RWKV-4`包装器。
它分为两部分：安装和设置，以及使用示例。

## 安装和设置
- 使用`pip install rwkv`命令安装Python软件包
- 使用`pip install tokenizer`命令安装分词器Python软件包
- 下载[RWKV模型](https://huggingface.co/BlinkDL/rwkv-4-raven/tree/main)并将其放置在所需的目录中
- 下载[tokens文件](https://raw.githubusercontent.com/BlinkDL/ChatRWKV/main/20B_tokenizer.json)

## 使用方法

### RWKV

要使用RWKV包装器，您需要提供预训练模型文件的路径和分词器的配置。
```python
from langchain.llms import RWKV

# Test the model

```python
def generate_prompt(instruction, input=None):
    if input:
        return f"""下面的指令描述了一项任务，并且提供了更多的上下文。请写一个回应，以适当地完成请求。

# 指令：
{instruction}

# 上下文：
{input}

# 回应：
"""
    else:
        return f"""下面的指令描述了一项任务。请写一个回应，以适当地完成请求。

# 指令：
{instruction}

# 回应：
"""


model = RWKV(model="./models/RWKV-4-Raven-3B-v7-Eng-20230404-ctx4096.pth", strategy="cpu fp32", tokens_path="./rwkv/20B_tokenizer.json")
response = model(generate_prompt("从前有一个故事， "))
```
## Model File

You can find links to model file downloads at the [RWKV-4-Raven](https://huggingface.co/BlinkDL/rwkv-4-raven/tree/main) repository.

### Rwkv-4 models -> recommended VRAM


```
RWKV VRAM
模型 | 8位 | bf16/fp16 | fp32
14B   | 16GB | 28GB      | >50GB
7B    | 8GB  | 14GB      | 28GB
3B    | 2.8GB| 6GB       | 12GB
1b5   | 1.3GB| 3GB       | 6GB
```

See the [rwkv pip](https://pypi.org/project/rwkv/) page for more information about strategies, including streaming and cuda support.
