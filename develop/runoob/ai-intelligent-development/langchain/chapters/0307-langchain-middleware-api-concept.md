# LangChain：LangChain Middleware API 参考

- 来源：[LangChain Middleware API](https://www.runoob.com/langchain/langchain-middleware-api.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：概念卡
- 章节序号：0307

## 本章内容

在 LangChain 1.x 中，Middleware（中间件） 是扩展 Agent 行为的重要机制。

通过 Middleware，开发者可以在模型调用之前或之后执行自定义代码，控制工具调用、调整系统提示词、记录日志、处理异常，甚至修改 Agent 的执行流程。

例如，一个智能客服 Agent 可以通过 Middleware 实现：

- 模型调用前检查用户输入。
- 根据用户身份动态调整可用工具。
- 为模型调用设置重试或备用模型。
- 记录模型与工具的调用耗时。
- 执行敏感操作时检查权限。
- 在 Agent 完成后处理最终回答。

本章节基于 LangChain 1.x，整理 AgentMiddleware 基类、全部主要 Hook、装饰器参数、ModelRequest、ModelResponse、ExtendedModelResponse，以及 Middleware 的执行顺序和状态更新方式。


## 一、Middleware 的工作原理

一个普通 LangChain Agent 的执行过程如下：

```text
用户消息
    ↓
调用模型
    ↓
是否需要工具？
    ├── 否 → 返回回答
    └── 是 → 执行工具 → 再次调用模型
```

加入 Middleware 后，流程变成：

```text
用户消息
    ↓
before_agent
    ↓
before_model
    ↓
wrap_model_call
    ↓
调用模型
    ↓
after_model
    ↓
是否需要工具？
    ├── 是
    │    ↓
    │  wrap_tool_call
    │    ↓
    │  执行工具
    │    ↓
    │  返回 before_model
    │
    └── 否
         ↓
      after_agent
         ↓
       返回结果
```

这是一幅简化的执行流程图，实际执行还会受到 Middleware 跳转、中断、结构化输出和错误处理等配置的影响。

Middleware 主要有两种类型：


## 二、AgentMiddleware 基类

AgentMiddleware 是自定义 Middleware 的基类。

开发者可以继承它，并重写需要使用的 Hook。

```text
from langchain.agents.middleware import AgentMiddleware

class MyMiddleware(AgentMiddleware):
    def before_model(self, state, runtime):
        return None
```

一个 Middleware 不需要实现全部 Hook。只需要实现实际使用的方法。


### AgentMiddleware 主要属性

其中 transformers 和 trace_policy 属于较新的扩展能力，使用时需要注意实际安装的 LangChain 版本。


## 三、AgentMiddleware 全部主要 Hook

AgentMiddleware 提供同步和异步 Hook。

其中：

- before_agent 和 after_agent 位于 Agent 执行周期的外围。
- before_model 和 after_model 随模型调用循环执行，可能运行多次。
- wrap_model_call 包裹模型请求。
- wrap_tool_call 包裹每次工具执行。

注意：同步 Hook 与异步 Hook 需要根据执行方式正确实现。一个自定义 Middleware 如果只实现同步逻辑，不应直接假设所有异步操作都能自动适配。


## 四、Middleware 装饰器一览

除了继承 AgentMiddleware，也可以直接使用装饰器创建 Middleware。

装饰器更适合逻辑比较简单、只需要单个 Hook 的场景。

常见导入方式：

```text
from langchain.agents.middleware import (
    AgentMiddleware,
    before_agent,
    after_agent,
    before_model,
    after_model,
    wrap_model_call,
    wrap_tool_call,
    dynamic_prompt,
    hook_config
)
```

其中，装饰器参数的支持范围可能随着版本更新而扩展。表中列出了日常开发中最需要掌握的配置。


## 五、before_agent：Agent 开始前执行

before_agent 用于在 Agent 运行开始时执行预处理逻辑。

常见用途：

- 初始化自定义状态。
- 记录请求开始信息。
- 检查应用层面的输入条件。
- 准备本次执行所需的数据。


### 实例：记录 Agent 启动


## 实例

返回 None 表示不修改 Agent State。

如果返回字典，则可以更新对应的状态字段。

注意：before_agent 并不适合替代每轮模型调用前的检查。需要检查每一轮模型请求时，应该使用 before_model。


## 六、before_model：模型调用前执行

before_model 在每次模型调用前运行。

例如，Agent 执行三个模型调用周期，before_model 就可能执行三次。


### 实例：统计消息数量


## 实例

before_model 也可以根据条件提前结束执行。


### 实例：提前拦截测试指令


## 实例

这里的：

```text
can_jump_to=["end"]
```

声明允许 Hook 提前结束执行。

重要：如果需要在 Hook 中使用 jump_to，应明确配置允许的跳转目标。它不是一个可以任意指定节点名称的通用跳转接口。


## 七、after_model：模型回复后执行

after_model 在每次模型调用获得响应后执行。

适合：

- 记录模型调用结果。
- 更新模型调用计数。
- 检查模型是否请求了工具。
- 根据模型回复决定是否继续执行。


### 实例：记录工具调用


## 实例

需要注意，after_model 可能多次触发，因此不适合无条件追加一次性客服签名。

如果需要在整个 Agent 正常结束后格式化最终回答，通常可以考虑 after_agent。


## 八、after_agent：Agent 完成后执行

after_agent 通常用于处理 Agent 正常执行完成后的状态。

例如：

- 记录任务完成信息。
- 格式化最终回答。
- 汇总执行结果。
- 更新完成状态。


### 实例：给最终回答添加标记


## 实例

这里保留了 AIMessage 的原始 ID，因此在支持 add_messages Reducer 的状态中，可以更新已有消息，而不是简单追加一条新的回答。

注意：after_agent 不是通用的 finally 处理器。如果执行中发生未处理异常，不应假定它一定执行。需要无论成功或失败都清理资源时，应在应用层使用 try/finally 或上下文管理器。


## 九、wrap_model_call：包裹模型调用

wrap_model_call 是控制模型执行的核心 Hook。

它与 before_model 的区别在于，wrap_model_call 能够直接控制底层模型处理器是否执行。

基本形式：

```text
@wrap_model_call
def middleware(request, handler):
    return handler(request)
```

其中：

- request：本次模型请求的 ModelRequest。
- handler：真正执行下一层模型调用的处理函数。

Middleware 可以：

- 调用 handler 一次，正常执行。
- 在特定错误时调用多次，实现重试。
- 不调用 handler，直接返回自定义结果。
- 通过 request.override() 修改模型或请求内容。


### 实例：记录模型调用耗时


## 实例

这里的计时覆盖 handler(request) 的同步执行过程。

如果底层处理器抛出异常，finally 仍会打印耗时。

这类 Middleware 适合记录延迟和性能指标，但不要在生产日志中直接输出包含隐私的完整请求内容。


## 十、使用 request.override() 修改模型请求

ModelRequest.override() 会创建一个修改后的新请求对象。

原始 request 不会直接被修改。

例如，我们可以动态替换系统消息：


## 实例

也可以修改模型：

```text
new_request = request.override(
    model=different_model
)
```

或者调整允许使用的工具：

```text
new_request = request.override(
    tools=[selected_tool]
)
```

注意：tools 只能使用已注册、可以由 Agent 执行的工具。不能简单将任意新工具对象加入 request.tools，就假定底层 ToolNode 自动具备执行能力。


## 后续章节

- 十一、ModelRequest 关键属性
- ModelRequest.override() 支持的常见字段
- 十二、dynamic_prompt：动态系统提示词
- 实例：根据日期生成系统提示词
- 实例
- 十三、wrap_tool_call：包裹工具执行
- 实例：记录工具执行
- 实例
- 十四、wrap_tool_call：处理工具异常
- 实例：只处理指定异常
- 实例
- 十五、ModelResponse 数据结构
- 实例：读取 ModelResponse
- 实例
- 十六、ModelCallResult 返回类型
- 实例

## 记忆卡片

- 一句话定义：`LangChain Middleware API` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
