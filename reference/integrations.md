# 集成

除了安装这个Python包之外，您还需要安装其他的包并设置环境变量，具体取决于您想要使用哪些链。

注：默认情况下，这些包未包含在依赖项中，原因是我们想象这个包要扩展，我们不想强制使用不需要的依赖项。

以下使用情况需要特定的安装和API密钥：

- _OpenAI_:
  - 使用 `pip install openai` 安装所需的依赖项
  - 获取OpenAI api key，并将其设置为环境变量 (`OPENAI_API_KEY`) 或将其传递到LLM构造函数中作为 `openai_api_key`。
- _Cohere_:
  - 使用 `pip install cohere` 安装所需的依赖项
  - 获取Cohere的API密钥，并将其设置为环境变量 (`COHERE_API_KEY`) 或将其传递到LLM构造函数中作为 `cohere_api_key`。
- _GooseAI_:
  - 使用 `pip install openai` 安装所需的依赖项
- 获取GooseAI的API密钥，将其设置为环境变量(`GOOSEAI_API_KEY`)或将其作为`gooseai_api_key`传递给LLM构造函数。
- _Hugging Face Hub_
  - 使用`pip install huggingface_hub`命令安装所需的依赖。
  - 获取Hugging Face Hub的API令牌，将其设置为环境变量(`HUGGINGFACEHUB_API_TOKEN`)或将其作为`huggingfacehub_api_token`传递给LLM构造函数。
- _Petals_:
  - 使用`pip install petals`命令安装所需的依赖。
  - 获取GooseAI的API密钥，将其设置为环境变量(`HUGGINGFACE_API_KEY`)或将其作为`huggingface_api_key`传递给LLM构造函数。
- _CerebriumAI_:
  - 使用`pip install cerebrium`命令安装所需的依赖。
  - 获取Cerebrium的API密钥，将其设置为环境变量(`CEREBRIUMAI_API_KEY`)或将其作为`cerebriumai_api_key`传递给LLM构造函数。
- _PromptLayer_:
  - 使用`pip install promptlayer`命令安装所需的依赖（确保使用的版本为0.1.62或更高）。
- 从[promptlayer.com](http://www.promptlayer.com)获取API密钥，并使用`promptlayer.api_key=<API KEY>`进行设置。
- _SerpAPI_:
  - 使用`pip install google-search-results`安装所需的依赖。
  - 获取SerpAPI api密钥，并将其设置为环境变量（`SERPAPI_API_KEY`）或将其作为参数传递给LLM构造函数中的`serpapi_api_key`。
- _GoogleSearchAPI_:
  - 使用`pip install google-api-python-client`安装所需的依赖。
  - 获取Google api密钥，并将其设置为环境变量（`GOOGLE_API_KEY`）或将其作为参数传递给LLM构造函数中的`google_api_key`。您还需要设置`GOOGLE_CSE_ID`环境变量为您的自定义搜索引擎ID。您也可以将其作为参数传递给LLM构造函数中的`google_cse_id`。
- _WolframAlphaAPI_:
  - 使用`pip install wolframalpha`安装所需的依赖。
  - 获取Wolfram Alpha api密钥，并将其设置为环境变量（`WOLFRAM_ALPHA_APPID`）或将其作为参数传递给LLM构造函数中的`wolfram_alpha_appid`。
- _NatBot_:
- 使用 `pip install playwright` 安装必要的依赖项。
- _Wikipedia_:
  - 使用 `pip install wikipedia` 安装必要的依赖项。
- _Elasticsearch_:
  - 使用 `pip install elasticsearch` 安装必要的依赖项。
  - 设置 Elasticsearch 后端。如果您想在本地搭建，请参考 [这篇文章](https://www.elastic.co/guide/en/elasticsearch/reference/7.17/getting-started.html)。
- _FAISS_:
  - 对于 Python3.7，请使用 `pip install faiss` 安装必要的依赖项；对于 Python3.10+，请使用 `pip install faiss-cpu`。
- _MyScale_：
  - 使用 `pip install clickhouse-connect` 安装必要的依赖项。有关文档，请参阅[此文档](https://docs.myscale.com/en/overview/)。
- _Manifest_:
  - 使用 `pip install manifest-ml` 安装必要的依赖项。（注意：目前只在 Python 3.8+ 中可用）。
- _OpenSearch_:
  - 使用 `pip install opensearch-py` 安装必要的依赖项。
  - 如果您希望在本地设置 OpenSearch，请参考[这篇文章](https://opensearch.org/docs/latest/)。
- _DeepLake_:
- 使用 `pip install deeplake` 安装所需的依赖。
- _LlamaCpp_:
  - 使用 `pip install llama-cpp-python` 安装所需的依赖。
  - 下载模型并按照 [llama.cpp 说明](https://github.com/ggerganov/llama.cpp) 进行转换。
- _Milvus_:
  - 使用 `pip install pymilvus` 安装所需的依赖。
  - 如果想设置本地群集，请参考[这里](https://milvus.io/docs)。
- _Zilliz_:
  - 使用 `pip install pymilvus` 安装所需的依赖。
  - 要快速上手，请参考[这里](https://zilliz.com/doc/quick_start)。


如果您使用的是 `NLTKTextSplitter` 或者 `SpacyTextSplitter`，还需要安装相应的模型。例如，如果您想使用 `SpacyTextSplitter`，则需要使用 `python -m spacy download en_core_web_sm` 命令安装 `en_core_web_sm` 模型。同样，如果您想使用 `NLTKTextSplitter`，则需要使用 `python -m nltk.downloader punkt` 命令安装 `punkt` 模型。