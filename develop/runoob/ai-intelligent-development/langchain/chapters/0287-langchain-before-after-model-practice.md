# LangChain：LangChain 中间件钩子——@before_model 与 @after_model

- 来源：[LangChain 中间件钩子](https://www.runoob.com/langchain/langchain-before-after-model.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：练习笔记
- 章节序号：0287

## 本章内容

在 LangChain Agent 中，@before_model 和 @after_model 是两个非常常用的 Middleware 钩子。

它们分别在模型调用之前和之后执行，可以用于消息预处理、上下文管理、输入检查、响应审核和流程控制。

与普通工具不同，Middleware 不需要由模型主动选择，而是由 Agent 执行框架在对应阶段运行。

本章节基于 LangChain 1.x，介绍两个钩子的工作机制、状态更新、消息裁剪、回复替换及 can_jump_to 流程控制。


## 一、before_model 与 after_model 的区别

一个典型的 Agent 执行循环如下：

```text
用户输入
    ↓
before_model
    ↓
模型调用
    ↓
after_model
    ↓
是否需要调用工具？
    ├── 是 → 执行工具 → 回到 before_model
    └── 否 → 返回最终结果
```

两者的主要区别：

如果 Agent 需要多轮工具调用，模型也可能调用多次，因此这两个钩子不一定只执行一次。


## 二、钩子的定义方式

可以通过装饰器快速创建 Middleware。

基本语法：


## 实例

随后将两个中间件传给 create_agent()：

```text
agent = create_agent(
    model="deepseek:deepseek-flash",
    tools=[],
    middleware=[pre_model, post_model]
)
```

这两个钩子接收两个重要参数：

- state：当前 Agent State，包括 messages 等字段。
- runtime：当前执行上下文，可以访问运行时 Context 等信息。

如果只是记录日志，可以返回 None，不需要修改 State。


## 三、@before_model：模型调用前处理

@before_model 在每次模型调用前运行，可以读取当前消息历史，并根据需要提交状态更新。

例如，检查消息数量：


## 实例

需要注意，消息数量并不等于对话轮数。

一次 Agent 工具调用可能增加 AIMessage 和 ToolMessage 等多条消息。


## 四、场景一：限制对话历史长度

随着对话增加，Agent State 中的消息数量可能不断增长，从而占用更多上下文 Token。

可以使用 before_model 管理历史消息，但必须理解 add_messages Reducer 的工作方式。


### 错误写法

```text
return {"messages": messages[-6:]}
```

这种写法并不能保证只保留最近六条消息。

因为 messages 使用 add_messages 合并更新。原有的其他消息不会仅仅因为没有出现在新列表中就自动删除。


### 正确方式：通过 RemoveMessage 删除消息

如果需要真正修改已保存的消息历史，可以使用 RemoveMessage。

下面先给出一个简单示例，删除早期的用户与 AI 普通文本消息。


## 实例

这段代码与原文不同，它会明确向 Reducer 提交删除指令。

但为了避免误删工具消息，示例主动跳过包含 Tool Calling 的对话历史。

注意：正式项目不能简单按消息条数随意删除，尤其不能让 AIMessage 中的工具调用与对应 ToolMessage 脱离。


### 推荐方案：使用 SummarizationMiddleware

对于长对话，更推荐使用 LangChain 内置的 SummarizationMiddleware，在上下文达到阈值时生成摘要，而不是盲目保留最后几条消息。

如果需要直接清理旧的工具输出，也可以考虑 ContextEditingMiddleware。

因此，建议：


## 五、场景二：输入内容检查

可以通过 before_model 在模型调用前检查用户输入，并在满足规则时提前结束 Agent。

例如，对于某些演示专用关键词，直接返回提示，不调用模型。

需要注意，不建议直接将"密码""身份证"等词作为全部禁止关键词，因为用户可能只是正常询问密码安全、身份认证等技术知识。


### 实例：演示关键词拦截


## 实例

输出：

```text
该请求已被演示规则拦截。
```

这里有两个关键点：

- 通过 can_jump_to=["end"] 声明允许跳转到结束流程。
- 通过 AIMessage 添加助手回复，而不是错误地用 HumanMessage 返回提示。

注意：这个示例只是演示输入拦截，不能当作完整的敏感信息识别或安全防护系统。

如果需要保护用户个人信息，应使用更可靠的规则、数据检测机制以及服务端权限控制。


## 六、@after_model：模型响应后处理

@after_model 会在模型返回响应后执行，适合对输出内容进行检查或记录。

它既可能在最终回复后运行，也可能在模型请求工具调用后运行。

因此，处理最终文本之前，应先检查模型是否产生了 tool_calls。


### 实例：检查模型是否请求工具


## 实例

如果模型请求工具，Agent 随后可能继续执行工具节点。

如果模型没有产生工具调用，并且不存在其他流程控制，通常会结束当前循环。


## 七、场景三：审核并替换模型回复

对于某些应用，需要在模型返回回复后检查内容。

例如，某个系统禁止向用户展示约定的内部测试标记。

这里使用 INTERNAL_DEMO_ONLY 作为教学用拦截字符串。


### 为什么不能直接新增 AIMessage？

原文使用下面的方式：

```text
return {
    "messages": [AIMessage(content="替换后的回复")]
}
```

这并不能保证覆盖旧回复，因为新 AIMessage 通常具有不同的消息 ID。

如果要替换已经存在的消息，应使用相同的消息 ID，让 add_messages Reducer 执行替换。


### 正确实例：保留原消息 ID


## 实例

这里的关键代码是：

```text
id=last.id
```

由于新旧消息使用相同的 ID，Reducer 可以替换已有的模型回复，而不是在消息历史中额外追加一条回答。

注意：如果已经将未经审核的消息片段通过 Streaming 发送给前端，那么 after_model 的替换无法撤回已经传输的内容。

对于需要严格审核后才能展示的内容，应先缓冲响应并完成审核，再发送给用户，或采用其他可靠的输出防护机制。


## 八、场景四：为最终回答添加提示信息

如果需要自动在模型最终回答后添加说明，也可以通过 after_model 更新最后一条消息。

例如，为 AI 生成内容添加固定的说明。


### 实例：追加内容声明


## 实例

如果模型返回：

```text
Python 是一门适合初学者的编程语言。
```

更新后的消息内容为：

```text
Python 是一门适合初学者的编程语言。

---
以上内容由 AI 生成，仅供参考。
```

这里再次使用 id=last.id 替换原有回复。

同时还检查了声明是否已经存在，避免重复追加。

注意：这里为了便于教学，构造了新的 AIMessage。生产环境如果需要保留原消息的响应元数据、使用量信息等，可以优先考虑复制原消息并只更新必要字段。


## 九、can_jump_to：控制 Agent 执行流程

can_jump_to 用于声明钩子允许将 Agent 路由到哪些目标。

可选目标包括：

例如：

```text
@before_model(can_jump_to=["end"])
def check_exit(state, runtime):
    ...
```

只有明确设计了路由目标，才应该返回对应的 jump_to 值。


## 后续章节

- 实例：用户输入再见时提前结束
- 实例
- 十、完整实例：输入检查与回复处理
- 完整实例
- 可能的运行结果
- 十一、before_model 与 wrap_model_call 的区别
- 十二、常见问题
- 1、before_model 每轮都会执行吗？
- 2、after_model 能拦截工具调用吗？
- 3、为什么返回最近六条消息没有删除旧消息？
- 4、为什么 after_model 返回 AIMessage 后出现两条 AI 回复？
- 5、为什么内容过滤使用 AIMessage？
- 6、can_jump_to=["tools"] 能直接执行任意工具吗？
- 7、可以同时注册多个 before_model 吗？
- 8、after_model 适合做完整的内容安全审核吗？
- 9、怎样在中间件中发送自定义进度？

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `LangChain 中间件钩子` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
