# LangChain：LangChain 个人知识库问答系统

- 来源：[LangChain 个人知识库](https://www.runoob.com/langchain/langchain-project-knowledge-qa.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：学习笔记
- 章节序号：0299

## 本章内容

前面我们已经学习了 LangChain RAG 的基本原理，以及如何将 Retriever 封装成 Agent 工具。

本章节将进一步构建一个 个人知识库问答系统，支持导入 Markdown、TXT 和 PDF 文件，自动建立向量索引，并使用大语言模型回答文档相关的问题。

例如，将自己的编程笔记、PDF 教材、技术文档和项目说明导入知识库，之后便可以直接提问：

- 这份 PDF 主要讲了哪些内容？
- 我的 Python 笔记中有哪些关于装饰器的说明？
- 这几个文档对同一个问题有什么不同解释？
- 某个知识点出现在文档的哪一页？

本项目基于 LangChain 1.x，使用 DeepSeek 作为聊天模型、阿里百炼作为 Embedding 模型，并通过 Chroma 将知识库保存在本地。


## 一、系统功能与架构

我们的知识库系统需要实现以下功能：


### 整体工作流程

```text
【知识库构建】

Markdown / TXT / PDF
          ↓
     Document Loader
          ↓
       Document
          ↓
      Text Splitter
          ↓
       文档 Chunk
          ↓
      Embedding 模型
          ↓
     Chroma 向量库


【用户问答】

        用户问题
            ↓
       RAG Agent
            ↓
    search_knowledge
            ↓
        Retriever
            ↓
        相关文档
            ↓
      DeepSeek 模型
            ↓
     回答 + 来源信息
```

知识库构建和问答是两个不同的阶段。文档不变时，无需在每次提问时重新计算全部向量。


## 二、环境准备

建议使用 Python 3.11 或更新的兼容版本。


### 安装依赖

```text
pip install -U langchain langgraph langchain-deepseek langchain-openai langchain-community langchain-chroma langchain-text-splitters pypdf python-dotenv
```

主要依赖说明：


### 配置 API Key

在项目根目录新建 .env：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
DASHSCOPE_API_KEY=your_dashscope_api_key
```

其中：

- DeepSeek 用于理解问题和生成回答。
- 阿里百炼 text-embedding-v4 用于文档和查询向量化。

如果没有配置阿里百炼，可以参考上一章节，将 Embedding 替换为 OpenAI 的 text-embedding-3-small。

注意：向量数据库建立后，不能随意更换 Embedding 模型或向量维度。如果更换模型，应建立新的集合并重新向量化文档。


## 三、项目目录结构

建议创建以下目录：

```text
personal-knowledge-base/
│
├── .env
├── knowledge_qa.py
│
├── docs/
│   ├── python.md
│   ├── notes.txt
│   └── manual.pdf
│
└── my_knowledge_db/
    └── Chroma 数据文件
```

docs/ 用于保存本地文档；my_knowledge_db/ 由 Chroma 自动维护。

示例中的 docs/ 也可以是其他本地目录。使用文件时，应确保路径存在，并且程序有读取权限。


## 四、创建 KnowledgeBase 知识库类

为了方便后续扩展，我们将文档加载、索引更新、检索和删除功能集中在一个类中。

核心接口设计如下：

另外，我们还将为文档建立稳定的 ID，避免重复运行程序就新增一批重复向量。


## 五、初始化 Embedding 与 Chroma

首先创建知识库的初始化部分。


## 实例

主要参数说明：

- chunk_size=500：目标片段长度为 500 个字符。
- chunk_overlap=80：希望相邻片段保留部分上下文。
- add_start_index=True：记录文本片段的起始字符位置。
- persist_directory：保存本地向量数据库。

注意，chunk_overlap 不是保证每两个片段都恰好重叠 80 个字符。

此外，chunk_size=10 和 chunk_size=500 是两个完全不同的参数：前者属于 Embedding 批量请求，后者属于文本切分。


## 六、根据文件格式加载文档

知识库支持三种文件类型：

对于 Markdown，使用 TextLoader 可以直接读取 Markdown 原文，包括标题和代码块。

如果希望按 Markdown 标题切分，可以进一步使用 MarkdownHeaderTextSplitter。


### 实例：按文件类型选择 Loader


## 实例

这里明确限制支持的文件格式，不会将 DOCX、图片或其他二进制文件错误地当作普通文本读取。


### PDF 页码

PyPDFLoader 通常会在 metadata 中加入：

```text
{
    "source": "docs/manual.pdf",
    "page": 0
}
```

其中 page 一般从 0 开始。

向用户展示时，应转换为从第 1 页开始的页码。

注意：对于扫描件 PDF，如果正文只是图片，普通 PyPDFLoader 可能提取不到文字，需要先执行 OCR。


## 七、完整 KnowledgeBase 类

下面实现一个支持持久化和增量更新的知识库管理器。

增量更新的处理方式：

```text
读取文件
    ↓
计算文件内容哈希
    ↓
检查已有索引
    ↓
是否已经索引相同版本？
    ├── 是 → 跳过
    └── 否 → 加载并切分
              ↓
          生成新向量
              ↓
          删除旧片段
              ↓
          完成更新
```

这里利用 Chroma 保存的 metadata 查找指定来源的旧片段，并通过固定 ID 识别文件版本。


## 完整实例：KnowledgeBase

这个类解决了原文最重要的一个问题：重复运行程序，不再默认重复添加全部文档。

例如，同一文件第一次导入时生成向量；第二次导入发现哈希相同，就直接跳过。

文件被修改后，程序会添加新版本片段，并删除此前的旧片段。

注意：这是一套适合本地、单进程使用的增量更新实现，不具备数据库事务级的原子性。多进程并发写入、程序在更新过程中崩溃以及复杂的索引版本管理，需要在生产环境中另行设计。

这里的 source_key 来自规范化绝对路径。同名但路径不同的文件可以分开管理；如果移动文件路径，它会被视为新的来源。


## 八、添加 Markdown、TXT、PDF 文件

创建 KnowledgeBase 实例后，就可以导入真实文档。


### 实例：导入单个文件


## 实例

程序会自动根据扩展名选择 Loader。

例如：

```text
[已更新] python.md：8 个片段
[已更新] notes.txt：3 个片段
[已更新] manual.pdf：25 个片段
```

这里的片段数量仅为示例，实际结果取决于原始文档内容与切分参数。


### 批量导入整个目录


## 实例

当目录中有多个文件时，可以逐个导入。

对导入失败的文档打印错误，不影响其他文件继续处理。

注意：这种演示代码用于本地可信文档目录。正式提供文件上传功能时，还需要限制文件大小、格式、解析资源和访问路径，不能直接允许用户任意指定服务器文件路径。


## 九、增量更新与文档删除

知识库不是一次性建立后永远不变。

例如：

- 修改了 Markdown 学习笔记。
- 重新上传新版 PDF。
- 删除已经过时的说明文档。

对于这类需求，可以直接使用前面提供的 add_file() 和 remove_file()。


### 更新文档


## 实例


### 删除文档


## 后续章节

- 实例
- 十、检索知识库
- 实例：查询 Python 学习资料
- 实例
- 十一、给检索结果添加来源信息
- 实例：格式化文档引用
- 实例
- 十二、将知识库集成到 Agent
- 实例：创建搜索工具
- 实例
- 十三、创建 RAG Agent
- 实例
- 十四、普通问答：显示检索结果与最终回答
- 实例：ask()
- 实例
- 十五、流式输出：逐步显示回答

## 复习重点

- 能说明 `LangChain 个人知识库` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
