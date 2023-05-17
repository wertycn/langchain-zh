# 本地部署设置

本页包含安装说明和设置环境使用本地托管版本的跟踪程序。

## 安装

1. 确保您已经安装了Docker（见[获取Docker](https://docs.docker.com/get-docker/)），并且它正在运行。
2. 安装最新版本的 `langchain`：`pip install langchain` 或者 `pip install langchain -U` 以升级您的现有版本。
3. 运行 `langchain-server`。当您运行上面的命令 `pip install langchain` 时，这个命令将被自动安装。
    1. 这将在终端中启动服务器，默认情况下在端口 `4137` 上托管。
    2. 一旦您看到终端输出 `langchain-langchain-frontend-1 | ➜ Local: [http://localhost:4173/](http://localhost:4173/)`, 
       请导航到 [http://localhost:4173/](http://localhost:4173/)

4. 您应该可以看到一个页面，显示您的跟踪工作会话。请参阅概述页面，了解UI的详细步骤。
5. 目前，`langchain-server`程序并不能保证追踪数据在每次运行之间得到持久化。如果您想要持久化存储您的数据，可以将一个卷挂载到Docker容器中。详见[Docker文档](https://docs.docker.com/storage/volumes/)。
6. 要停止服务器，请在运行`langchain-server`的终端中按下`Ctrl+C`。

## 环境设置

在安装完成后，您现在需要设置您的环境以便使用追踪功能。

只需要在终端中设置一个环境变量即可，方法是运行 `export LANGCHAIN_HANDLER=langchain`。

您也可以在每个脚本的顶部添加以下代码段来实现上述功能。**重要提示：** 这必须放置在您脚本的最顶部，在从`langchain`中导入任何内容之前。
```python
import os
os.environ["LANGCHAIN_HANDLER"] = "langchain"
```

