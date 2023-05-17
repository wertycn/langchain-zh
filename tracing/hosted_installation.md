# 云托管设置

我们提供托管版本的跟踪服务，请前往 [langchainplus.vercel.app](https://langchainplus.vercel.app/) 使用。您可以使用此版本而无需在本地运行服务器即可查看您的运行中的跟踪信息。

注：目前我们只向少数用户提供此服务。托管平台处于非常原始的开发状态，数据可能会被随时删除。请勿依赖系统长期保存数据，并且请勿记录可能包含敏感信息的跟踪信息。如果您有兴趣使用托管平台，请填写[表格](https://forms.gle/tRCEMSeopZf6TE3b6)。

## 安装

1. 登录系统并在右上角点击“API Key”。生成一个新的密钥并妥善保管。您将需要使用该密钥进行身份验证。

## 环境设置

安装完成后，您现在必须设置您的环境以使用跟踪服务。

您可以通过在终端中设置环境变量来完成此操作。例如运行`export LANGCHAIN_HANDLER=langchain`。
您也可以通过在每个脚本的顶部添加以下代码段来实现此功能。 **重要提示：**这必须放在您的脚本的最顶部， 在从“langchain”导入任何东西之前。
```python
import os
os.environ["LANGCHAIN_HANDLER"] = "langchain"
```
您还需要设置一个环境变量来指定端点和API密钥。这可以通过以下环境变量完成：

1. `LANGCHAIN_ENDPOINT` = "https://langchain-api-gateway-57eoxz8z.uc.gateway.dev"
2. `LANGCHAIN_API_KEY` - 将其设置为您在安装期间生成的API密钥。

下面是添加所有相关环境变量的示例：
```python
import os
os.environ["LANGCHAIN_HANDLER"] = "langchain"
os.environ["LANGCHAIN_ENDPOINT"] = "https://langchain-api-gateway-57eoxz8z.uc.gateway.dev"
os.environ["LANGCHAIN_API_KEY"] = "my_api_key"  # Don't commit this to your repo! Better to set it in your terminal.
```
