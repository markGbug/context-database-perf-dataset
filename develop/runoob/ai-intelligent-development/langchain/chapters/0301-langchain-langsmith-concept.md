# LangChain：LangChain LangSmith——可观测性与调试

- 来源：[LangChain LangSmith](https://www.runoob.com/langchain/langchain-langsmith.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：概念卡
- 章节序号：0301

## 本章内容

前面的教程中，我们已经使用 LangChain 构建了 RAG Agent、智能客服机器人和多工具个人助手。

但随着 Agent 变得复杂，一个新的问题也出现了：当 AI 回答错误、工具调用失败或响应速度变慢时，我们应该如何定位问题？

例如，一个 RAG Agent 没有正确回答用户的问题，可能是因为模型没有调用检索工具、检索结果不相关，或者模型没有正确理解资料。

仅仅查看最终回答，通常无法快速判断问题发生在哪一步。

这时就可以使用 LangSmith。

LangSmith 是 LangChain 提供的 AI 应用可观测性、调试和评估平台，能够追踪 Agent 的模型调用、工具执行、输入输出、耗时以及部分 Token 使用情况。

本章节基于 LangChain 1.x，介绍 LangSmith 的基本使用、自动追踪、自定义 Trace、项目管理、性能分析、追踪采样和数据隐私。


## 一、什么是 LangSmith？

LangSmith 可以帮助开发者了解 AI 应用的实际运行情况。

例如，用户询问：

```text
帮我查一下 Python 入门课程。
```

Agent 可能经历以下过程：

```text
用户问题
    ↓
Agent 开始执行
    ↓
调用 DeepSeek 模型
    ↓
模型选择 search_course 工具
    ↓
执行 search_course("Python")
    ↓
工具返回课程资料
    ↓
再次调用 DeepSeek
    ↓
生成最终回答
    ↓
Agent 执行完成
```

如果没有追踪工具，开发者通常只能依靠 print() 和程序日志查看部分过程。

启用 LangSmith 后，可以在控制台中查看这些操作的调用关系、执行时间以及可记录的输入输出。


### LangSmith 的主要功能

注意：LangSmith 展示的是应用能够记录的执行轨迹，并不意味着能够读取模型未公开的内部推理过程。


## 二、几个重要概念

在使用 LangSmith 之前，需要了解几个基本术语。

例如，一个智能客服的 Trace 可能包含多个子 Run：

```text
Trace：客服问题处理
    |
    ├── Run：Agent
    |
    ├── Run：ChatDeepSeek
    |
    ├── Run：search_knowledge
    |
    └── Run：ChatDeepSeek
```

通过这个执行结构，可以看到每一步花费了多少时间，以及问题可能发生在哪里。


## 三、注册 LangSmith

首先访问 LangSmith 官方网站：

https://smith.langchain.com/

登录后，在 Workspace 的相关设置中创建或获取 API Key。

API Key 用于让本地 Python 程序把追踪数据发送到对应的 LangSmith 工作空间。

注意：LangSmith API Key 与 DeepSeek API Key 是两套独立的凭据，不能互相替代。


## 四、安装依赖

如果已经安装了 LangChain，可以额外安装 LangSmith SDK：

```text
pip install -U langsmith
```

为了运行本文的完整 Agent 示例，建议安装：

```text
pip install -U langchain langchain-deepseek langsmith python-dotenv
```

其中：

LangChain 本身具有 LangSmith 追踪集成。对于一般的 Agent 自动追踪，设置好环境变量后通常不需要再为每一个工具手动编写追踪代码。


## 五、配置 LangSmith 环境变量

在项目目录中创建 .env 文件：


## 实例：.env

主要环境变量：

其中 LANGSMITH_ENDPOINT 通常可以省略，使用默认的服务地址。

如果账号所在区域不是默认的美国区域，需要按 LangSmith 官方文档配置相应的区域 Endpoint。

当 API Key 与多个 Workspace 关联，或者使用需要明确指定 Workspace 的凭据时，应配置 LANGSMITH_WORKSPACE_ID。

版本说明：旧教程可能使用 LANGCHAIN_TRACING_V2、LANGCHAIN_API_KEY 和 LANGCHAIN_PROJECT。在新项目中，建议统一使用 LANGSMITH 前缀，避免混淆。


## 六、自动追踪 Agent

LangSmith 最方便的地方是自动追踪。

配置环境变量后，正常创建并调用 LangChain Agent，模型和工具等支持追踪的组件通常会自动记录执行信息。

下面创建一个简单的课程查询 Agent。


### 完整实例：自动追踪


## 实例

运行：

```text
python trace_agent.py
```

如果配置正确，LangSmith 会接收这次 Agent 执行的追踪数据。

在控制台中打开：

```text
runoob-agent-demo
```

就可以查看相关执行记录。

实际 Trace 是否出现，取决于 API Key、工作空间配置、网络连接以及追踪数据是否成功上传。


## 七、查看 Agent 的执行轨迹

在 LangSmith 中选择对应 Project，然后打开某条 Trace。

你通常可以看到以下信息：


### 1、执行时间线

例如：

```text
Agent
  ├── ChatDeepSeek
  │     └── 请求 search_course
  ├── search_course
  │     └── 返回模拟课程
  └── ChatDeepSeek
        └── 生成最终回答
```

这样可以判断模型实际调用了哪些工具，而不是仅依靠最终回答推测。


### 2、输入和输出

可以检查模型收到的消息、工具参数以及模型返回的内容。

例如：

```text
Tool：search_course

Input：
{"keyword": "Python"}

Output：
"Python 入门、Python 函数、Python 面向对象"
```

如果工具参数不正确，就可以进一步检查模型的工具选择逻辑与 Prompt。


### 3、执行耗时

可以分析耗时主要发生在：

- 模型生成。
- 工具执行。
- 外部 API 请求。
- 检索或其他应用处理步骤。

例如一个 Agent 总共耗时 8 秒，其中 6 秒来自模型请求，就应优先检查模型调用，而不是盲目优化 Python 字符串处理。


### 4、错误信息

如果某个被追踪步骤抛出异常，LangSmith 可以记录相应的错误信息。

错误细节的完整程度取决于 SDK、异常处理以及实际运行环境。


## 八、Token 使用量与费用分析

LangSmith 可以展示可获取的模型 Token 用量和费用信息，帮助开发者分析 Agent 的调用成本。

例如一次 Agent 请求可能包含：

以上数字仅用于演示，不代表真实模型消耗。

需要注意，Token 用量与成本不是同一个概念。

即使模型接口提供了准确的 Token 数量，如果 LangSmith 尚未识别该模型的价格，也不一定能够正确计算费用。

建议：正式成本统计应以模型服务商的实际计费记录为准，并结合 LangSmith 分析每次请求的成本结构。


## 九、查看实际工具调用次数

除了使用 LangSmith 界面，还可以在代码中检查 Agent 是否真正调用了工具。


### 实例：打印工具调用记录


## 实例

这适合本地调试。

LangSmith 则可以进一步将每次模型和工具调用以可视化方式关联起来，方便查看完整执行流程。


## 十、使用 @traceable 手动追踪函数

除了自动追踪 LangChain Agent，还可以通过 LangSmith 的 @traceable 装饰器，为普通 Python 函数创建独立的追踪记录。

例如，我们希望追踪：

```text
用户问题预处理
        ↓
    调用 Agent
        ↓
    格式化最终结果
```

可以将整个业务函数标记为一个 Trace 节点。


### 实例：追踪业务函数


## 实例

如果追踪成功，LangSmith 中可以看到：

```text
process_user_query
    |
    └── Agent
         |
         ├── ChatDeepSeek
         ├── search_course
         └── ChatDeepSeek
```

@traceable 很适合追踪自己编写的业务函数，例如输入清理、权限检查、RAG 查询和结果转换。

注意：追踪普通 Python 函数时，只有被显式追踪的函数及其支持上下文传播的子调用，才会形成相应的可观测执行结构。并不是任意第三方代码都会自动变成独立 Trace 节点。


## 十一、给追踪添加 Tags 和 Metadata

实际项目中，你可能需要区分不同环境、模型版本和业务场景。

例如：

```text
开发环境：development
生产环境：production

业务类型：course-search
模型：deepseek-chat
版本：v1.0
```

可以在调用 Agent 时使用 config 添加 Tags 和 Metadata。


### 实例


## 后续章节

- 实例
- 十二、为不同环境设置 Project
- 实例：tracing_context
- 实例
- 十三、如何关闭 LangSmith 追踪？
- 实例
- 十四、生产环境设置采样率
- 实例：采样配置
- 十五、保护用户隐私与敏感数据
- 隐藏输入和输出
- 生产安全建议
- 十六、LangSmith 与普通日志有什么区别？
- 十七、使用 LangSmith 评估 Agent
- 十八、如何分析一个 RAG Agent 的问题？
- 十九、常见问题
- 1、LangSmith 必须与 LangChain 一起使用吗？

## 记忆卡片

- 一句话定义：`LangChain LangSmith` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
