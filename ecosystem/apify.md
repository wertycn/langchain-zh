# Apify

本页面说明如何在LangChain中使用[Apify](https://apify.com)。

## 概述

Apify是一个云平台，可用于网络爬虫和数据提取，它提供了一个包含1000多个预制应用程序的“Actor”生态系统，可用于各种爬取、抓取和提取用例。

[![Apify Actors](../_static/ApifyActors.png)](https://apify.com/store)

此集成使您能够在Apify平台上运行Actors，并将它们的结果加载到LangChain中，以便从网站、博客或知识库中获取文档和数据，例如生成文档、博客或知识库中的答案。

## 安装和设置

- 使用`pip install apify-client`命令安装Python的Apify API客户端。
- 获取您的[Apify API令牌](https://console.apify.com/account/integrations)，然后将其设置为环境变量(`APIFY_API_TOKEN`)或在构造函数中作为`apify_api_token`参数传递给`ApifyWrapper`。

## 包装器

### 实用工具
您可以使用`ApifyWrapper`在Apify平台上运行Actor。
```python
from langchain.utilities import ApifyWrapper
```
要了解更详细的封装教程，请参见[此笔记本](../modules/agents/tools/examples/apify.ipynb)。

### 载入器

您也可以使用我们的`ApifyDatasetLoader`从Apify数据集中获取数据。
```python
from langchain.document_loaders import ApifyDatasetLoader
```
要了解此加载器的更详细步骤，请参见[这个notebook](../modules/indexes/document_loaders/examples/apify_dataset.ipynb)。