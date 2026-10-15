# LangChain：LangChain 中间件钩子——@before_agent 与 @after_agent

- 来源：[LangChain @before_agent](https://www.runoob.com/langchain/langchain-before-after-agent.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：学习笔记
- 章节序号：0290

## 本章内容

在 LangChain Agent 中，@before_agent 和 @after_agent 是两个 Agent 级别的 Middleware 钩子。

它们分别在 Agent 主执行流程开始前和正常完成后运行，适合处理输入预处理、状态初始化、访问检查、结果格式化以及执行统计等任务。

与每次模型调用前后执行的 @before_model 和 @after_model 不同，这两个钩子作用于整个 Agent 的生命周期。

本章节基于 LangChain 1.x，介绍两个钩子的基本用法、状态更新、执行控制以及实际应用。


## 一、before_agent 与 after_agent 的区别

一个简单 Agent 的执行流程可以理解为：

```text
用户输入
    ↓
before_agent
    ↓
before_model
    ↓
模型调用
    ↓
after_model
    ↓
是否调用工具？
    ├── 是 → 执行工具 → 再次调用模型
    └── 否 → 继续
    ↓
after_agent
    ↓
返回最终结果
```

其中，before_agent 和 after_agent 主要控制 Agent 整体执行的开始与结束阶段。

注意：如果 Agent 在执行期间发生异常、中断或者通过 Checkpointer 恢复，实际钩子执行情况可能与正常完整调用不同。


## 二、两个钩子的基本语法

可以通过装饰器快速定义 Agent 生命周期钩子。


## 实例

使用时加入 middleware：

```text
agent = create_agent(
    model="deepseek:deepseek-flash",
    tools=[],
    middleware=[start_hook, finish_hook]
)
```

两个钩子接收的主要参数：

- state：当前 Agent State，可以读取消息历史和自定义状态。
- runtime：当前运行环境，可以读取应用传入的 Context 等信息。

如果不需要修改状态，可以返回 None，或者不显式返回。


## 三、@before_agent：输入预处理

@before_agent 可以在 Agent 执行前规范化用户输入。

例如，移除问题前后的多余空格，将全角空格转换为普通空格。

需要注意，AgentState 中的 messages 使用 add_messages Reducer，不能直接返回一条全新的消息就认为原来的消息已经被替换。

正确方法是复用原消息 ID。


### 实例：规范化用户消息


## 实例

在这个示例中，原始用户输入为：

```text
　 Python 是什么？
```

经过预处理后，消息内容变成：

```text
Python 是什么？
```

模型收到的就是规范化后的问题。

关键点：HumanMessage(id=last.id, ...) 保留了原消息 ID，因此 add_messages 可以替换对应的消息，而不是追加重复的用户消息。

这个示例只处理纯文本，不直接修改图片、音频等多模态内容。


## 四、@before_agent：初始化自定义状态

对于需要维护业务状态的 Agent，可以在 before_agent 中初始化缺失字段。

例如，学习助手需要保存当前学习等级和学习目标。


### 实例：初始化学习状态


## 实例

假设输入状态只有：

```text
{
    "messages": [...]
}
```

中间件可以添加：

```text
{
    "user_level": "入门",
    "current_goal": "学习 Python"
}
```

这里使用自定义 LearningState 声明扩展字段。

注意：自定义字段不在 AgentState 默认结构中，需要通过 state_schema 等受支持的方式声明。

如果用户已经提供了相关字段，示例不会覆盖原来的值。


## 五、@before_agent：访问控制

在某些应用中，Agent 执行前需要检查用户是否可以使用特定功能。

例如，普通访客可以查询课程，但不能调用管理功能。

可以利用 before_agent 在流程开始时进行初步检查。

不过，真正的用户身份和权限必须由可信后端确认，不能依赖模型自行判断，也不能只靠用户消息中的关键词。


### 实例：根据运行时角色拦截请求

这里使用 Context 模拟后端已经确认的角色。


## 实例

输出：

```text
当前账户没有管理功能权限。
```

这里的 /admin 只是演示用的命令前缀，不是完整的安全控制。

重要：真实管理工具仍然必须在工具执行层或后端 API 中进行权限校验。

即使 before_agent 拦截了部分请求，也不能据此认为用户无法通过其他提示词触发受限工具。

对于严格的访问控制，更可靠的设计是：

- 先由应用后端完成用户认证。
- 将可信权限信息传给 Agent Runtime。
- 根据权限限制可用工具。
- 在每个有副作用的工具中再次检查权限。


## 六、can_jump_to：提前结束 Agent

before_agent 可以配置 can_jump_to，声明允许的流程跳转目标。

例如：

```text
@before_agent(can_jump_to=["end"])
def check_request(state, runtime):
    ...
```

如果输入不满足业务规则，可以返回：

```text
{
    "jump_to": "end",
    "messages": [AIMessage(content="请求不符合要求。")]
}
```

这样可以在不正常调用模型的情况下提前结束当前执行流程。

支持的跳转目标包括：

通常情况下，before_agent 最常见的跳转场景是 "end"。

注意：不应该认为设置 jump_to="tools" 就可以直接执行任意工具。工具节点仍然需要合法的工具调用上下文。


## 七、@after_agent：执行完成后统计

@after_agent 在 Agent 正常完成执行时运行，可以对消息历史进行统计。

例如：

- 消息总数。
- 用户消息数量。
- 工具调用请求数量。
- 工具结果消息数量。

需要注意，消息数量不等于模型 API 调用次数。


### 实例：统计执行结果


## 实例

如果 Agent 进行了一次工具调用，可能得到：

```text
消息总数： 4
用户消息： 1
工具请求： 1
工具结果： 1
```

实际数据取决于 Agent 的执行路径。

如果 Agent 使用 Checkpointer 保存多轮历史，这里统计的可能是当前 State 中的累计消息，而不是仅本次新增的消息。

如果需要精确统计单次运行的模型 API 调用次数，建议使用专门的 Middleware 计数器或模型调用追踪数据。


## 八、通过自定义状态保存统计结果

除了直接打印日志，还可以把统计结果写入 Agent State。

这样调用方就可以从最终结果中读取统计信息。


### 实例：返回自定义统计字段


## 实例

Agent 正常执行完成后，可以读取：

```text
result["message_count"]
result["tool_result_count"]
```

这种方式适合将统计数据返回应用程序。

但应注意，它们是当前消息状态的统计值，不一定等于本次调用的独立计数。


## 九、@after_agent：格式化最终输出

除了记录统计数据，还可以通过 after_agent 统一调整最终回答。

例如，自动追加 AI 内容声明。

但是，原文中通过新增 AIMessage 的方式可能导致重复回答。

因为 messages 使用 add_messages Reducer，要替换已有消息，应保留原来的消息 ID。


### 实例：为最终回复添加页脚


## 实例

如果模型原始回答为：

```text
Python 语法简洁，适合初学者学习。
```

最终返回的内容会变成：

```text
Python 语法简洁，适合初学者学习。

---
由菜鸟教程 RUNOOB AI 助手提供，内容仅供参考。
```

这里使用 model_copy(update=...) 保留了原始 AIMessage 的 ID 和其他消息字段，并只更新内容。

因此，add_messages 会替换对应的旧回复，而不是追加一条全新的回复。

注意：如果使用 Streaming 实时推送模型文本，那么已发送到浏览器的文本不会因为 after_agent 修改了最终 State 而自动更新。

如果需要显示格式化后的最终内容，可以在执行结束后发送最终结果事件，或者在前端单独渲染固定页脚。


## 十、after_agent 与自定义流式事件

如果希望将统计信息实时推送给前端，可以在支持的运行时上下文中发送 Custom Streaming 事件。

需要通过 stream_mode="custom" 接收，并根据 LangGraph 版本使用相应的事件结构。


### 实例：发送完成统计事件


## 后续章节

- 实例
- 十一、完整实例：四个钩子协作
- 完整实例
- 可能的运行结果
- 十二、before_agent 与 before_model 如何选择？
- 十三、after_agent 与 after_model 如何选择？
- 十四、六个 Middleware 钩子速查表
- 十五、生产环境注意事项
- 1、不要只在 before_agent 中检查工具权限
- 2、不要重复初始化已有状态
- 3、不要将 after_agent 当作异常清理钩子
- 4、不要将消息数量当作 API 调用次数
- 5、避免在日志中泄露敏感信息
- 6、注意流式输出与最终状态的区别
- 十六、常见问题
- 1、before_agent 和 after_agent 一定各执行一次吗？

## 复习重点

- 能说明 `LangChain @before_agent` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
