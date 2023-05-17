# Graphsignal

本页面介绍如何使用[Graphsignal](https://app.graphsignal.com)来跟踪和监控LangChain。Graphsignal可以完全可视化您的应用程序，并提供链和工具的延迟分解、完整上下文的异常、数据监控、计算/GPU利用率、OpenAI成本分析等功能。


## 安装和设置

- 使用 `pip install graphsignal` 命令安装Python库。
- 在[这里](https://graphsignal.com)创建免费的Graphsignal账户。
- 获取API密钥，并将其设置为环境变量(`GRAPHSIGNAL_API_KEY`)。

## 跟踪和监控

Graphsignal会自动进行处理并开始跟踪和监控链。然后在您的[Graphsignal仪表板](https://app.graphsignal.com)中可以查看跟踪和指标数据。

通过提供部署名称来初始化跟踪器：
```python
import graphsignal

graphsignal.configure(deployment='my-langchain-app-prod')
```
若需要在任何函数或代码中增加追踪功能，可以使用装饰器或上下文管理器：
```python
@graphsignal.trace_function
def handle_request():    
    chain.run("some initial text")
```

```python
with graphsignal.start_trace('my-chain'):
    chain.run("some initial text")
```
可选地，启用性能分析以记录每个追踪的函数级统计信息。
```python
with graphsignal.start_trace(
        'my-chain', options=graphsignal.TraceOptions(enable_profiling=True)):
    chain.run("some initial text")
```
请查看[快速入门指南](https://graphsignal.com/docs/guides/quick-start/)以获取完整的设置说明。