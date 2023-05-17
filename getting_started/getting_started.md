# 快速上手指南


本教程将为您快速介绍如何使用LangChain构建一个端到端的语言模型应用程序。

## 安装

要开始使用LangChain，请使用以下命令安装LangChain：
```bash
pip install langchain
# or
conda install langchain -c conda-forge
```
## 环境设置

通常使用LangChain将需要与一个或多个模型提供者、数据存储、API等进行集成。

在本例中，我们将使用OpenAI的API，因此我们首先需要安装他们的SDK：
```bash
pip install openai
```
接下来，我们需要在终端中设置环境变量。
```bash
export OPENAI_API_KEY="..."
```
或者，您可以在Jupyter笔记本或Python脚本中执行以下操作：
```python
import os
os.environ["OPENAI_API_KEY"] = "..."
```
## 构建语言模型应用程序：LLMs

既然我们已经安装了LangChain并设置好了环境，我们便可以开始构建语言模型应用程序。

LangChain提供许多模块可用于构建语言模型应用程序。这些模块可以组合在一起以创建更复杂的应用程序，也可以单独用于简单的应用程序。

## LLMs：从语言模型中获取预测结果

LangChain的最基本的构建块是在一些输入上调用一个LLM。让我们通过一个简单的例子来演示如何做到这一点。请假设我们正在构建一个基于公司产品的名称来生成公司名称的服务。

为了做到这一点，我们首先需要导入LLM wrapper。
```python
from langchain.llms import OpenAI
```
我们可以使用任何参数来初始化包装器。
在这个例子中，我们可能希望输出结果更加随机，所以我们将使用高温度来初始化它。
```python
llm = OpenAI(temperature=0.9)
```
现在我们可以对某些输入进行调用!
```python
text = "What would be a good company name for a company that makes colorful socks?"
print(llm(text))
```

```pycon
Feetful of Fun
```
有关如何在LangChain中使用LLMs的详细信息，请参阅[LLM入门指南](../modules/models/llms/getting_started.ipynb)。


## 提示模板：管理LLMs的提示

调用LLM是很好的第一步，但这只是一个开始。
通常，当您在应用程序中使用LLM时，您并不会直接将用户输入发送到LLM。
相反，您可能会获取用户输入并构建一个提示，然后将其发送到LLM。

例如，在之前的示例中，我们传递的文本是硬代码的，要求为一家生产彩色袜子的公司提供名称。
在这个虚构的服务中，我们只想使用描述公司业务的用户输入，并使用这些信息格式化提示。

这很容易在LangChain中实现！

首先，让我们定义提示模板：
```python
from langchain.prompts import PromptTemplate

prompt = PromptTemplate(
    input_variables=["product"],
    template="What is a good name for a company that makes {product}?",
)
```
现在让我们看看它是如何工作的！我们可以调用`.format`方法进行格式化。
```python
print(prompt.format(product="colorful socks"))
```

```pycon
What is a good name for a company that makes colorful socks?
```
[更多细节请查看提示的入门指南。](../modules/prompts/chat_prompt_template.ipynb)


## 链：将LLM和提示模块组合在多步骤工作流中

迄今为止，我们已经单独使用PromptTemplate和LLM原语。但是，真正的应用程序不只是一个原语，而是它们的组合。

在LangChain中，链由链接组成，可以是像LLM这样的原语，也可以是其他链。

最基本的链类型是LLMChain，它由PromptTemplate和LLM组成。

扩展之前的示例，我们可以构造一个LLMChain，它接收用户输入，使用PromptTemplate格式化输入，然后将格式化后的响应传递给LLM。
```python
from langchain.prompts import PromptTemplate
from langchain.llms import OpenAI

llm = OpenAI(temperature=0.9)
prompt = PromptTemplate(
    input_variables=["product"],
    template="What is a good name for a company that makes {product}?",
)
```
我们现在可以创建一个非常简单的链，它将采用用户输入，使用它来格式化提示，然后将其发送到LLM：
```python
from langchain.chains import LLMChain
chain = LLMChain(llm=llm, prompt=prompt)
```
我们现在可以只指定产品来运行该链！
```python
chain.run("colorful socks")
# -> '\n\nSocktastic!'
```
来了！第一个Chain - 一个LLM Chain。

这是比较简单的链的类型之一，但是理解其工作原理可为您处理更复杂的链奠定基础。

[欲了解更多详情，请查看链的入门指南。](../modules/chains/getting_started.ipynb)

## Agents: 根据用户输入动态调用链

到目前为止，我们看到的链是按预定顺序运行的。

