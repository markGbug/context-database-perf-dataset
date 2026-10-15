# LangChain：LangChain 构建 RAG Agent

- 来源：[LangChain RAG Agent](https://www.runoob.com/langchain/langchainrag-agent.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：学习笔记
- 章节序号：0297

## 本章内容

前两篇我们已经介绍了 LangChain 的 RAG 基础，包括文档加载、文本切分、Embedding 向量化以及 Chroma 向量数据库。

本章节将这些组件组合起来，构建一个完整的 RAG Agent（检索增强智能体）。

与普通 RAG 不同，RAG Agent 可以将知识库检索封装为 Tool，由大语言模型判断什么时候需要搜索，再根据检索结果生成回答。

例如，用户询问菜鸟教程 RUNOOB 的课程信息时，Agent 可以先搜索知识库，再根据找到的资料回答。

本教程基于 LangChain 1.x，使用 DeepSeek 作为聊天模型，OpenAI 或阿里百炼作为 Embedding 模型，Chroma 作为向量数据库。


## 一、RAG Agent 是什么？

RAG Agent 是将 RAG 检索能力集成到 Agent 工具系统中的一种实现方式。

普通 RAG 的执行过程通常是固定的：

```text
用户问题
    ↓
知识库检索
    ↓
检索到的文档
    ↓
大模型生成回答
```

而 RAG Agent 的执行过程是：

```text
用户问题
    ↓
Agent 判断是否需要检索
    ↓
是否调用知识库工具？
    ├── 是 → Retriever → 返回相关文档
    │                       ↓
    │                 Agent 读取资料
    │                       ↓
    │                 生成最终回答
    │
    └── 否 → 直接生成回答
```

因此，RAG Agent 的关键在于：把 Retriever 包装成 Agent 可以调用的 Tool。


### 普通 RAG 与 RAG Agent 对比

注意：RAG Agent 不一定比普通 RAG 更准确。如果业务要求每个回答都必须先查阅知识库，2-step RAG 通常更容易保证这一流程。


## 二、环境准备

先安装本教程所需的 Python 包：

```text
pip install -U langchain langchain-deepseek langchain-openai langchain-chroma langchain-text-splitters python-dotenv
```

主要组件：


### 配置 API Key

在项目目录下创建 .env：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key

# 使用阿里百炼 Embedding
DASHSCOPE_API_KEY=your_dashscope_api_key

# 使用 OpenAI Embedding 时配置
OPENAI_API_KEY=your_openai_api_key
```

聊天模型和 Embedding 模型可以来自不同服务商。

本教程的完整示例默认使用阿里百炼 Embedding，便于不使用 OpenAI API Key 的读者运行。


## 三、初始化 Embedding 模型

Embedding 用于把知识文档和用户查询转换成向量。

这里提供两种方案，选择其中一种即可。


### 方式一：OpenAI Embedding


## 实例（OpenAI）

text-embedding-3-small 默认输出 1536 维向量。


### 方式二：阿里百炼 Embedding

如果没有 OpenAI API Key，可以使用阿里百炼的 text-embedding-v4。

百炼提供 OpenAI 兼容接口，可以通过 OpenAIEmbeddings 调用。


## 实例（阿里百炼）

使用默认设置时，text-embedding-v4 通常输出 1024 维向量。

这里的两个参数需要注意：

- check_embedding_ctx_length=False：避免 OpenAI 专用的 Token ID 预处理与百炼兼容接口发生冲突。
- chunk_size=10：限制 Embedding 批量请求的文本条数。

也可以参考：LangChain 阿里百炼配置教程。

重要：创建索引和执行检索时必须使用兼容的同一 Embedding 模型。不能把 OpenAI 和阿里百炼生成的向量混合到同一个已有集合中。


## 四、准备知识库文档

下面使用几条教学模拟资料，构建一个小型编程课程知识库。

这些资料是为了演示 RAG 流程而编写的测试数据，不代表真实课程数量、网站历史或会员服务信息。


### 实例：创建 Document


## 实例

这里使用 Document 而不是普通字符串，是因为 Document 可以保存来源元数据。

后续检索时，可以通过 metadata 获取资料标题和来源标识。


## 五、切分文档

对于长篇教程、PDF 或 Markdown，通常需要先切分成较小的 Chunk。

可以使用 RecursiveCharacterTextSplitter。


### 实例：切分中文资料


## 实例

由于当前演示文档很短，每个 Document 通常仍然只有一个 Chunk。

实际项目中，可以通过 Document Loader 加载大量真实资料，再使用相同的方法切分。

注意：chunk_size 是目标字符长度，不保证每个 Chunk 都恰好为 300 字符。


## 六、创建 Chroma 向量数据库

接下来将 Chunk 转换为向量，存入 Chroma。

这里使用本地持久化目录，避免程序重启后丢失向量数据。


### 实例：创建向量存储


## 实例

主要参数：

添加文档：


## 实例

这里使用内容相关的固定 ID，方便识别文档。

但如果原始文档发生修改，仍然需要删除旧版本的片段并重新建立索引，不能依赖固定 ID 自动完成整个文档同步过程。


## 七、创建 Retriever 检索器

向量数据库建立后，通过 as_retriever() 获取标准化检索接口。


## 实例

k=3 表示最多返回三个相关片段。

向量检索返回的是相对相关的候选资料，不代表每个结果都能正确回答用户问题。

如果知识库很大，可以进一步使用元数据过滤、相似度阈值或重排序模型改善检索质量。


## 八、将 Retriever 包装成 Tool

这是构建 RAG Agent 最关键的一步。

通过 @tool 把 Retriever 封装成模型可调用的工具。


### 实例：search_knowledge_base


## 实例

例如调用：

```text
search_knowledge_base("Python 函数怎么定义？")
```

工具可能返回：

```text
[来源1] 标题：Python 函数说明
来源ID：demo-python-functions
内容：Python 函数使用 def 定义，可以接收参数、返回结果，并封装重复逻辑。
```

模型可以根据返回资料进行回答。

注意：这是提供给模型的文本来源标识，并不代表模型自动完成了事实核查。


## 后续章节

- 九、创建 RAG Agent
- 实例：使用 DeepSeek 创建 Agent
- 实例
- 十、测试 RAG Agent
- 实例
- 十一、查看 Agent 是否真的调用了检索工具
- 实例：查看工具调用记录
- 实例
- 十二、添加文档来源引用
- 实例：带来源的检索工具
- 实例
- 十三、当知识库没有答案时怎么办？
- 十四、向量数据库持久化
- 首次建立数据库
- 实例
- 后续直接连接

## 复习重点

- 能说明 `LangChain RAG Agent` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
