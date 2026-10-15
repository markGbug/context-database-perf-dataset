# LangChain：LangChain 智能客服机器人 -- RAG、订单查询、对话记忆与人工转接

- 来源：[LangChain 智能客服](https://www.runoob.com/langchain/langchain-project-customer-service.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：学习笔记
- 章节序号：0298

## 本章内容

经过前面的学习，我们已经掌握了 LangChain 的 Agent、Tools、Middleware、RAG、Checkpointer 和 Human-in-the-Loop 等功能。

但这些功能单独使用还不够。真正的 AI 应用，通常需要将它们组合起来，解决一个完整的业务问题。

本章节将构建一个 LangChain AI 智能客服机器人，实现知识库问答、订单查询、多轮对话、输入检查以及人工转接。

整个项目基于 LangChain 1.x，使用 DeepSeek 作为聊天模型、阿里百炼作为 Embedding 模型、Chroma 保存知识库、SQLite 保存对话状态。

说明：本项目使用模拟的课程、订单和人工客服数据，重点演示 LangChain 的开发流程，不会连接真实订单、会员、退款或人工客服系统。


## 一、项目功能与需求分析

我们的客服机器人需要支持以下功能：

系统的整体流程如下：

```text
用户发送消息
       ↓
    智能客服
       ↓
  Middleware 检查
       ↓
     大语言模型
       ↓
   判断任务类型
       |
       ├── 课程问题 → RAG 检索知识库
       |
       ├── 订单问题 → 订单查询工具
       |
       ├── 人工转接 → interrupt() 暂停
       |                  ↓
       |               人工处理
       |                  ↓
       |           Command(resume)
       |
       └── 普通问题 → 模型回答
       ↓
   最终回复格式化
       ↓
    Checkpointer
       ↓
     返回用户
```

这是一个典型的工具型 Agent：模型负责理解用户意图并选择工具，工具负责实际的数据查询或业务动作。


## 二、项目目录结构

我们先创建一个独立的 Python 项目。

```text
langchain-customer-service/
│
├── .env
├── .gitignore
├── check_install.py
├── customer_service_bot.py
│
├── runoob_kb/
│   └── Chroma 向量数据
│
└── customer_service.db
    SQLite 对话状态数据库
```

其中：

- .env：保存模型 API Key。
- check_install.py：检查运行环境。
- customer_service_bot.py：客服机器人主程序。
- runoob_kb/：Chroma 知识库持久化目录，运行后生成。
- customer_service.db：SQLite 检查点文件，运行后生成。

本教程将核心功能放在一个 Python 文件里，方便学习和测试。

正式项目可以进一步拆分为 Agent、Tools、Knowledge Base、Database 和 API 模块。


## 三、环境准备


### 第一步：检查 Python 版本

建议使用 Python 3.11 或更新的兼容版本。

```text
python --version
```

如果 Python 版本太旧，需要先升级，再安装 LangChain 相关依赖。


### 第二步：创建虚拟环境

```text
python -m venv venv
```

Windows 激活：

```text
venv\Scripts\activate
```

macOS / Linux 激活：

```text
source venv/bin/activate
```


### 第三步：安装依赖

执行：

```text
python -m pip install -U langchain langgraph langchain-deepseek langchain-openai langchain-chroma langchain-text-splitters langgraph-checkpoint-sqlite python-dotenv
```

主要依赖：


### 第四步：配置 API Key

在项目根目录创建 .env 文件：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
DASHSCOPE_API_KEY=your_dashscope_api_key
```

本教程默认使用：

- DeepSeek：负责用户对话和工具调用。
- 阿里百炼 text-embedding-v4：负责知识库向量化。

如果使用 OpenAI Embedding，可以参考前面的 RAG 教程替换 Embedding 初始化代码。

创建 .gitignore：

```text
.env
venv/
__pycache__/
*.pyc
customer_service.db
runoob_kb/
```

注意：API Key 和包含聊天记录的数据库文件都不应该提交到公开的 Git 仓库。


## 四、验证安装环境

创建 check_install.py，检查依赖及环境变量。


## 实例：check_install.py

运行：

```text
python check_install.py
```

如果依赖和环境变量正常，会打印当前安装版本和成功提示。

注意：此脚本只检查本地导入和环境变量是否存在，并不会实际验证 API Key 是否有效。真实接口是否可用，需要在后续请求中确认。


## 五、准备客服知识库

客服机器人的第一项能力，是根据知识库回答问题。

这里使用一组模拟数据，涉及编程课程、学习方式和客服规则。

为了避免把教学资料误当作真实商业政策，课程数量、会员价格和退款规则均不使用未经核实的数据。


### 实例：模拟知识库


## 实例

每条文档包含：

- page_content：知识正文。
- source：来源标识。
- title：文档标题。

真实项目应该从经过审核的文档、数据库或网站内容中加载知识，并保留来源 URL 和更新时间。


## 六、创建 Chroma 向量知识库

使用阿里百炼 Embedding 将知识文档转换成向量，再保存到 Chroma。

为了避免重复初始化，每个文档使用稳定的 ID。


### 实例：向量化和检索


## 实例

这里的每个模拟文档都比较短，通常只产生一个 Chunk，因此可以直接使用 source 作为演示 ID。

但实际长文档可能会拆分成多个 Chunk，这时必须为每个 Chunk 创建独立 ID，例如文档 ID 加上片段序号或内容哈希。

注意：真实项目应将知识库构建与客服问答分开运行。文档更新时还要处理旧索引，而不只是不断调用 add_documents()。


## 七、定义知识库检索工具

通过 @tool 将 Retriever 包装为 Agent 可调用的搜索工具。


### 实例：search_kb


## 实例

例如用户询问：

```text
Python 入门应该学习哪些知识？
```

Agent 可以调用：

```text
search_kb("Python 入门需要学习的知识点")
```

并根据返回资料生成回答。

需要注意，向量检索不保证返回的所有内容都正确相关。如果知识库没有答案，模型应该明确说明资料不足。


## 八、定义订单查询工具

客服系统另一个常见需求是订单查询。

例如：

```text
我的订单 ORD-DEMO-001 是什么状态？
```

但订单数据属于用户私人信息，必须处理权限问题。

不能仅凭知道订单号就允许查询订单详情。

这里通过 ToolRuntime.context 获取经过应用后端认证的用户 ID，然后检查订单归属。


### 准备模拟订单数据


## 实例

这里的数据仅用于演示，不对应真实交易。


### 实例：query_order


## 实例

注意，这里的 user_id 不是由模型生成的工具参数，而是由应用通过 Runtime Context 提供。

如果当前用户是：

```text
user_xiaoming
```

他可以查询：

```text
ORD-DEMO-001
```

但无法读取归属于 user_other 的订单。

重要：实际 Web 应用需要由后端登录系统提供可信 user_id，不能允许浏览器直接指定任意身份。


## 九、人工转接：interrupt()

当用户需要投诉、人工协助或进一步处理时，可以通过 HITL 机制暂停当前 Agent。

LangGraph 的 interrupt() 会让执行在当前节点暂停，等待外部系统提供恢复数据。

例如：

```text
用户：我要投诉，请转接人工
          ↓
Agent 调用 transfer_to_human
          ↓
       interrupt()
          ↓
      等待人工处理
          ↓
   Command(resume=...)
          ↓
      Agent 继续执行
```


## 后续章节

- 实例：人工转接工具
- 实例
- 十、Middleware：用户输入检查
- 实例：content_guard
- 实例
- 十一、Middleware：统一客服签名
- 实例：auto_signature
- 实例
- 十二、SqliteSaver：实现多轮对话记忆
- 实例：创建 Checkpointer
- 实例
- 十三、创建智能客服 Agent
- 实例：创建客服 Agent
- 实例
- 十四、完整代码：智能客服机器人
- 完整实例

## 复习重点

- 能说明 `LangChain 智能客服` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
