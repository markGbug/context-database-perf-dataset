# LangChain：LangChain 集成阿里百炼

- 来源：[LangChain 集成阿里百炼](https://www.runoob.com/langchain/langchain-alibailian.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：练习笔记
- 章节序号：0270

## 本章内容

LangChain 是当下最主流的大模型应用开发框架，它通过统一的组件接口帮助开发者快速搭建提示词、模型、工具链与智能体应用。

阿里云百炼（DashScope）是阿里云的大模型服务平台，提供通义千问（qwen）系列聊天模型、文本嵌入模型和重排序模型。

本文介绍如何把百炼模型接入 LangChain，覆盖聊天模型、文本嵌入模型、重排序模型三大类，并给出 Python、JavaScript、Java 三种语言的完整示例。


### 前置准备

我们需要开通阿里云百炼模型服务并获得 API-KEY。

我们可以先使用阿里云主账号访问百炼模型服务平台：https://bailian.console.aliyun.com/，然后点击右上角登录，登录成功后点击右上角的齿轮⚙️图标，选择 API key，然后复制 API key，如果没有也可以创建 API key：

在动手之前，先理解两个关键概念：LangChain 的「模型接入类」，以及百炼的「两种接入模式」。


### 模型接入类

LangChain 把不同供应商的模型封装成统一的「接入类」。

应用代码面向统一接口编程，切换供应商时只需更换接入类与参数，业务逻辑几乎不用改动。

以聊天模型为例，Python 端有 ChatOpenAI、ChatTongyi 两个接入类，分别对应百炼的 OpenAI 兼容模式与 DashScope 原生模式。


### 两种接入模式

百炼同时提供两套接入协议，选择不同协议对应不同的 LangChain 接入类。

OpenAI 兼容模式：接口协议与 OpenAI 保持一致，凡是支持 OpenAI 协议的框架都能直接对接，接入成本最低。

DashScope 原生模式：使用百炼自有的 DashScope 协议，可调用百炼全部文本生成模型，包括部署后的自定义模型。

整体接入架构如下图所示：

所谓「OpenAI 兼容接口」，指供应商的 HTTP 接口协议与 OpenAI 保持一致。

只要协议兼容，任何为 OpenAI 编写的代码或工具都可以直接复用，仅需修改接口地址即可。


### 配置环境变量

所有语言与接入方式统一使用环境变量 DASHSCOPE_API_KEY 保存密钥。

Linux / macOS 在终端导出：

```text
export DASHSCOPE_API_KEY="sk-你的百炼APIKey"
```

Windows（CMD）设置方式：

```text
set DASHSCOPE_API_KEY=sk-你的百炼APIKey
```

建议把导出命令写入 shell 配置文件（如 ~/.bashrc、~/.zshrc），避免每次打开终端都重新设置。


### 通过 .env 文件配置（推荐）

更推荐的做法是把密钥写入项目根目录的 .env 文件，配合 python-dotenv 自动加载到环境变量。

密钥与代码分离，配合 .gitignore 可避免误提交，多人协作时也便于各自维护。

在项目根目录创建 .env 文件：

```text
# 文件路径：项目根目录/.env
DASHSCOPE_API_KEY=sk-你的百炼APIKey
```

比如我们测试的项目 runoob-langchain-test 下创建 .env 文件，并添加配置：

安装 python-dotenv：

```text
pip install python-dotenv
```

在 Python 代码开头加载 .env 文件：


## 实例

加载后，代码里 os.getenv("DASHSCOPE_API_KEY") 即可读到密钥，效果与手动 export 一致。

在「聊天模型」一节的示例中，已演示了这种加载方式。

.env 属于敏感文件，请加入 .gitignore（写一行 .env），防止密钥被提交到版本库。

请把示例中的密钥替换为真实 Key，切勿分享给他人。


## 两种接入方式对比

先看一张对比表，再按需选择接入方式。

两种模式使用同一个域名 dashscope.aliyuncs.com，差异在于路径：OpenAI 兼容模式路径为 /compatible-mode/v1，DashScope 原生模式的路径由 SDK 内置。


## 聊天模型（Chat Model）

聊天模型是最常用的一类模型，用于多轮对话、问答、内容生成等任务。

下面按语言介绍接入方式，示例模型统一使用 qwen-plus，可按需更换。


### Python：OpenAI 兼容方式

使用 langchain_openai 包中的 ChatOpenAI 接入类，把百炼当作一个 OpenAI 服务来调用。

先安装依赖：

```text
pip install langchain_openai
```

示例代码：


## 实例

输出结果（省略部分字段）：

```text
{
  "content": "我是通义千问，由阿里云开发的大语言模型，可以回答你的问题、协助创作、提供建议等。",
  "usage": { "prompt_tokens": 12, "completion_tokens": 28, "total_tokens": 40 }
}
```

调用成功后返回 AIMessage 对象，model_dump_json() 可将其序列化为 JSON，方便查看完整响应。


### Python：DashScope 原生方式

使用 langchain-community 包中的 ChatTongyi 接入类，走 DashScope 原生协议，支持流式输出。

ChatTongyi 来自 langchain-community 社区包，该包与 dashscope 已停止维护。

新项目建议优先使用 OpenAI 兼容方式的 ChatOpenAI 接入，仅当需要 DashScope 原生能力（如部署模型）时再考虑本方式。

先安装依赖：

```text
pip install langchain-community dashscope
```

示例代码：


## 实例

输出结果：

```text
chat resp: 你好
chat resp: ！我是通义千问，有什么可以帮您的吗？
```

流式输出让模型在生成的同时逐段返回内容，适合需要打字机效果的聊天界面。


## 文本嵌入模型（Embedding Model）

嵌入模型把文本转换成语义向量，是 RAG（检索增强生成）、语义搜索等应用的基础。


### 模型选型

百炼提供多个版本的嵌入模型，可用 MTEB、CMTEB 两个评估指标对比效果，数值越大越好。

text-embedding-v3 与 text-embedding-v4 通过 LangChain 调用时无法指定向量维度，默认输出 1024 维向量。

版本越高效果越好，优先选择 v4。


### Python 示例

百炼的嵌入接口兼容 OpenAI 接口规范，直接使用 langchain-openai 包中的 OpenAIEmbeddings 接入类，把 base_url 指向百炼的兼容端点即可。

无需安装 langchain-community 与 dashscope 这两个已停止维护的包。

先安装依赖：

```text
pip install langchain-openai
```

OpenAIEmbeddings 需要三个关键参数：model（嵌入模型名）、api_key（百炼密钥）、base_url（百炼 OpenAI 兼容端点）。

base_url 固定为 https://dashscope.aliyuncs.com/compatible-mode/v1，与聊天模型的兼容端点一致。

示例代码：


## 实例

输出结果：

```text
文本向量长度：1024
文本向量数量：5 ，文本向量长度：1024
```

embed_query 用于把用户查询向量化，embed_documents 用于把候选文档批量向量化，两者输出的向量维度一致，才能计算相似度。


## 重排序模型（Reranker Model）

重排序模型对检索结果做二次打分排序，能显著提升 RAG 应用的回答质量。


### 模型参数

百炼提供以下重排序模型，根据语种、成本与场景选择：


### Python 示例

使用 langchain-community 包中的 DashScopeRerank 接入类。

该示例使用 langchain-community 社区包中的 DashScopeRerank。

langchain-community 与 dashscope 已停止维护，新项目请关注百炼官方提供的替代接入方式。

先安装依赖：

```text
pip install langchain-community dashscope
```

示例代码：


## 实例

rerank 方法根据 query 对候选文档重新打分排序，top_n 指定返回数量，常用于 RAG 检索后的精排阶段。


## JavaScript 与 Java 接入


### JavaScript：OpenAI 兼容方式

Node.js 端使用 @langchain/openai 包的 ChatOpenAI 接入类。

先安装依赖：

```text
npm install @langchain/openai @langchain/core
```

示例代码：


## 实例

输出结果：

```text
---------------------------
J'adore la programmation.
```


### JavaScript：DashScope 原生方式

使用 @langchain/community 包中的 ChatAlibabaTongyi 接入类。

先安装依赖：

```text
npm install @langchain/community @langchain/core
```

示例代码：


## 后续章节

- 实例
- Java：OpenAI 兼容方式（LangChain4j）
- 实例
- Java：DashScope 原生方式（LangChain4j）
- 实例
- 实例
- 注意事项 / 常见问题
- Java 版本要求
- OpenAI 兼容模式只支持部分模型
- 嵌入向量默认维度
- API Key 安全
- 参考链接

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `LangChain 集成阿里百炼` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
