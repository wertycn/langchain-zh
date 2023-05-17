# Helicone

本页面介绍如何在LangChain中使用[Helicone](https://helicone.ai)生态系统。

## Helicone是什么？

Helicone是一个[开源的](https://github.com/Helicone/helicone)可观测性平台，代理您的OpenAI流量并为您提供有关开支、延迟和使用情况的关键见解。

![Helicone](../_static/HeliconeDashboard.png)

## 快速入门

在LangChain环境下，您只需添加以下参数即可。
```bash
export OPENAI_API_BASE="https://oai.hconeai.com/v1"
```
现在，请前往[Helicone.ai](https://helicone.ai/onboarding?step=2)创建您的账户，并在我们的仪表板中添加您的OpenAI API密钥以查看日志。

![Helicone](../_static/HeliconeKeys.png)

## 如何启用Helicone缓存
```python
from langchain.llms import OpenAI
import openai
openai.api_base = "https://oai.hconeai.com/v1"

llm = OpenAI(temperature=0.9, headers={"Helicone-Cache-Enabled": "true"})
text = "What is a helicone?"
print(llm(text))
```
[Helicone缓存文档](https://docs.helicone.ai/advanced-usage/caching)

## 如何使用Helicone自定义属性
```python
from langchain.llms import OpenAI
import openai
openai.api_base = "https://oai.hconeai.com/v1"

llm = OpenAI(temperature=0.9, headers={
        "Helicone-Property-Session": "24",
        "Helicone-Property-Conversation": "support_issue_2",
        "Helicone-Property-App": "mobile",
      })
text = "What is a helicone?"
print(llm(text))
```
[Helicone资产文档](https://docs.helicone.ai/advanced-usage/custom-properties)