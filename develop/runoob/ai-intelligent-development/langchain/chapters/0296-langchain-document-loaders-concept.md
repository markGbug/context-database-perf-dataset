# LangChain：LangChain 文档加载与切分

- 来源：[LangChain 文档加载](https://www.runoob.com/langchain/langchain-document-loaders.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：概念卡
- 章节序号：0296

## 本章内容

上一章节我们介绍了 LangChain RAG，通过 Embedding 和向量数据库，让大模型能够根据外部知识回答问题。

但之前的示例主要使用手动编写的文本。在实际项目中，知识库可能来自 PDF、网页、Markdown、TXT、CSV，甚至整个文档目录。

要将这些内容用于 RAG，通常需要先经过两个步骤：Document Loader（文档加载） 和 Text Splitter（文本切分）。

本章节基于 LangChain 1.x，介绍常用文档加载器、Document 对象、中文文本切分、Markdown 标题切分以及完整的文档向量化流程。


## 一、为什么需要文档加载与切分？

一个典型的 RAG 知识库建立流程如下：

```text
PDF / TXT / Markdown / 网页
              ↓
        Document Loader
              ↓
        Document 对象
              ↓
         Text Splitter
              ↓
        多个文档 Chunk
              ↓
        Embedding 模型
              ↓
          VectorStore
              ↓
        Retriever 检索
```

两个组件的职责不同：

文档切分的目的不只是满足模型长度限制，更重要的是提高知识检索的准确性。

例如，一份包含 100 个 Python 知识点的教程，如果整个文档只生成一个向量，搜索某个具体知识点时，可能受到大量无关内容的干扰。

将文档合理拆分后，检索系统就可以返回与问题更加相关的片段。


## 二、Document：LangChain 的统一文档格式

无论加载 TXT、PDF 还是网页，LangChain 通常都会将内容转换为 Document 对象。

Document 包含三个常用字段：


### 实例：手动创建 Document


## 实例

输出：

```text
内容： Python 是一种通用编程语言，适合初学者学习。
来源： python-tutorial.txt
```

metadata 非常重要，后续 RAG 检索可以利用它展示文档来源、过滤用户权限或定位原始资料。


## 三、常用 Document Loader

LangChain 提供多种文档加载器，覆盖常见的文件和网页内容。

常用依赖安装：

```text
pip install -U langchain-core langchain-community langchain-text-splitters pypdf beautifulsoup4 unstructured python-dotenv
```

如果需要构建向量知识库，可以继续安装：

```text
pip install -U langchain-openai langchain-chroma
```

注意，不同 Loader 可能还有额外依赖。应根据实际文件格式安装，不需要一次性安装所有文档解析库。


## 四、TextLoader：加载 TXT 文件

TextLoader 用于读取本地纯文本文件，是最简单的文档加载器。

例如创建 knowledge.txt：

```text
Python 是一种常用的编程语言。
Python 支持面向对象编程。
初学者可以先学习变量、列表、循环和函数。
```


### 实例：读取文本文件


## 实例

对于普通 TXT，通常会返回一个 Document，其元数据包含源文件路径。

例如：

```text
文档数量： 1
元数据： {'source': 'knowledge.txt'}
```

注意：load() 读取文件并返回 Document 列表，不代表文本已经完成切分。

对于较大的文本文件，还需要使用 Text Splitter。


## 五、PyPDFLoader：加载 PDF 文档

PDF 是企业知识库中常见的文档格式。

LangChain 可以使用 PyPDFLoader 提取 PDF 中的文本内容。


### 实例：读取 PDF


## 实例

通常情况下，按页加载 PDF 时，每页会生成一个 Document。

元数据可能包含：

```text
{
    "source": "python-guide.pdf",
    "page": 0
}
```

其中页码通常从 0 开始。面向普通用户显示页码时，可以根据实际情况加 1。


### 扫描件 PDF 如何处理？

需要特别注意，PDF 不一定包含可提取的文字。

例如：

- 普通电子 PDF：通常可以直接提取文本。
- 扫描件 PDF：页面可能是图片，需要 OCR。
- 复杂表格 PDF：文本顺序可能与视觉布局不同。
- 双栏论文：可能需要进行阅读顺序和版面分析。

因此，对于合同、财务报表、试卷等需要高准确率的文件，不能只依赖 PDF 文本提取结果，应根据需要增加 OCR、版面分析与人工核对。


## 六、WebBaseLoader：加载网页

WebBaseLoader 可以读取网页并提取 HTML 中的文本。

例如，读取一个编程教程页面：


## 实例

需要注意，网页加载通常得到的是页面文本，不一定只有文章正文。

例如页面还可能包含：

- 顶部导航。
- 侧边栏。
- 底部版权信息。
- 相关推荐。
- 广告或其他非正文元素。

如果要将网页用于 RAG，建议进一步提取文章主内容，避免导航和重复页面元素影响检索。

注意：WebBaseLoader 不是完整浏览器。对于依赖 JavaScript 动态加载内容的网页，普通 HTTP 加载可能无法取得最终渲染后的文章。

批量抓取网站前，还应遵守目标网站的访问规则，并设置合理的请求频率。


## 七、CSVLoader：加载 CSV 数据

除了普通文档，LangChain 也可以加载 CSV 表格数据。

例如创建 courses.csv：

```text
name,level,category
Python基础,入门,Python
Java基础,入门,Java
HTML基础,入门,前端
```


### 实例：读取 CSV


## 实例

CSVLoader 通常会将每一行转换为一个 Document。

但要注意，CSV 中的大量数字、金额、统计指标，不一定适合全部转换为向量进行计算。

如果任务涉及精确筛选、求和、排序或统计，通常应该使用数据库、SQL 或 pandas 等结构化数据工具。


## 八、Markdown 文档加载

Markdown 常用于技术教程、开发文档和项目 README。

可以使用 UnstructuredMarkdownLoader 加载：


## 实例

这个示例会将 Markdown 解析为文本 Document。

对于希望保留标题层级的 Markdown 知识库，还可以结合 MarkdownHeaderTextSplitter 按标题切分。

这通常比单纯按照固定字符数拆分技术文档更有利于保留章节结构。


## 九、DirectoryLoader：批量加载整个目录

实际项目可能有几十甚至上百个文档。

可以使用 DirectoryLoader 按文件类型批量加载。

例如：

```text
knowledge/
    ├── python.txt
    ├── java.txt
    └── html.txt
```


### 实例：批量读取 TXT


## 实例

其中：

- glob：指定匹配的文件。
- loader_cls：指定实际使用的加载器。
- loader_kwargs：传入加载器参数。
- silent_errors：是否忽略部分加载错误。

如果目录中同时存在 PDF、TXT 和 Markdown，可以分别使用对应加载器读取，再合并 Document 列表。


## 十、Text Splitter：文档切分

文档加载完成后，下一步是将长文本拆分成适合检索的片段。

LangChain 将这些片段称为 Chunk。

例如：

```text
一篇 3000 字的文章
         ↓
      TextSplitter
         ↓
Chunk 1：Python 基础语法
Chunk 2：变量与数据类型
Chunk 3：条件判断
Chunk 4：循环语句
Chunk 5：函数和模块
         ↓
      分别建立向量索引
```

理想情况下，每个 Chunk 应包含足够独立的知识内容，同时不要引入过多无关信息。


## 十一、RecursiveCharacterTextSplitter

RecursiveCharacterTextSplitter 是 LangChain 推荐的通用文本切分器。

它会按照一组分隔符递归尝试切分文本，尽可能保留段落、句子等自然结构。

对于中文内容，建议显式添加中文标点。


## 后续章节

- 实例：切分中文教程
- 实例
- 十二、chunk_size 与 chunk_overlap
- chunk_size
- chunk_overlap
- 十三、切分参数设置指南
- 十四、split_text() 与 split_documents()
- 实例：保留来源信息
- 实例
- 十五、MarkdownHeaderTextSplitter：按照标题切分
- 实例：保留 Markdown 标题信息
- 实例
- 十六、如何处理代码文档？
- 实例：切分 Python 代码
- 实例
- 十七、完整流程：加载、切分、向量化

## 记忆卡片

- 一句话定义：`LangChain 文档加载` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
