# LangChain：LangChain 中间件（Middleware）

- 来源：[LangChain 中间件](https://www.runoob.com/langchain/langchain-middleware-concepts.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：练习笔记
- 章节序号：0286

## 本章内容

LangChain Middleware（中间件）是扩展 Agent 行为的重要机制。

通过 Middleware，开发者可以在模型调用、工具执行和 Agent 生命周期的特定阶段插入自定义逻辑，实现日志记录、重试、模型降级、内容检查、动态提示词和执行限制等功能。

这些逻辑可以与 Agent 的业务工具分离，不需要每次都修改 Agent 的核心执行代码。

本章节基于 LangChain 1.x，介绍 Middleware 的六个核心钩子、装饰器与类继承两种定义方式、执行顺序、状态更新和常用内置中间件。


## 一、什么是 Middleware？

Middleware 可以理解为 Agent 执行流程中的拦截器或钩子（Hook）。

一个普通 Agent 通常按照以下流程运行：

```text
用户输入
   ↓
调用模型
   ↓
模型判断是否调用工具
   ↓
执行工具
   ↓
将工具结果返回模型
   ↓
生成最终回答
```

Middleware 可以在这些环节前后运行额外逻辑。

例如：

```text
用户输入
   ↓
[before_agent] 初始化和请求检查
   ↓
[before_model] 模型调用前检查
   ↓
[wrap_model_call] 模型请求拦截、重试
   ↓
       Model
   ↓
[after_model] 模型响应检查
   ↓
[wrap_tool_call] 工具执行拦截
   ↓
       Tools
   ↓
重新调用模型（按需循环）
   ↓
[after_agent] 执行结束处理
   ↓
返回结果
```

需要注意，以上只是简化流程。实际执行顺序还受到多个 Middleware 的组合方式、模型工具调用、中断和其他执行控制机制影响。


## 二、Middleware 的六个核心钩子

LangChain Middleware 提供六个主要钩子，分为 Node-style 和 Wrap-style 两类。


### Node-style Hooks

节点钩子在指定执行阶段运行，适合日志记录、状态更新和流程检查。

包含：

```text
before_agent
before_model
after_model
after_agent
```

通常可以返回：

- None：不修改状态。
- dict：更新 Agent State。
- Command：在支持的执行场景中进行状态或流程控制。


### Wrap-style Hooks

包装钩子负责拦截模型或工具调用。

包含：

```text
wrap_model_call
wrap_tool_call
```

这类钩子会收到一个 handler，由它执行被包装的操作。

开发者可以选择调用 handler 一次、多次，或者在合适的条件下不调用 handler。

注意：Wrap-style Hook 的返回值必须符合相应协议，不能将普通状态字典直接当作模型或工具调用的返回值。


## 三、两种 Middleware 定义方式

LangChain 支持使用装饰器或者继承 AgentMiddleware 类创建中间件。


### 方式一：装饰器

适合功能简单、逻辑独立的中间件。


## 实例

使用时将中间件加入 middleware：

```text
agent = create_agent(
    model="deepseek:deepseek-flash",
    middleware=[log_before, log_after]
)
```

装饰器定义的中间件可以在多个 Agent 中复用。


### 方式二：继承 AgentMiddleware

如果一个中间件需要多个钩子、内部配置或者状态管理，可以使用类继承。


## 实例

类中只需要实现实际使用的钩子，不需要把六个方法全部写出来。

默认情况下，中间件名称通常使用类名，也可以根据实际需求配置。

注意：对于简单日志，装饰器已经足够。只有逻辑复杂、需要维护配置或组合多个钩子时，才建议使用类继承。


## 四、before_agent：Agent 开始前

before_agent 在 Agent 主流程开始前运行，适合进行初始化、输入检查与基础日志记录。

例如，记录用户消息数量：


## 实例

在正常的完整执行中，before_agent 通常在一次 Agent 调用开始时执行。

但如果涉及持久化检查点、执行恢复或中断，不应该简单认为每次恢复都一定重新运行所有生命周期钩子。


## 五、before_model：模型调用前

before_model 在模型调用前运行。

与 before_agent 不同，如果 Agent 需要多次调用模型，before_model 也可能执行多次。

它适合检查消息、修改状态，或者在满足条件时提前结束当前执行。


### 实例：限制消息数量


## 实例

这里的 can_jump_to=["end"] 声明允许该钩子跳转到结束流程。

如果消息数量达到限制，钩子返回新的 AIMessage，并控制 Agent 结束。

注意：这只是演示消息数量限制，不是 Token 数量限制，也不能替代实际上下文窗口管理。


## 六、after_model：模型调用后

after_model 在模型获得响应后运行。

可以用于记录模型是否发起工具调用，或者更新执行统计信息。


### 实例：检查工具请求


## 实例

如果模型请求了工具，Agent 之后可能进入工具执行节点。

如果没有工具调用，并且没有其他执行控制要求，Agent 通常会结束当前循环。

另外，after_model 可以通过返回状态字典更新自定义状态字段，但对应字段需要在 Agent State Schema 中定义。


## 七、wrap_model_call：拦截模型调用

wrap_model_call 是功能较强的 Middleware 钩子。

它可以通过 handler 包裹一次模型调用，并控制请求执行方式。

典型场景包括：

- 模型 API 请求失败后重试。
- 根据条件切换模型。
- 统计模型调用耗时。
- 修改模型请求参数。
- 缓存特定模型请求。


### 实例：记录模型调用耗时


## 实例

这里的 handler(request) 执行实际模型调用。

如果不调用 handler，就不会按通常流程执行被包装的模型请求。


### 实例：失败后重试

下面提供一个简化的重试示例：


## 实例

示例只捕获 TimeoutError，并非所有提供商超时异常都属于此类型。

真实项目推荐针对当前模型集成实际抛出的异常进行处理，加入指数退避及重试上限。

LangChain 也提供现成的 ModelRetryMiddleware，一般不需要从零编写完整的重试机制。


## 八、wrap_tool_call：拦截工具执行

wrap_tool_call 用于包装 Agent 中的工具执行。

可以在调用工具前后记录日志，或者捕获特定工具执行异常。


### 实例：记录工具调用


## 后续章节

- 实例
- 九、after_agent：Agent 执行结束后
- 实例
- 十、完整实例：观察 Middleware 生命周期
- 完整实例
- 可能的运行结果
- 十一、Middleware 的返回值与状态更新
- 实例：统计模型调用次数
- 实例
- 十二、多个 Middleware 的执行顺序
- 十三、内置 Middleware：无需重复造轮子
- 实例：限制模型调用次数
- 实例
- 十四、Middleware 与流式事件
- 实例：自定义状态事件
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `LangChain 中间件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
