# 部署

那么，你已经创建了一个非常酷的链 - 然后呢？如何部署它并使它与世界分享？

本节介绍了几种选项。请注意，这些选项旨在快速部署原型和演示，而不是用于生产系统。如果您需要有关生产系统部署的帮助，请直接与我们联系。

接下来是一些模板 GitHub 存储库的列表，这些存储库旨在轻松分叉和修改以使用您的链。这个列表远非详尽无遗，我们非常欢迎在这里添加贡献。

## [Streamlit](https://github.com/hwchase17/langchain-streamlit-template)

这个存储库作为一个模板，介绍了如何使用Streamlit部署LangChain。它实现了一个聊天机器人的接口。它还包含了在Streamlit平台上部署该应用程序的说明。

## [Gradio (on Hugging Face)](https://github.com/hwchase17/langchain-gradio-template)

这个存储库作为一个模板，介绍了如何使用Gradio部署LangChain。
该应用程序实现了聊天机器人接口，并采用了“自行携带令牌”的方法（适用于避免产生巨额账单）。同时，本教程还包含了如何在Hugging Face平台上部署该应用程序的说明。此外，本教程受到James Weaver[优秀示例](https://huggingface.co/JavaFXpert)的很大影响。

## [Beam](https://github.com/slai-labs/get-beam/tree/main/examples/langchain-question-answering)

该存储库是如何使用[Beam](https://beam.cloud)部署LangChain的模板。

它实现了一个问答应用程序，并包含了将该应用程序部署为无服务器REST API的说明。

## [Vercel](https://github.com/homanp/vercel-langchain)

这是一个最小的示例，演示如何在Flask上运行LangChain。

## [Kinsta](https://github.com/kinsta/hello-world-langchain)

这是一个最小的示例，演示如何使用Flask将LangChain部署到[Kinsta](https://kinsta.com)。

## [Fly.io](https://github.com/fly-apps/hello-fly-langchain)
在Flask上使用LangChain部署的最简示例。

## [Digitalocean App Platform](https://github.com/homanp/digitalocean-langchain)

如何将LangChain部署到DigitalOcean App Platform的最小示例。

## [Google Cloud Run](https://github.com/homanp/gcp-langchain)

如何将LangChain部署到Google Cloud Run的最小示例。

## [SteamShip](https://github.com/steamship-core/steamship-langchain/)

此存储库包含用于SteamShip的LangChain适配器，使LangChain开发人员可以快速在SteamShip上部署他们的应用程序。这包括：生产就绪的终端节点，跨依赖项的水平扩展，应用程序状态的持久存储，多租户支持等。

## [Langchain-serve](https://github.com/jina-ai/langchain-serve)
本代码库允许用户通过RESTful、gRPC或WebSocket API来提供本地链和代理，感谢[Jina](https://docs.jina.ai/)。轻松部署您的链与代理，享受独立扩展、无服务和自动缩放的API，以及在Jina AI云端的Streamlit Playground。

## [BentoML](https://github.com/ssheng/BentoChain)

本代码库提供了一个使用[BentoML](https://github.com/bentoml/BentoML)部署LangChain应用程序的示例。BentoML是一个框架, 可以将机器学习应用程序标准化为OCI镜像进行容器化。 BentoML还允许自动生成OpenAPI和gRPC端点。使用BentoML, 您可以将来自所有流行的ML框架的模型集成并部署为运行在最优硬件上的微服务，并可以独立缩放。

## [Databutton](https://databutton.com/home?new-data-app=true)
这些模板是使用Databutton构建、部署和分享LangChain应用程序的示例。您可以使用Streamlit创建用户界面、通过调度Python代码自动化任务，并在内置存储中存储文件和数据。示例包括具有对话式记忆的聊天机器人界面、个人搜索引擎和LangChain应用程序的起始模板。部署和分享仅需一键即可完成。