Agents则不再如此：它们使用LLM来确定需要执行的操作以及执行顺序。一个操作可以是使用工具并观察其输出，或将输出返回给用户。

如果正确使用，Agents可以非常强大。在本教程中，我们通过最简单、最高水平的API向您展示如何轻松使用Agents。

为了加载Agents，您需要理解以下概念：
- 工具（Tool）：执行特定任务的函数。例如：Google搜索、数据库查找、Python REPL或者其它链。目前，工具的接口是一个期望输入一个字符串并返回一个字符串的函数。
- LLM：驱动代理的语言模型。
- 代理（Agent）：要使用的代理。这应该是一个字符串，引用了一个支持的代理类。因为这个notebook只涵盖最简单、最高级别的API，所以仅包括使用标准支持的代理。如果您想实现自定义代理，请参阅自定义代理的文档（即将推出）。

**代理**：支持代理及其规格的列表，请参见[此处](../modules/agents/getting_started.ipynb)。

**工具**：预定义的工具及其规格的列表，请参见[此处](../modules/agents/tools/getting_started.md)。

为了本示例，您还需要安装SerpAPI Python包。
```bash
pip install google-search-results
```
并设置相应的环境变量。
```python
import os
os.environ["SERPAPI_API_KEY"] = "..."
```
现在我们可以开始了！
```python
from langchain.agents import load_tools
from langchain.agents import initialize_agent
from langchain.agents import AgentType
from langchain.llms import OpenAI

# First, let's load the language model we're going to use to control the agent.
llm = OpenAI(temperature=0)

# Next, let's load some tools to use. Note that the `llm-math` tool uses an LLM, so we need to pass that in.
tools = load_tools(["serpapi", "llm-math"], llm=llm)


# Finally, let's initialize an agent with the tools, the language model, and the type of agent we want to use.
agent = initialize_agent(tools, llm, agent=AgentType.ZERO_SHOT_REACT_DESCRIPTION, verbose=True)

# Now let's test it out!
agent.run("What was the high temperature in SF yesterday in Fahrenheit? What is that number raised to the .023 power?")
```

```pycon
> Entering new AgentExecutor chain...
 I need to find the temperature first, then use the calculator to raise it to the .023 power.
Action: Search
Action Input: "High temperature in SF yesterday"
Observation: San Francisco Temperature Yesterday. Maximum temperature yesterday: 57 °F (at 1:56 pm) Minimum temperature yesterday: 49 °F (at 1:56 am) Average temperature ...
Thought: I now have the temperature, so I can use the calculator to raise it to the .023 power.
Action: Calculator
Action Input: 57^.023
Observation: Answer: 1.0974509573251117

Thought: I now know the final answer
Final Answer: The high temperature in SF yesterday in Fahrenheit raised to the .023 power is 1.0974509573251117.

> Finished chain.
```
## 内存：为链和代理添加状态

