# LangChain：LangChain 跨会话存储——Store

- 来源：[LangChain 跨会话存储](https://www.runoob.com/langchain/langchain-store.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：学习笔记
- 章节序号：0292

## 本章内容

上一章节我们介绍了 Checkpointer，它可以保存 Agent 的对话历史，让同一个线程具备多轮记忆能力。

但如果用户开启新的对话，使用了不同的 thread_id，之前的聊天记录通常不会自动出现在新会话中。

如果希望 Agent 在不同会话之间共享用户偏好、学习进度或长期信息，就可以使用 Store（长期存储）。

LangChain 1.x 基于 LangGraph Store 提供跨会话的数据存储能力，支持按命名空间管理数据，并通过 ToolRuntime 在工具中读写。

本章节介绍 Store 的基本操作、在 Agent 中使用 Store、跨会话记忆、与 Checkpointer 配合、PostgreSQL 持久化以及数据安全。


## 一、Checkpointer 与 Store 的区别

两者都能保存数据，但负责的内容不同。

可以这样理解：

```text
Checkpointer
    ├── 对话 A 的消息历史
    ├── 对话 B 的消息历史
    └── 当前 Agent 执行状态

Store
    ├── 用户学习偏好
    ├── 已完成的课程
    └── 长期学习目标
```

同一个用户即使开启不同对话，也可以通过 Store 读取自己的长期信息。

注意：Store 并不会自动从聊天中提取用户偏好。需要程序或 Agent 工具明确执行保存和读取操作。


## 二、Store 的数据组织结构

Store 采用 namespace + key + value 的方式组织数据。

可以将它理解为：

```text
namespace：数据所属的命名空间
key：命名空间中的唯一键
value：需要保存的 JSON 数据
```

例如：

```text
namespace = ("users", "user_001")
key = "preferences"

value = {
    "language": "zh-CN",
    "theme": "dark"
}
```

其中，namespace 是字符串元组，可以用于区分用户、项目或业务模块。


### 推荐的命名空间设计

建议将数据按访问范围划分：公共数据使用公共命名空间，用户私人数据使用包含可信用户 ID 的命名空间。


## 三、InMemoryStore 基本操作

InMemoryStore 是最简单的 Store 实现，数据保存在当前 Python 进程内存中。

主要提供四种常见操作：


### 实例：读写用户偏好和学习进度


## 实例

运行结果：

```text
用户偏好： {'theme': 'dark', 'language': 'zh-CN', 'level': '入门'}
学习进度： {'completed_courses': ['HTML 基础', 'Python 基础'], 'total_hours': 35}
preferences {'theme': 'dark', 'language': 'zh-CN', 'level': '入门'}
progress {'completed_courses': ['HTML 基础', 'Python 基础'], 'total_hours': 35}
删除后： None
```

需要注意：

- get() 返回 Store Item，实际数据在 item.value 中。
- 如果没有找到对应数据，通常返回 None。
- put() 使用相同 namespace 和 key 时，会更新对应数据。
- delete() 删除的是指定数据项，不代表删除整个用户的其他数据。

注意：InMemoryStore 只适合开发和测试。程序退出后数据会丢失，不应该直接作为长期生产存储。


## 四、理解 Store Item

通过 store.get() 读取数据时，返回的不是简单字典，而是包含数据及元信息的 Item。


### 实例


## 实例

这些属性可以帮助开发者了解数据的内容和保存时间。

但需要注意，更新时间不等于数据一定是最新的业务信息。

例如，Store 中保存的课程目录可能已经过时，需要由业务程序定期同步。


## 五、在 Agent 中访问 Store

创建 Agent 时，通过 store 参数传入 Store 实例：

```text
agent = create_agent(
    model="deepseek:deepseek-flash",
    tools=[...],
    store=store
)
```

LangChain 1.x 推荐使用 ToolRuntime 在工具中访问 Store。

在工具函数中增加：

```text
runtime: ToolRuntime
```

然后通过：

```text
runtime.store
```

读取或写入数据。

与旧版注入写法相比，这种方式更简洁，也可以统一访问 State、Context 和工具调用 ID。


### 实例：课程查询工具


## 实例

如果模型调用工具，可能回答：

```text
Python3 基础教程是一门免费的入门课程。
```

这里的课程资料来自 InMemoryStore，不会连接菜鸟教程网站的真实课程数据库。

注意：模型不一定主动调用工具。如果某项查询必须执行，应该由应用程序或确定性工作流负责。


## 六、ToolRuntime：读取运行时信息

ToolRuntime 是 LangChain 1.x 中工具获取运行时信息的主要方式。

工具参数中的 runtime 由 LangChain 自动注入，不会作为普通工具参数发送给大语言模型。

例如：

```text
@tool
def my_tool(keyword: str, runtime: ToolRuntime) -> str:
    ...
```

模型只需要生成 keyword 参数。

注意：只有创建 Agent 时传入了 Store，才能保证 runtime.store 可用于相应的存储操作。


## 七、根据可信用户 ID 读取个人数据

如果 Store 中保存的是用户私人信息，不应该让模型自己提供任意 user_id 查询。

例如，下面这种工具设计存在越权风险：

```text
@tool
def get_user_info(user_id: str):
    ...
```

因为模型可能生成其他用户的 ID。

更合理的方式是通过 context_schema 接收应用后端已经认证的用户信息。


### 实例：读取当前用户学习偏好


## 实例

如果工具正确执行，Agent 可以获取当前用户的偏好：

```text
学习语言：Python
学习级别：入门
回答语言：中文
```

这里没有将 user_id 暴露为模型可填写的工具参数，而是从 Runtime Context 获取。

重要：Context 中的 user_id 应由可信后端认证后注入。不能直接把用户浏览器提交的任意 user_id 当作已认证身份。


## 八、通过工具保存用户长期记忆

除了读取 Store，工具也可以写入 Store。

例如，用户告诉学习助手：

```text
以后给我讲 Python 时，尽量使用简单的例子。
```

Agent 可以调用工具，保存这一偏好。


### 实例：保存学习偏好


## 实例

这里先读取原有的 preferences，再更新学习风格，避免直接覆盖之前保存的语言和学习等级等字段。

存储后的数据可能为：

```text
{
    "language": "zh-CN",
    "level": "入门",
    "favorite": "Python",
    "learning_style": "尽量使用简单的例子"
}
```

如果使用 InMemoryStore，数据只会在进程内保留。

注意：长期偏好应尽量由用户明确提出或经过确认，避免把模型的推测当作用户真实偏好保存。


## 九、完整实例：跨两个会话共享学习偏好

这是 Store 最重要的应用场景。

下面将 Checkpointer 与 Store 一起使用。

两个会话使用不同的 thread_id，但使用同一个 user_id。

这样可以实现：

- 不同会话拥有独立的聊天记录。
- 不同会话共享同一个用户的长期学习偏好。
- 学习偏好通过 Store 保存，不需要从之前的聊天历史中重新提取。

文件名：store_memory_demo.py

安装依赖：

```text
pip install -U langchain langgraph langchain-deepseek python-dotenv
```

配置 .env：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
```


## 完整实例

如果模型正确调用保存和读取工具，可能得到：

```text
会话 A：学习偏好已经保存。

会话 B：你希望学习 Python 时，多使用简单的代码示例。
```

两个 thread_id 不同：

```text
chat-a
chat-b
```

但两个会话使用相同的：

```text
user_id = "student-001"
```

因此，虽然聊天历史不同，但工具可以通过相同的 namespace 访问长期偏好。

可以理解为：

```text
用户 student-001
        |
        +---- 会话 chat-a ---- Checkpointer
        |
        +---- 会话 chat-b ---- Checkpointer
        |
        +---- 学习偏好 ----- Store
```

注意：这个示例的工具调用由模型决定。生产环境如果必须保证某项偏好被保存，应由应用程序显式执行保存操作，并检查结果。


## 十、让 Agent 自动读取长期偏好

前面的例子需要模型主动调用工具才能读取学习偏好。

但有时希望用户每次提问时，Agent 都能自动加载已保存的偏好。

可以使用 @dynamic_prompt，在模型请求前读取 Store，然后动态生成 System Prompt。


### 实例：将偏好注入系统提示词


## 实例

创建 Agent 时加入：

```text
agent = create_agent(
    model="deepseek:deepseek-flash",
    tools=[],
    store=store,
    context_schema=UserContext,
    middleware=[personalized_prompt]
)
```

这样即使用户没有主动询问偏好，Agent 也可以在每次模型调用前读取已保存的数据。

注意：Store 中的文本应被视为数据，而不是具有最高优先级的系统指令。不能让未经验证的存储内容覆盖权限控制或其他关键应用规则。


## 后续章节

- 十一、search()：搜索 Store 中的数据
- 实例：搜索用户记忆
- 实例
- 十二、Store 的语义搜索
- 十三、PostgresStore：持久化长期记忆
- 完整实例：PostgreSQL 存储
- 实例
- 十四、在 Agent 中使用 PostgresStore
- 实例
- 十五、异步 Store
- 实例：异步 PostgreSQL Store
- 实例
- 十六、Store 与普通数据库有什么区别？
- 十七、生产环境注意事项
- 1、不要信任模型生成的用户 ID
- 2、命名空间不等于权限控制

## 复习重点

- 能说明 `LangChain 跨会话存储` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
