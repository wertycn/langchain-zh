# 开始使用

在本教程中，我们将学习以下内容：
- 什么是提示模板以及为什么需要它，
- 如何创建提示模板，
- 如何向提示模板传递少量示例，
- 如何为一个提示模板选择示例。

## 什么是提示模板？

提示模板是一种可复制的生成提示的方式。它包含一个文本字符串（“模板”），可以从最终用户那里接收一组参数并生成提示。

提示模板可以包含：
- 对语言模型的指示，
- 一组少量示例，以帮助语言模型生成更好的响应，
- 对语言模型的问题。

以下代码片段包含一个提示模板的示例：
```python
from langchain import PromptTemplate


template = """
I want you to act as a naming consultant for new companies.
What is a good name for a company that makes {product}?
"""

prompt = PromptTemplate(
    input_variables=["product"],
    template=template,
)
prompt.format(product="colorful socks")
# -> I want you to act as a naming consultant for new companies.
# -> What is a good name for a company that makes colorful socks?
```
## 创建提示模板

您可以使用`PromptTemplate`类创建简单的硬编码提示。提示模板可以接受任意数量的输入变量，并可以格式化生成提示。
```python
from langchain import PromptTemplate

# An example prompt with no input variables
no_input_prompt = PromptTemplate(input_variables=[], template="Tell me a joke.")
no_input_prompt.format()
# -> "Tell me a joke."

# An example prompt with one input variable
one_input_prompt = PromptTemplate(input_variables=["adjective"], template="Tell me a {adjective} joke.")
one_input_prompt.format(adjective="funny")
# -> "Tell me a funny joke."

# An example prompt with multiple input variables
multiple_input_prompt = PromptTemplate(
    input_variables=["adjective", "content"], 
    template="Tell me a {adjective} joke about {content}."
)
multiple_input_prompt.format(adjective="funny", content="chickens")
# -> "Tell me a funny joke about chickens."
```
如果您不想手动指定 `input_variables`，您也可以使用 `from_template` 类方法创建一个 `PromptTemplate`。`langchain` 将根据传递的 `template` 自动推断 `input_variables`。
```python
template = "Tell me a {adjective} joke about {content}."

prompt_template = PromptTemplate.from_template(template)
prompt_template.input_variables
# -> ['adjective', 'content']
prompt_template.format(adjective="funny", content="chickens")
# -> Tell me a funny joke about chickens.
```
您可以创建自定义提示模板，以任何您想要的方式格式化提示。更多信息，请参见[自定义提示模板](examples/custom_prompt_template.ipynb)。

<!-- TODO(shreya): 添加至Jinja的链接 -->

## 模板格式

