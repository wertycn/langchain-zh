# Anyscale

本页面介绍如何在LangChain中使用Anyscale生态系统。包括安装与设置和对特定Anyscale包装器的参考。

## 安装和设置
- 获取Anyscale服务的URL、路由和API密钥，并将它们设置为环境变量(`ANYSCALE_SERVICE_URL`,`ANYSCALE_SERVICE_ROUTE`, `ANYSCALE_SERVICE_TOKEN`)。
- 更多详情请参见[Anyscale文档](https://docs.anyscale.com/productionize/services-v2/get-started)。

## 包装器

### LLM

存在一个Anyscale LLM包装器，您可以使用它来训练和部署Anyscale的语言建模服务，如下：
```python
from langchain.llms import Anyscale
```
