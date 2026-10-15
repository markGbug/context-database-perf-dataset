# LangChain：LangChain 模型调用拦截——@wrap_model_call

- 来源：[LangChain 模型调用拦截](https://www.runoob.com/langchain/langchain-wrap-model-call.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：概念卡
- 章节序号：0288

## 本章内容

@wrap_model_call 是 LangChain Middleware 中重要的模型调用拦截机制。

与 @before_model 和 @after_model 不同，@wrap_model_call 可以直接包裹模型调用，通过自定义逻辑控制模型请求的执行方式。

例如，可以在调用模型之前检查请求，在执行失败时重试，切换备用模型，读取缓存，或者在特定条件下直接返回预设结果。

本章节基于 LangChain 1.x，介绍 handler 回调、ModelRequest、ModelResponse、请求修改、模型重试、故障转移、缓存和多个中间件组合。


## 一、什么是 @wrap_model_call？

@wrap_model_call 属于 LangChain 的 Wrap-style Middleware。

它通过包装模型执行过程，实现对模型请求和响应的拦截。

基本流程：

```text
Agent 准备调用模型
        ↓
  wrap_model_call
        ↓
检查或修改 ModelRequest
        ↓
   handler(request)
        ↓
     模型执行
        ↓
     ModelResponse
        ↓
修改或记录执行结果
        ↓
     返回 Agent
```

其中，handler 是关键。

调用 handler(request) 会继续执行被包装的模型请求；如果不调用 handler，就可以在符合协议的前提下直接返回结果。


### 基本语法


## 实例

与 Node-style Middleware 不同，这里不能直接返回普通 State 字典代替模型响应。

如果需要修改 Agent State，应使用对应的状态更新机制。


## 二、理解 ModelRequest 与 ModelResponse

wrap_model_call 中最重要的两个对象分别是：

- ModelRequest：当前准备发送给模型的请求。
- ModelResponse：模型执行后返回的消息及结构化结果。


### ModelRequest 的常用属性

其中，request.messages 是当前准备提交给模型的消息，不一定等同于完整的 Agent 历史状态。


### ModelResponse 的常用属性

例如，可以通过：

```text
response = handler(request)
for message in response.result:
    print(message.content)
```

读取模型返回的消息。

注意：handler(request) 通常返回 ModelResponse，而不是直接返回 AIMessage，因此不能在所有场景中使用 response.content。


## 三、场景一：记录模型调用耗时

最简单的应用是记录模型执行时间。

可以使用 Python 的 time.perf_counter() 统计每次调用的耗时。


### 实例


## 实例

执行时可能输出：

```text
[Model] 耗时：1.82 秒
Python 是一种通用编程语言，语法简洁易读。
```

这里使用 finally，即使模型调用抛出异常，也可以记录已经消耗的时间。

不过，如果模型执行失败，程序仍然会抛出原始异常，不会自动生成成功结果。


## 四、场景二：模型调用失败后重试

模型 API 可能因为网络中断、请求超时或者服务端临时故障而失败。

对于适合重试的临时错误，可以使用 wrap_model_call 调用 handler 多次。


### 实例：限制重试次数


## 实例

这里最多调用 handler 三次，等待时间分别为 1 秒、2 秒。

需要注意，实际模型 SDK 的超时异常不一定是 Python 内置的 TimeoutError。

生产环境应该根据具体模型提供商的异常类型处理，并区分：

- 网络超时、临时服务端错误：通常可以有限重试。
- 限流错误：应结合 Retry-After 或退避策略。
- API Key 无效、请求参数错误：通常不应该重复重试。
- 内容或权限限制：不能简单通过重试绕过。

此外，重复调用模型会增加请求次数和费用。


### 推荐：使用内置 ModelRetryMiddleware

LangChain 已经提供 ModelRetryMiddleware，一般不需要自行实现重试和退避机制。


## 实例

这里 max_retries=2 表示允许额外重试，具体执行次数还受到异常处理配置影响。

注意：模型集成本身也可能配置重试次数。应检查两层重试的叠加效果，避免发生远超预期的 API 请求。


## 五、场景三：模型降级与故障转移

如果主模型不可用，可以切换到备用模型。

这种机制称为 Fallback（故障转移）。

例如，主模型因为临时错误失败后，可以尝试使用另一个模型服务。

需要注意，备用模型应该是确实不同的模型或部署，而不是简单地将同一个模型重新初始化。


### 实例：通过 request.override() 切换模型


## 实例

这个示例需要同时安装：

```text
pip install -U langchain-deepseek langchain-openai
```

并配置：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
OPENAI_API_KEY=your_openai_api_key
```

主模型失败后，代码会重新使用备用模型执行请求。

如果备用模型也失败，异常继续向上抛出。

注意：上面的示例为了突出原理，捕获了所有异常。真实项目应限制可触发故障转移的异常类型，避免把鉴权错误或不正确的业务配置掩盖为普通服务故障。


### request.override() 的作用

request.override() 返回新的 ModelRequest，不会原地修改旧请求。

例如：

```text
new_request = request.override(model=fallback_model)
response = handler(new_request)
```

除了模型，还可以修改系统消息、当前消息列表、工具定义和其他受支持的请求配置。


### 推荐：使用 ModelFallbackMiddleware

对于常见的故障转移需求，可以使用 LangChain 内置中间件。


## 实例

内置中间件可以在主模型调用失败后尝试备用模型。

如果主模型和备用模型来自不同提供商，需要确保二者都支持当前 Agent 所需的工具调用、结构化输出和其他能力。

另外，跨模型故障转移还应考虑数据传输范围、隐私政策和费用差异。


## 六、场景四：缓存模型响应

如果多个模型请求完全相同，可以考虑缓存响应，减少重复请求。

但缓存 Agent 模型结果比缓存普通字符串复杂。

因为模型输出可能受到以下信息影响：

- 系统提示词。
- 完整消息历史。
- 工具定义。
- 模型名称与参数。
- 结构化输出配置。
- 运行时上下文。

因此，不能只根据最后一条用户消息创建缓存键。


### 为什么原来的缓存方式有问题？

例如：

```text
cache_key = last_content[:200]
```

这种写法可能导致两个不同请求使用相同的缓存键。

同时，用户发送相同的问题，不代表模型应该返回相同的结果。

例如，在不同对话历史下：

```text
用户 A：介绍一下 Python。
用户 B：介绍一下 Python。
```

两个用户的系统权限、回答语言或工具数据可能不同。

如果共享错误的缓存结果，可能造成数据泄露或者返回不相关的信息。


### 实例：只缓存简单无工具请求

下面创建一个适合教学的内存缓存示例，仅处理固定模型、没有工具、没有结构化输出的简单请求。


## 实例

这个示例通过完整消息内容、系统提示和模型信息构造缓存键，避免仅使用最后 200 个字符。

但这仍然只是教学实现，不适合直接作为生产级多用户缓存。

真实项目还需要考虑：

- 模型参数、API 版本与结构化输出配置。
- 用户、租户与数据访问隔离。
- 缓存有效期和容量限制。
- 工具数据变化后的缓存失效。
- 并发请求去重。
- 响应中可能包含的敏感信息。

注意：上述示例使用进程内字典，程序重启后缓存会消失，也不适合多进程共享。

如果只是希望缓存普通模型调用结果，也可以考虑 LangChain 的模型缓存机制，而不必专门使用 Middleware 实现。


## 后续章节

- 七、场景五：修改模型请求
- 实例：动态注入时间信息
- 实例
- 八、短路返回：不调用模型
- 实例：返回固定回复
- 实例
- 九、多个 wrap_model_call 的组合顺序
- 实例：观察执行顺序
- 实例
- 十、缓存与重试的执行顺序
- 十一、同步与异步 wrap_model_call
- 实例：异步记录模型调用时间
- 实例
- 十二、完整实例：模型调用监控与重试
- 完整实例
- 十三、生产环境注意事项

## 记忆卡片

- 一句话定义：`LangChain 模型调用拦截` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
