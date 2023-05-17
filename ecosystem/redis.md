# Redis

这个页面介绍如何在LangChain中使用[Redis](https://redis.com) 生态系统。
它被分成两部分：安装和设置，以及对特定Redis封装的引用。

## 安装和设置
- 使用 `pip install redis` 安装 Redis Python SDK

## 封装

### 缓存

缓存封装允许使用[Redis](https://redis.io)作为低延迟的远程内存缓存，用于LLM提示和响应。

#### 标准缓存
标准缓存是全球[开源](https://redis.io)和[企业](https://redis.com)用户在生产中使用的Redis常规用例。

要导入此缓存，可以使用以下代码：
```python
from langchain.cache import RedisCache
```
使用这个缓存与你的LLMs配合使用：
```python
import langchain
import redis

redis_client = redis.Redis.from_url(...)
langchain.llm_cache = RedisCache(redis_client)
```
#### 语义缓存
语义缓存允许用户根据用户输入和之前缓存结果之间的语义相似性来检索缓存的提示。实现上，它将Redis作为缓存和向量存储器。

要导入该缓存，请执行以下操作：
```python
from langchain.cache import RedisSemanticCache
```
要使用此缓存与您的LLM进行配合：
```python
import langchain
import redis

# use any embedding provider...
from tests.integration_tests.vectorstores.fake_embeddings import FakeEmbeddings

redis_url = "redis://localhost:6379"

langchain.llm_cache = RedisSemanticCache(
    embedding=FakeEmbeddings(),
    redis_url=redis_url
)
```
### VectorStore

`vectorstore`包装器将Redis转换为用于语义搜索或LLM内容检索的低延迟[向量数据库](https://redis.com/solutions/use-cases/vector-database/)。

要导入`vectorstore`，请执行以下操作：
```python
from langchain.vectorstores import Redis
```
更详细的Redis向量存储器包装器指南，请参见[this notebook](../modules/indexes/vectorstores/examples/redis.ipynb)。

### 检索器

Redis向量存储器检索器包装了向量存储器类，以执行低延迟文档检索。要创建检索器，请在基本向量存储器类上调用`.as_retriever()`方法。

### 存储器

Redis可用于持久化LLM会话。

#### 向量存储器检索器存储器

有关`VectorStoreRetrieverMemory`包装器的更详细介绍，请参见[this notebook](../modules/memory/types/vectorstore_retriever_memory.ipynb)。

#### 聊天信息历史存储器

有关使用Redis缓存会话消息历史记录的详细示例，请参见[this notebook](../modules/memory/examples/redis_chat_message_history.ipynb)。