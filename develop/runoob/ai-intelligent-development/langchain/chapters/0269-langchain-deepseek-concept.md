# LangChain：LangChain 集成 DeepSeek

- 来源：[LangChain DeepSeek](https://www.runoob.com/langchain/langchain-deepseek.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：概念卡
- 章节序号：0269

## 本章内容

本章节介绍如何在 LangChain 中集成和使用 DeepSeek 聊天模型。

通过 langchain-deepseek 扩展包，开发者可以快速接入 DeepSeek 提供的大语言模型服务。

DeepSeek 模型既支持官方托管 API，也支持通过 Ollama、Fireworks、Together 等平台进行本地或第三方推理部署。

除了官方API接口外，我们也可以通过Coding Plan/Token Plan套餐直接接入DeepSeek、Kimi、GLM、Doubao、MiniMax等主流大模型，无需单独购买各家API。


### DeepSeek 介绍

DeepSeek 是一个开源大语言模型系列，支持聊天、推理、代码生成等能力。

在 LangChain 中，DeepSeek 主要通过 ChatDeepSeek 类进行调用。

集成信息：

模型能力支持：

DeepSeek API 使用与 OpenAI/Anthropic 兼容的 API 格式，通过修改配置，您可以使用 OpenAI/Anthropic SDK 来访问 DeepSeek API，或使用与 OpenAI/Anthropic API 兼容的软件。


## 安装 langchain-deepseek

在开始使用前，需要先安装 DeepSeek 的 LangChain 集成包：

```text
pip install -qU langchain-deepseek
```


## 配置 DeepSeek API Key

你需要先注册 DeepSeek 账号，并创建 API Key，如果还没有需要先去 https://platform.deepseek.com/api_keys 创建一个 API key。

通常推荐使用 python-dotenv 来读取当前目录中的 .env 配置文件。

```text
pip install python-dotenv
```

在当前项目目录创建 .env 文件：


## .env 文件配置：

Python 读取 .env 文件：


## 完整实例

指定 .env 文件路径: 如果 .env 文件不在当前目录，可以手动指定路径：


## 实例


### 配置 LangSmith（可选）

如果需要开启 LangChain 调用链追踪与调试功能， 可以配置 LangSmith API Key：


## 实例


### 创建 ChatDeepSeek 模型

安装完成后，可以通过 ChatDeepSeek 初始化模型：


## 实例

参数说明:

也可以使用 init_chat_model() 函数来调用：


## 实例


## 调用 DeepSeek 模型

下面示例演示如何向 DeepSeek 模型发送聊天消息：

注意我这里测试，把 API Key 写在了测试文件中：

```text
llm = ChatDeepSeek(
    api_key="sk-xxx",  # 设置你的 DeepSeek API Key
    model="deepseek-v4-flash"
)
```

实际的生产环境请设置在 .env 文件中。


## 实例

以上代码将英文翻译成中文，运行后，模型会返回翻译后的结果：

```text
我喜欢编程。
```

支持的 DeepSeek 模型:


## LangChain + DeepSeek 完整测试实例

下面演示一个完整可运行的 LangChain + DeepSeek 示例。


### 创建测试文件

创建 test.py 文件：


## 完整实例

在终端执行：

```text
python test.py
```

输出如下：

代码说明：


### 使用 deepseek-v4-pro 推理模型

LangChain 支持 DeepSeek 流式输出，需要使用 deepseek-v4-pro 推理模型：


## 实例


### 使用 PromptTemplate

结合 PromptTemplate 动态生成 Prompt：


## 实例


### 常见错误


### 推荐项目结构


## 项目结构


### requirements.txt 示例


## 后续章节

- 实例
- 参考文档

## 记忆卡片

- 一句话定义：`LangChain DeepSeek` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
