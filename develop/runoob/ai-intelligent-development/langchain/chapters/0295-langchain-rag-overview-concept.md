# LangChain：LangChain RAG——检索增强生成

- 来源：[LangChain RAG](https://www.runoob.com/langchain/langchain-rag-overview.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：概念卡
- 章节序号：0295

## 本章内容

大语言模型虽然具备丰富的知识，但并不一定知道你的私有文档、企业资料或最新更新的内容。

例如，你希望 AI 根据公司的内部文档、个人笔记或者编程教程回答问题，如果只依赖模型本身，它可能无法获得这些信息，甚至生成看似合理但实际错误的答案。

这时就可以使用 RAG（Retrieval-Augmented Generation，检索增强生成）。

RAG 的核心思想是：先从知识库检索相关资料，再将资料交给大模型生成回答。

不需要重新训练或微调模型，就可以让应用利用自己的文档知识。

本章节基于 LangChain 1.x，使用 DeepSeek、OpenAI 或阿里百炼 Embedding，以及 Chroma 向量数据库，完成从文档索引到 RAG 问答的完整流程。


## 一、什么是 RAG？

RAG 是将信息检索与大模型生成相结合的一种技术。

传统模型主要依赖训练阶段获得的知识，以及本次请求中提供的上下文。

而 RAG 可以在回答之前，从外部知识库检索相关内容。

例如，用户提问：

```text
Python 入门课程主要包含哪些内容？
```

RAG 系统可以先搜索教程资料，找到相关段落，再让模型根据检索内容组织回答。

通常分为两个阶段：

- 索引阶段：加载文档、清洗、切分、生成向量并存储。
- 检索与生成阶段：接收问题、检索相关内容、组织上下文、调用模型生成回答。

需要注意，RAG 不等于简单的向量搜索。向量搜索负责寻找资料，而 RAG 还需要使用这些资料生成最终回答。


## 二、RAG 工作流程

一个典型的 RAG 系统包括以下环节：

```text
【索引阶段】

原始文档（TXT、PDF、HTML）
           ↓
      DocumentLoader
           ↓
       TextSplitter
           ↓
       文档片段 Chunk
           ↓
      Embedding 模型
           ↓
       向量数据库 Chroma


【检索与生成阶段】

         用户问题
             ↓
       Embedding 模型
             ↓
       向量相似度检索
             ↓
       相关 Document
             ↓
     检索资料 + 用户问题
             ↓
         大语言模型
             ↓
        带来源的回答
```

整个流程涉及几个重要组件：


## 三、安装依赖与环境准备

本教程使用 LangChain 1.x、Chroma 和 DeepSeek。

安装依赖：

```text
pip install -U langchain langchain-core langchain-deepseek langchain-openai langchain-chroma chromadb langchain-text-splitters langchain-community pypdf python-dotenv
```

主要依赖说明：

创建 .env 文件：

```text
# DeepSeek 聊天模型
DEEPSEEK_API_KEY=your_deepseek_api_key

# 方式一：OpenAI Embedding
OPENAI_API_KEY=your_openai_api_key

# 方式二：阿里百炼 Embedding
DASHSCOPE_API_KEY=your_dashscope_api_key
```

其中 OpenAI 和阿里百炼 Embedding 只需要选择其中一种，不必同时配置两个 Key。

注意：DeepSeek 在本教程中主要用于生成最终回答，Embedding 使用单独的向量模型。聊天模型和 Embedding 模型不是同一回事。


## 四、什么是 Embedding？

Embedding（文本嵌入）可以将文本转换为一组浮点数，也就是向量。

例如：

```text
Python 是一种编程语言
        ↓
Embedding 模型
        ↓
[0.012, -0.026, 0.031, ...]
```

语义相近的文本，生成的向量通常也会在向量空间中更接近。

例如：

```text
如何学习 Python？

Python 初学者学习路线

怎样入门 Python 编程？
```

这些文本虽然用词不同，但语义有一定关联，因此可以利用向量检索寻找相似内容。

LangChain Embedding 接口主要提供两个方法：

注意：Embedding 向量本身不是可读的知识文本。向量数据库通常还需要关联原始文本和来源元数据，才能在检索后提供给模型使用。


## 五、方式一：使用 OpenAI Embedding

LangChain 通过 OpenAIEmbeddings 调用 OpenAI 文本嵌入模型。

这里使用 text-embedding-3-small，默认生成 1536 维向量。


### 实例：将文本转换成向量


## 实例

成功时会得到类似：

```text
原始文本： 菜鸟教程 RUNOOB 是一个编程学习平台
向量维度： 1536
前5个数值： [0.012, -0.004, 0.023, ...]
```

具体向量数值由模型返回，不同文本会产生不同结果。

实际代码中不应把展示用的示例向量当作真实输出。


## 六、方式二：使用阿里百炼 Embedding

如果不使用 OpenAI Embedding，也可以选择阿里云百炼提供的 text-embedding-v4。

百炼支持 OpenAI 兼容的 Embedding API，可以使用 langchain-openai 中的 OpenAIEmbeddings，指定对应的 API 地址。

该模型默认输出 1024 维向量，也可以根据服务支持情况指定其他维度。

需要关注两个兼容参数：

- check_embedding_ctx_length=False：避免使用 OpenAI 专用的 Token ID 预处理方式，向兼容接口传入文本字符串。
- chunk_size=10：限制每批请求中的文本数量，适配 text-embedding-v4 的批量输入上限。


### 实例：百炼 text-embedding-v4


## 实例

使用默认维度时，通常输出：

```text
原始文本： 菜鸟教程 RUNOOB 是一个编程学习平台
向量维度： 1024
前5个数值： [...]
```

这里使用北京地域的传统兼容地址。百炼也提供业务空间专属地址，生产环境建议根据 API Key 所属地域和业务空间使用对应的服务端点。

注意：chunk_size=10 限制的是每批 Embedding 请求的文本条数，不是每个文档片段的字符数，也不是 TextSplitter 的 chunk_size。


### 两种 Embedding 的选择

重要：创建知识库和检索知识库时，应使用同一套兼容的 Embedding 配置。不能随意将 OpenAI 的向量与百炼的向量混用，即使维度相同，也不代表向量空间兼容。


## 七、Document：LangChain 的文档对象

LangChain 使用 Document 表示一段文本及其元数据。

最常见的字段有：

- page_content：文档的文本内容。
- metadata：文档来源、分类、页码等附加信息。
- id：可选的文档标识。


### 实例：创建课程文档


## 实例

相比只保存普通字符串，Document 的优点是可以将文本与来源信息关联起来。

后续生成 RAG 回答时，可以利用 metadata 展示参考文档。


## 八、DocumentLoader：加载真实文档

实际项目通常不会将知识内容手动写成字符串列表，而是直接读取 TXT、PDF、Markdown 或其他文档。


### 实例：读取 TXT 文件


## 实例

这里会读取当前目录下的 python_tutorial.txt。

如果文件不存在，需要先创建对应文本文件。


### 实例：读取 PDF 文件


## 实例

通常每一页 PDF 会产生一个 Document，并在 metadata 中保留页码等信息。

注意：PyPDFLoader 对可提取文本的 PDF 比较适合。对于扫描件、拍照合同或图片型 PDF，通常需要先通过 OCR 识别文字，不能假设 PDF Loader 能准确提取其中的全部内容。


## 九、TextSplitter：将长文档切分成 Chunk

直接把一本教程或一份几十页的 PDF 作为一个整体向量化，往往不利于检索具体知识点。

因此，RAG 通常需要先将文档切分成多个较小的片段，称为 Chunk。

LangChain 推荐使用 RecursiveCharacterTextSplitter 处理常规文本。


### 实例：切分文档


## 实例

主要参数：

默认长度计算一般以字符为单位，而不是模型 Token 数量。

对于普通文档，可以先尝试：

```text
chunk_size=800
chunk_overlap=150
```

之后根据文档结构、检索效果和模型上下文窗口调整。

注意：chunk_size 和 chunk_overlap 没有适合所有文档的固定最佳值。过小可能丢失上下文，过大则可能引入较多无关内容。


## 十、创建 Chroma 向量存储

Chroma 是一个适合 RAG 入门的向量数据库。

通过 langchain-chroma，可以使用统一的 VectorStore 接口添加和搜索文档。

下面继续使用前面创建的 embeddings。


### 实例：初始化 Chroma


## 后续章节

- 实例
- 十一、向向量数据库添加文档
- 实例：添加课程知识
- 实例
- 十二、使用 similarity_search() 语义搜索
- 实例：查找 Python 教程
- 实例
- 查看相似度分数
- 实例
- 十三、创建 Retriever 检索器
- 实例：创建检索器
- 实例
- 常见检索方式
- 十四、完整 RAG：根据检索结果生成回答
- 实例：检索增强问答
- 实例

## 记忆卡片

- 一句话定义：`LangChain RAG` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
