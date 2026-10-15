# AI Agent（智能体）：LangChain 制作智能体

- 来源：[LangChain 制作智能体](https://www.runoob.com/ai-agent/langchain-agent.html)
- 分类：AI / 智能开发
- 技术：AI Agent（智能体）
- 笔记类型：概念卡
- 章节序号：0023

## 本章内容

LangChain 是一个用于构建 LLM 应用的框架，可以把模型调用升级为可组合、可控制、可扩展的应用系统。

LangChain 解决的不是怎么调模型，而是：

- 多步骤推理如何组织
- 外部数据如何接入
- 工具如何被模型安全调用
- 上下文如何被长期管理

开源地址：https://github.com/langchain-ai/langchain。

LangChain 教程：https://www.runoob.com/langchain/langchain-tutorial.html

想象一下，你正在建造一个智能机器人助手，这个助手需要能够理解你的问题、从各种资料中查找信息、进行逻辑推理，最后用自然语言回答你。单独使用像 GPT 这样的语言模型，就像只给机器人装了一个聪明的大脑，但它还缺少手和眼睛——它不知道如何获取外部数据、如何执行具体任务。

LangChain 就是这样一个框架，它充当了连接器和协调者的角色。

LangChain 将强大的语言模型（如 GPT-4、DeepSeek）与外部数据源、计算工具以及记忆系统巧妙地连接起来，构建出功能强大、可实际应用的 AI 应用程序。

简单来说，LangChain 的核心价值在于：让语言模型变得有用，解决了大语言模型（LLM）的几个关键限制：

- 知识实时性：LLM 的训练数据有截止日期，无法获取最新信息。
- 领域专精性：通用 LLM 缺乏特定行业或公司的私有知识。
- 可操作性：LLM 本身无法执行如计算、查询数据库、调用 API 等动作。
- 对话连贯性：在多轮对话中，LLM 需要记住之前的聊天历史。

LangChain 通过一系列标准化的链（Chains）和组件（Components）来组织这些功能，让开发者能够像搭积木一样，快速构建复杂的 AI 应用。

LangChain 模块总览：


### 环境准备

使用国内镜像安装：

```text
pip install langchain langchain-openai langchain-community python-dotenv -i https://mirrors.aliyun.com/pypi/simple/
```

如果你使用 OpenAI 的话，可以配置环境变量：

```text
export OPENAI_API_KEY=你的key
```

然后使用以下代码测试：


## 实例

国内我们可以采用 DeepSeek 大模型来测试，如果还没有需要先去 https://platform.deepseek.com/api_keys 创建一个 API key。

DeepSeek 的 API 文档参考：https://api-docs.deepseek.com/zh-cn/。

如果你需要统一管理多个第三方模型，可以选择安装 LiteLLM 作为模型网关：

```text
pip install -U litellm
```

不过本文的示例直接使用 ChatOpenAI 配合 openai_api_base 参数连接 DeepSeek，无需额外安装 LiteLLM。


## 实例

执行以上代码，就会输出内容：

```text
你好！很高兴认识你！

我是DeepSeek，由深度求索公司创造的AI助手。我的特点包括：
。。。
```


## 构建 LCEL 链 (LangChain Expression Language)

单纯调用模型不够强大，我们需要构建一个标准的处理流程：

```text
Prompt -> LLM -> OutputParser
```

完整代码如下：


## 实例


### 流式输出 (Streaming)

在实际应用（如聊天机器人）中，我们需要像 ChatGPT 那样一个字一个字地吐出文字，而不是等生成完了才一次性显示。

LangChain 对此支持非常简单，使用 .stream() 替代 .invoke()：


## 实例


### 代码结构

- ChatPromptTemplate 明确区分 system / user
- Prompt 是结构化输入函数，不是字符串
- ChatOpenAI 只是统一接口
- LangChain 不增强模型能力，只增强可控性
- 模型输出永远是 Message
- StrOutputParser 是显式类型转换
- 没有 Parser，工程不可控


## 核心组件详解


### 1. 模型 (Models)

LangChain 提供了统一的抽象接口，现在主要推荐使用 Chat Models，因为目前的模型（如 DeepSeek, GPT-4）大多针对对话进行了优化。

- Chat Models: 输入和输出是结构化的消息。
- SystemMessage: 设定 AI 角色。
- HumanMessage: 用户发送的消息。
- AIMessage: AI 返回的消息。


### 2. 提示词 (Prompts)

新版本中，推荐使用 ChatPromptTemplate 来构建对话式提示词，它更符合当前主流 LLM 的调用习惯。

```text
from langchain_core.prompts import ChatPromptTemplate

# 使用 from_messages 构建结构化模板
prompt_template = ChatPromptTemplate.from_messages([
    ("system", "你是一位专业的{role}。"),
    ("user", "{content}")
])

# 动态填充变量
prompt = prompt_template.invoke({"role": "美食评论家", "content": "评价一下这碗炸酱面"})
# 输出：包含 SystemMessage 和 HumanMessage 的列表
```


### 3. 链 (Chains) & LCEL

重要更新： LLMChain 已被弃用。现在使用 LCEL (管道符 |) 语法。这种方式更灵活、支持异步和流式输出。

```text
# 现代写法：Prompt | Model | OutputParser
from langchain_core.output_parsers import StrOutputParser

# 这里的 llm 是 ChatOpenAI(model="deepseek-v4-pro") 的实例
chain = prompt_template | llm | StrOutputParser()

# 调用链
result = chain.invoke({"role": "导游", "content": "介绍一下故宫"})
print(result) # 直接输出字符串
```


### 4. 索引与检索 (Indexes & Retrieval)

这是 RAG (检索增强生成) 的核心。新版本强调了将文档转化为"检索器"的过程。

- 流程: DocumentLoaders (加载) -> TextSplitter (切片) -> Embeddings (向量化) -> VectorStore (存储)。
- Retriever: 不再仅仅是数据库搜索，它是一个可以集成在链中的组件。

```text
# 将向量库转为检索器
retriever = vectorstore.as_retriever()
# 在新版链中引用
# chain = {"context": retriever, "question": RunnablePassthrough()} | prompt | llm
```

完整 RAG 实战示例

下面我们来实现一个完整的 RAG 应用。首先需要安装额外依赖：

```text
pip install langchain-community faiss-cpu sentence-transformers -i https://mirrors.aliyun.com/pypi/simple/
```


## 实例

- FAISS 是 Facebook 开源的向量相似度搜索库，适合本地开发测试，数据存储在内存中
- 生产环境 建议使用 Pinecone、Milvus、Chroma、Weaviate 等专业向量数据库，支持持久化和分布式
- Embedding 模型：本示例使用 HuggingFace 的 all-MiniLM-L6-v2 模型，首次运行会自动下载（约 80MB）
- 如果你有 OpenAI API Key，也可以使用 OpenAIEmbeddings 获得更好的中文效果
- 国内中文场景推荐使用 BAAI/bge-small-zh-v1.5 等中文 Embedding 模型
- chunk_size 和 chunk_overlap 需要根据实际文档特点调优，过大可能丢失精度，过小可能丢失上下文


### 5. 记忆 (Memory)

重要更新： 传统的 ConversationBufferMemory 在复杂的 LCEL 链中较难集成。最新推荐使用 ChatMessageHistory 配合 RunnableWithMessageHistory。

- 核心逻辑: 记忆不再是链的一个属性，而是一个独立的消息存储库，通过 session_id 区分不同用户。
- 持久化: 支持存入 Redis、PostgreSQL 或内存。


### 6. 代理 (Agents)

代理（Agent）是 LangChain 最强大的功能之一。与链（Chain）不同，代理可以根据用户输入自主决策调用哪些工具、以什么顺序执行，是真正的"智能体"。

Agent 的核心循环：接收任务 -> 思考（选择工具）-> 执行工具 -> 观察结果 -> 继续思考或给出最终答案。

使用 @tool 装饰器可以将任何 Python 函数转为 LLM 可调用的工具。LangChain 会自动将函数名和 docstring 传递给模型，让模型知道何时以及如何使用这个工具。

下面是一个完整的 Agent 实战示例，包含天气查询、数学计算和知识搜索三个工具：


## 实例

运行上述代码，你会看到（verbose=True 时的思考链输出）：

```text
==================================================

> Entering new AgentExecutor chain...
Invoking: `get_current_weather` with `{'city': '北京'}`

晴天，气温 28°C，湿度 45%

根据查询结果，北京今天的天气是晴天，气温 28°C，湿度 45%。

> Finished chain.

最终回答: 北京今天天气晴朗，气温 28°C，湿度 45%，适合外出活动。

==================================================

> Entering new AgentExecutor chain...
Invoking: `calculate` with `{'expression': '(15 * 37 + 228) / 3'}`

计算结果：(15 * 37 + 228) / 3 = 261.0

> Finished chain.

最终回答: (15 * 37 + 228) / 3 的计算结果是 261.0

==================================================

> Entering new AgentExecutor chain...
Invoking: `search_knowledge` with `{'query': 'LangChain'}`
Invoking: `calculate` with `{'expression': '2 ** 10'}`

LangChain 是一个用于构建 LLM 应用的开源框架...
计算结果：2 ** 10 = 1024

> Finished chain.

最终回答: LangChain 是一个用于构建 LLM 应用的开源框架，支持链式调用、记忆管理和工具集成。另外，2 的 10 次方等于 1024。
```

- verbose=True 让我们看到 Agent 的完整决策链路，便于调试和理解其行为
- Agent 会自动判断需要调用什么工具，不需要人工指定调用顺序
- 如果问题不需要工具（如简单的闲聊），Agent 会直接用自身知识回答
- 对于复杂问题，Agent 可能会多次调用工具，甚至并行调用多个工具


## 快速开始：构建你的第一个 LangChain 应用

让我们通过一个简单的例子，感受一下 LangChain 的便捷性。

实际的开发中，我们可以把 API 的相关信息保存在项目根目录的 .env 文件中，方便使用。

```text
# .env 文件内容
DEEPSEEK_API_KEY=sk-xxx
DEEPSEEK_BASE_URL=https://api.deepseek.com
DEEPSEEK_MODEL=deepseek-v4-pro
```


### 示例 1：基础问答链


## 实例


### 示例 2：带记忆的对话链

让我们创建一个能记住对话历史的简单聊天机器人。


## 实例

运行上述代码，你会看到：

```text
--- 已进入 DeepSeek 聊天模式 (输入 'exit' 退出) ---
你: 你好
AI: 你好！很高兴见到你！ 有什么我可以帮助你的吗？无论是回答问题、聊天，还是协助解决问题，我都很乐意为你提供帮助！

你: 我叫小明
AI: 你好，小明！很高兴认识你！
如果你有任何问题、想法，或者需要帮助的地方，随时告诉我哦～

你: 我叫什么记得吗？
AI: 当然记得！你刚刚告诉我你叫**小明**～
我会认真记住我们的对话内容，在之后的交流中尽量保持上下文连贯。不过如果对话过长或间隔太久，我可能需要你提醒一下哦～
有什么想聊的或需要帮助的吗？
```


## 总结

本文介绍了 LangChain 框架的核心概念和实战应用。LangChain 通过标准化的组件和链式调用，让开发者能够快速构建功能强大的 AI 应用。

下表总结了本文涉及的核心知识点：


### 推荐学习路径


## 记忆卡片

- 一句话定义：`LangChain 制作智能体` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
