# Unstructured

本页介绍如何在LangChain中使用[`unstructured`](https://github.com/Unstructured-IO/unstructured)生态系统。`Unstructured.IO`的 `unstructured`包可以从原始源文档（如PDF和Word文档）中提取干净的文本。

本页分为两部分：安装和设置，以及对特定的`unstructured`包装器的引用。

## 安装和设置

如果您使用的加载器在本地运行，请使用以下步骤在本地运行`unstructured`及其依赖项。

- 使用命令 `pip install "unstructured[local-inference]"` 安装Python SDK
- 安装以下系统依赖项（如果在您的系统上尚未可用）。 根据您解析的文档类型，您可能不需要所有这些。
    - `libmagic-dev`（文件类型检测）
    - `poppler-utils`（图像和PDF）
    - `tesseract-ocr`（图像和PDF）
    - `libreoffice` （MS Office文档）
    - `pandoc` （EPUB）
- 如果您正在使用“hi_res”策略解析PDF，请运行以下命令安装“detectron2”模型，它是“unstructured”用于布局检测的:
    - `pip install "detectron2@git+https://github.com/facebookresearch/detectron2.git@e2ce8dc#egg=detectron2"`
    - 如果未安装“detectron2”，则“unstructured”会回退到使用“fast”策略处理PDF，该策略直接使用`pdfminer`，并且不需要“detectron2”。

如果您想尽可能少的设置步骤，请运行`pip install unstructured`并使用`UnstructuredAPIFileLoader`或`UnstructuredAPIFileIOLoader`。这将使用托管的Unstructured API处理您的文档。需要注意的是，当前（截至2023年5月1日），Unstructured API是开放的，但它很快将需要API密钥。一旦可用，[Unstructured文档页](https://unstructured-io.github.io/) 将提供如何生成API密钥的说明。请查看说明。
[在这里](https://github.com/Unstructured-IO/unstructured-api#dizzy-instructions-for-using-the-docker-image)
如果您想要自行托管Unstructured API，或者在本地运行它。

## 封装器

### 数据加载器

`langchain`中的主要`unstructured`封装器是数据加载器。以下是如何使用最基本的非结构化数据加载器。在`langchain.document_loaders`模块中提供了其他特定于文件的数据加载器。
```python
from langchain.document_loaders import UnstructuredFileLoader

loader = UnstructuredFileLoader("state_of_the_union.txt")
loader.load()
```
如果您使用 `UnstructuredFileLoader(mode="elements")` 实例化加载器，则在页面编号、文本类型（例如标题、叙述性文本）可用时，加载器将跟踪其他元数据。