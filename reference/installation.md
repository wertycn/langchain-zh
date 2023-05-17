# 安装

## 正式版本

LangChain可以在PyPi上使用，因此可以轻松安装如下：
```
pip install langchain
```
这将安装LangChain的最基本要求。
当与各种模型提供程序、数据存储等集成时，LangChain的价值才得以体现。
默认情况下，需要用到的这些依赖关系不会被安装。
然而，有另外两种安装LangChain的方式可以带来这些依赖关系。

要安装常见LLM提供程序所需的模块，请运行:
```
pip install langchain[llms]
```
要安装所有集成所需的所有模块，请运行：
```
pip install langchain[all]
```
注意：如果您正在使用`zsh`，在将方括号作为命令参数传递时，需要将它们引用起来，例如：
```
pip install 'langchain[all]'
```
## 从源码安装

如果您想从源码安装，可以通过克隆代码库并运行以下命令来安装：
```
pip install -e .
```