到目前为止，我们研究过的所有链和代理都是无状态的。但是往往，您可能希望链或代理具有一些"内存"的概念，以便它可以记住有关其先前交互的信息。最清晰和简单的例子是设计聊天机器人 - 您希望它记住以前的消息，以便它可以使用上下文进行更好的交谈。这将是一种"短期记忆"的类型。在更复杂的一面，您可以想象一个链/代理随着时间的推移记住关键的信息 - 这将是一种"长期记忆"的形式。有关后者的更具体的想法，请参阅这个[awesome paper](https://memprompt.com/)。

LangChain提供了几个特别为此目的创建的链。本笔记本介绍了如何使用其中一个链（`ConversationChain`）和两种不同类型的内存。
默认情况下，`ConversationChain` 提供了一种简单的记忆类型，可以记住之前的所有输入/输出，并将它们添加到传递的上下文中。让我们看看如何使用这个链条（设置 `verbose=True`，这样我们可以看到提示信息）。
```python
from langchain import OpenAI, ConversationChain

llm = OpenAI(temperature=0)
conversation = ConversationChain(llm=llm, verbose=True)

output = conversation.predict(input="Hi there!")
print(output)
```

```pycon
> Entering new chain...
Prompt after formatting:
The following is a friendly conversation between a human and an AI. The AI is talkative and provides lots of specific details from its context. If the AI does not know the answer to a question, it truthfully says it does not know.

Current conversation:

Human: Hi there!
AI:

> Finished chain.
' Hello! How are you today?'
```

```python
output = conversation.predict(input="I'm doing well! Just having a conversation with an AI.")
print(output)
```

```pycon
> Entering new chain...
Prompt after formatting:
The following is a friendly conversation between a human and an AI. The AI is talkative and provides lots of specific details from its context. If the AI does not know the answer to a question, it truthfully says it does not know.

Current conversation:

Human: Hi there!
AI:  Hello! How are you today?
Human: I'm doing well! Just having a conversation with an AI.
AI:

> Finished chain.
" That's great! What would you like to talk about?"
```
## 构建语言模型应用程序：聊天模型

类似地，您可以使用聊天模型而不是LLMs。聊天模型是语言模型的一种变体。虽然聊天模型在底层使用语言模型，但它们提供的接口与“输入文本，输出文本”的API有所不同：它们提供的接口是输入和输出为“聊天消息”的API。

聊天模型API还比较新，因此我们还在研究正确的抽象层。

## 从聊天模型获取消息完成状态

您可以通过向聊天模型传递一个或多个消息来获取聊天完成状态。响应将是一条消息。LangChain当前支持的消息类型包括`AIMessage`、`HumanMessage`、`SystemMessage`和`ChatMessage`——`ChatMessage`带有一个任意的角色参数。大多数时候，您只需要处理`HumanMessage`、`AIMessage`和`SystemMessage`。
```python
from langchain.chat_models import ChatOpenAI
from langchain.schema import (
    AIMessage,
    HumanMessage,
    SystemMessage
)

chat = ChatOpenAI(temperature=0)
```
您可以通过传入一条消息来获得自动完成提示。
```python
chat([HumanMessage(content="Translate this sentence from English to French. I love programming.")])
# -> AIMessage(content="J'aime programmer.", additional_kwargs={})
```
您还可以将多个消息传递给OpenAI的gpt-3.5-turbo和gpt-4模型。
```python
messages = [
    SystemMessage(content="You are a helpful assistant that translates English to French."),
    HumanMessage(content="I love programming.")
]
chat(messages)
# -> AIMessage(content="J'aime programmer.", additional_kwargs={})
```
您可以进一步使用“generate”为多组消息生成已完成的建议。该函数将返回一个带有额外“message”参数的“LLMResult”:
```python
batch_messages = [
    [
        SystemMessage(content="You are a helpful assistant that translates English to French."),
        HumanMessage(content="I love programming.")
    ],
    [
        SystemMessage(content="You are a helpful assistant that translates English to French."),
        HumanMessage(content="I love artificial intelligence.")
    ],
]
result = chat.generate(batch_messages)
result
# -> LLMResult(generations=[[ChatGeneration(text="J'aime programmer.", generation_info=None, message=AIMessage(content="J'aime programmer.", additional_kwargs={}))], [ChatGeneration(text="J'aime l'intelligence artificielle.", generation_info=None, message=AIMessage(content="J'aime l'intelligence artificielle.", additional_kwargs={}))]], llm_output={'token_usage': {'prompt_tokens': 57, 'completion_tokens': 20, 'total_tokens': 77}})
```
您可以从 LLMResult 中恢复诸如 token 使用等信息。
```
result.llm_output['token_usage']
# -> {'prompt_tokens': 57, 'completion_tokens': 20, 'total_tokens': 77}
```
## 聊天提示模板

类似于 LLM，您可以通过使用 `MessagePromptTemplate` 来利用模板。您可以从一个或多个 `MessagePromptTemplate` 构建一个 `ChatPromptTemplate`。您可以使用 `ChatPromptTemplate` 的 `format_prompt` -- 这返回一个 `PromptValue`，您可以将其转换为字符串或 `Message` 对象，具体取决于您是否想将格式化后的值用作llm或聊天模型的输入。

为方便起见，模板上公开了一个 `from_template` 方法。如果您要使用此模板，它将如下所示：
```python
from langchain.chat_models import ChatOpenAI
from langchain.prompts.chat import (
    ChatPromptTemplate,
    SystemMessagePromptTemplate,
    HumanMessagePromptTemplate,
)

chat = ChatOpenAI(temperature=0)

template = "You are a helpful assistant that translates {input_language} to {output_language}."
system_message_prompt = SystemMessagePromptTemplate.from_template(template)
human_template = "{text}"
human_message_prompt = HumanMessagePromptTemplate.from_template(human_template)

chat_prompt = ChatPromptTemplate.from_messages([system_message_prompt, human_message_prompt])

# get a chat completion from the formatted messages
chat(chat_prompt.format_prompt(input_language="English", output_language="French", text="I love programming.").to_messages())
# -> AIMessage(content="J'aime programmer.", additional_kwargs={})
```
## 基于聊天模型的链式结构

如上一节所述，`LLMChain` 也可以与聊天模型一起使用：
```python
from langchain.chat_models import ChatOpenAI
from langchain import LLMChain
from langchain.prompts.chat import (
    ChatPromptTemplate,
    SystemMessagePromptTemplate,
    HumanMessagePromptTemplate,
)

chat = ChatOpenAI(temperature=0)

template = "You are a helpful assistant that translates {input_language} to {output_language}."
system_message_prompt = SystemMessagePromptTemplate.from_template(template)
human_template = "{text}"
human_message_prompt = HumanMessagePromptTemplate.from_template(human_template)
chat_prompt = ChatPromptTemplate.from_messages([system_message_prompt, human_message_prompt])

chain = LLMChain(llm=chat, prompt=chat_prompt)
chain.run(input_language="English", output_language="French", text="I love programming.")
# -> "J'aime programmer."
```
## 带有聊天模型的代理

代理还可以与聊天模型一起使用，您可以使用 `AgentType.CHAT_ZERO_SHOT_REACT_DESCRIPTION` 作为代理类型来初始化一个聊天代理。
```python
from langchain.agents import load_tools
from langchain.agents import initialize_agent
from langchain.agents import AgentType
from langchain.chat_models import ChatOpenAI
from langchain.llms import OpenAI

# First, let's load the language model we're going to use to control the agent.
chat = ChatOpenAI(temperature=0)

# Next, let's load some tools to use. Note that the `llm-math` tool uses an LLM, so we need to pass that in.
llm = OpenAI(temperature=0)
tools = load_tools(["serpapi", "llm-math"], llm=llm)


# Finally, let's initialize an agent with the tools, the language model, and the type of agent we want to use.
agent = initialize_agent(tools, chat, agent=AgentType.CHAT_ZERO_SHOT_REACT_DESCRIPTION, verbose=True)

# Now let's test it out!
agent.run("Who is Olivia Wilde's boyfriend? What is his current age raised to the 0.23 power?")
```

```pycon

> Entering new AgentExecutor chain...
Thought: I need to use a search engine to find Olivia Wilde's boyfriend and a calculator to raise his age to the 0.23 power.
Action:
{
  "action": "Search",
  "action_input": "Olivia Wilde boyfriend"
}

Observation: Sudeikis and Wilde's relationship ended in November 2020. Wilde was publicly served with court documents regarding child custody while she was presenting Don't Worry Darling at CinemaCon 2022. In January 2021, Wilde began dating singer Harry Styles after meeting during the filming of Don't Worry Darling.
Thought:I need to use a search engine to find Harry Styles' current age.
Action:
{
  "action": "Search",
  "action_input": "Harry Styles age"
}

Observation: 29 years
Thought:Now I need to calculate 29 raised to the 0.23 power.
Action:
{
  "action": "Calculator",
  "action_input": "29^0.23"
}

Observation: Answer: 2.169459462491557

Thought:I now know the final answer.
Final Answer: 2.169459462491557

> Finished chain.
'2.169459462491557'
```
## 记忆：将状态添加到链和代理中

您可以将内存与使用聊天模型初始化的链和代理一起使用。与用于LLM的内存的主要区别在于，我们可以将它们保留为其自己的独特内存对象，而不是尝试将所有先前的消息压缩成字符串。
```python
from langchain.prompts import (
    ChatPromptTemplate, 
    MessagesPlaceholder, 
    SystemMessagePromptTemplate, 
    HumanMessagePromptTemplate
)
from langchain.chains import ConversationChain
from langchain.chat_models import ChatOpenAI
from langchain.memory import ConversationBufferMemory

prompt = ChatPromptTemplate.from_messages([
    SystemMessagePromptTemplate.from_template("The following is a friendly conversation between a human and an AI. The AI is talkative and provides lots of specific details from its context. If the AI does not know the answer to a question, it truthfully says it does not know."),
    MessagesPlaceholder(variable_name="history"),
    HumanMessagePromptTemplate.from_template("{input}")
])

llm = ChatOpenAI(temperature=0)
memory = ConversationBufferMemory(return_messages=True)
conversation = ConversationChain(memory=memory, prompt=prompt, llm=llm)

conversation.predict(input="Hi there!")
# -> 'Hello! How can I assist you today?'


conversation.predict(input="I'm doing well! Just having a conversation with an AI.")
# -> "That sounds like fun! I'm happy to chat with you. Is there anything specific you'd like to talk about?"

conversation.predict(input="Tell me about yourself.")
# -> "Sure! I am an AI language model created by OpenAI. I was trained on a large dataset of text from the internet, which allows me to understand and generate human-like language. I can answer questions, provide information, and even have conversations like this one. Is there anything else you'd like to know about me?"
```