默认情况下，`PromptTemplate`将把提供的模板视为Python f-string。您可以通过`template_format`参数指定其他模板格式：
```python
# Make sure jinja2 is installed before running this

jinja2_template = "Tell me a {{ adjective }} joke about {{ content }}"
prompt_template = PromptTemplate.from_template(template=jinja2_template, template_format="jinja2")

prompt_template.format(adjective="funny", content="chickens")
# -> Tell me a funny joke about chickens.
```
当前， `PromptTemplate` 仅支持 `jinja2` 和 `f-string` 模板格式。 如果您想使用其他模板格式，请在 [Github](https://github.com/hwchase17/langchain/issues) 页面上开一个问题。

## 验证模板

默认情况下，`PromptTemplate` 将通过检查 `input_variables` 是否与 `template` 定义的变量匹配来验证 `template` 字符串。 您可以通过将 `validate_template` 设置为 `False` 来禁用这种行为。
```python
template = "I am learning langchain because {reason}."

prompt_template = PromptTemplate(template=template, 
                                 input_variables=["reason", "foo"]) # ValueError due to extra variables
prompt_template = PromptTemplate(template=template, 
                                 input_variables=["reason", "foo"], 
                                 validate_template=False) # No error
```
## 序列化提示模板

您可以将您的“PromptTemplate”保存到本地文件系统中。`langchain`会通过文件扩展名自动推断文件格式。目前，“langchain”支持将模板保存到YAML和JSON文件中。
```python
prompt_template.save("awesome_prompt.json") # Save to JSON file
```

```python
from langchain.prompts import load_prompt
loaded_prompt = load_prompt("awesome_prompt.json")

assert prompt_template == loaded_prompt
```
`langchain`还支持从LangChainHub加载提示模板，其中包含一系列您可以在项目中使用的有用提示。您可以在[这里](https://github.com/hwchase17/langchain-hub)阅读有关LangChainHub和其中可用提示的更多信息。
```python

from langchain.prompts import load_prompt

prompt = load_prompt("lc://prompts/conversation/prompt.json")
prompt.format(history="", input="What is 1 + 1?")
```
您可以在[如何序列化提示](examples/prompt_serialization.ipynb)中了解更多关于序列化提示模板的信息。

## 为提示模板添加少量样例

少量样例是一组可用于帮助语言模型生成更好响应的样例。

要生成带有少量样例的提示，您可以使用`FewShotPromptTemplate`。该类接受一个`PromptTemplate`以及一个少量样例的列表。然后，它将使用少量样例格式化提示模板。

在这个例子中，我们将创建一个提示，用于生成单词反义词。
```python
from langchain import PromptTemplate, FewShotPromptTemplate


# First, create the list of few shot examples.
examples = [
    {"word": "happy", "antonym": "sad"},
    {"word": "tall", "antonym": "short"},
]

# Next, we specify the template to format the examples we have provided.
# We use the `PromptTemplate` class for this.
example_formatter_template = """
Word: {word}
Antonym: {antonym}\n
"""
example_prompt = PromptTemplate(
    input_variables=["word", "antonym"],
    template=example_formatter_template,
)

# Finally, we create the `FewShotPromptTemplate` object.
few_shot_prompt = FewShotPromptTemplate(
    # These are the examples we want to insert into the prompt.
    examples=examples,
    # This is how we want to format the examples when we insert them into the prompt.
    example_prompt=example_prompt,
    # The prefix is some text that goes before the examples in the prompt.
    # Usually, this consists of intructions.
    prefix="Give the antonym of every input",
    # The suffix is some text that goes after the examples in the prompt.
    # Usually, this is where the user input will go
    suffix="Word: {input}\nAntonym:",
    # The input variables are the variables that the overall prompt expects.
    input_variables=["input"],
    # The example_separator is the string we will use to join the prefix, examples, and suffix together with.
    example_separator="\n\n",
)

# We can now generate a prompt using the `format` method.
print(few_shot_prompt.format(input="big"))
# -> Give the antonym of every input
# -> 
# -> Word: happy
# -> Antonym: sad
# ->
# -> Word: tall
# -> Antonym: short
# ->
# -> Word: big
# -> Antonym:
```
## 选择适合模板的示例

如果您有大量的示例，可以使用`ExampleSelector` 来选择那些能最好地提供信息以供语言模型学习的示例。这会帮助您生成更容易产生良好响应的提示。

在下面的例子中，我们将使用 `LengthBasedExampleSelector` 来根据输入的长度选择示例。这在您担心构建的提示会超过上下文窗口长度时非常有用。对于较长的输入，它将选择较少的示例进行包含，而对于较短的输入，它将选择更多示例。

我们将继续使用上一节的示例，但这次我们将使用 `LengthBasedExampleSelector` 来选择示例。
```python
from langchain.prompts.example_selector import LengthBasedExampleSelector


# These are a lot of examples of a pretend task of creating antonyms.
examples = [
    {"word": "happy", "antonym": "sad"},
    {"word": "tall", "antonym": "short"},
    {"word": "energetic", "antonym": "lethargic"},
    {"word": "sunny", "antonym": "gloomy"},
    {"word": "windy", "antonym": "calm"},
]

# We'll use the `LengthBasedExampleSelector` to select the examples.
example_selector = LengthBasedExampleSelector(
    # These are the examples is has available to choose from.
    examples=examples, 
    # This is the PromptTemplate being used to format the examples.
    example_prompt=example_prompt, 
    # This is the maximum length that the formatted examples should be.
    # Length is measured by the get_text_length function below.
    max_length=25,
)

# We can now use the `example_selector` to create a `FewShotPromptTemplate`.
dynamic_prompt = FewShotPromptTemplate(
    # We provide an ExampleSelector instead of examples.
    example_selector=example_selector,
    example_prompt=example_prompt,
    prefix="Give the antonym of every input",
    suffix="Word: {input}\nAntonym:",
    input_variables=["input"],
    example_separator="\n\n",
)

# We can now generate a prompt using the `format` method.
print(dynamic_prompt.format(input="big"))
# -> Give the antonym of every input
# ->
# -> Word: happy
# -> Antonym: sad
# ->
# -> Word: tall
# -> Antonym: short
# ->
# -> Word: energetic
# -> Antonym: lethargic
# ->
# -> Word: sunny
# -> Antonym: gloomy
# ->
# -> Word: windy
# -> Antonym: calm
# ->
# -> Word: big
# -> Antonym:
```
相反，如果我们提供了非常长的输入，则“LengthBasedExampleSelector”将选择在提示中包含较少的示例。
```python
long_string = "big and huge and massive and large and gigantic and tall and much much much much much bigger than everything else"
print(dynamic_prompt.format(input=long_string))
# -> Give the antonym of every input

# -> Word: happy
# -> Antonym: sad
# ->
# -> Word: big and huge and massive and large and gigantic and tall and much much much much much bigger than everything else
# -> Antonym:
```
LangChain提供了一些示例选择器供您使用。有关如何使用它们的更多详细信息，请参见[示例选择器](../example_selectors.rst)。

您可以创建自定义示例选择器，这些选择器可以根据您想要的任何条件选择示例。有关如何执行此操作的更多详细信息，请参见[创建自定义示例选择器](../example_selectors/examples/custom_example_selector.md)。