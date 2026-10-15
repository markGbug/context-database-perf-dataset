# DeepSeek Harness：DeepSeek Harness LLM 适配器：接入任意模型

- 来源：[DeepSeek Harness LLM 适配器](https://www.runoob.com/deepseek-harness/deepseek-harness-llm-adapter.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：概念卡
- 章节序号：0236

## 本章内容

模型提供方不止 DeepSeek 一家，想把 dsh 接到自己的模型端点，就要写一个 LLM 适配器。

本章节我们将讲 LlmAdapter 抽象类、stream() 方法、路由注册与 cordis.yml 配置。


## LLM 适配器是什么

LLM 适配器是一个继承 LlmAdapter 并实现 stream() 方法的类。

它把 Harness 的提供方无关请求，转换成具体提供方的 API 调用。

它再把响应转换回 Harness 的分片，也就是 StreamChunk。

因此 agent-loop 消费的是统一接口，不关心背后是哪家 API。

顶层是 agent-loop，它消费提供方无关的流式生成服务。

中间是 ctx.llm 注册表，维护 LlmAdapter 的抽象契约。

底层是各个适配器，分别对接不同的 API 格式。

注册时用 ctx.llm.registerAdapter(['my-provider'], adapter) 绑定路由。


## 最小实现

官方文档给了一个最小骨架，我们照着写并补上注释。

stream() 是核心，返回一个异步生成器 AsyncIterable。

三步注释标出了标准流程：转换消息格式、调用流式 API、把响应转成 StreamChunk。


## 实例

apiKey 来自插件配置，避免把密钥硬编码进代码。

providers 数组声明这个适配器负责哪些提供方路由。

apply 里先 new MyAdapter(config.apiKey)，再 registerAdapter 完成注册。

inject: ['llm'] 保证 ctx.llm 服务就绪后才执行 apply。

stream() 返回的是异步生成器，用 yield 逐片往外吐数据。

下一篇会详细讲 StreamChunk 的分片协议。


## GenerateOptions：适配器收到什么

stream() 接收仓库导出的 GenerateOptions。

它包含模型、推理强度、对话历史、系统提示词、工具 schema、生成参数、停止序列与中止信号。

完整字段以 @deepseek-ai/dsh-llm 导出的 TypeScript 类型为准。

适配器必须把支持的字段映射到具体 API。

如果某个字段无法支持，应抛出带稳定 code 的 LlmError，不得静默丢弃。

不支持的字段要明确报错，而不是悄悄忽略；否则模型会拿到残缺的结果。


## 注册适配器

apply 里调用 ctx.llm.registerAdapter 完成路由注册。


## 实例

第一个参数是适配器处理的提供方路由列表。

GenerateOptions.provider 会选择已注册的适配器。

GenerateOptions.model 则传入由适配器拥有、无需在生命周期启动时注册的模型 id。

如果适配器能向选择器公布模型选项，可以覆写 listModels()。

需要返回确切的提供方与模型身份时，可以覆写 resolveModel(provider, model, signal?)。

resolveModel 一次查询返回确切的提供方、模型身份，以及可选的 context 和 reasoning 元数据。

reasoning 元数据描述模型可选的推理强度：有序的不透明 ID、展示名称，以及可选的配置默认值。

保留适配器给出的权威可选列表，包括上游能力 API 返回的 off，不要把这些值提升为核心枚举。

异步查询必须响应可选的 signal，让取消和资源释放过程完全停稳。

服务会校验聚合结果：显式指定但不支持的推理强度，会在调用 stream() 之前被拒绝。

省略 reasoning，表示该模型没有可选的推理强度能力。


## 在 cordis.yml 中使用

把适配器插件和 agent-loop 一起加载，并让 agent-loop 用新的 provider 与 model。


## 实例

my-llm 插件的 config.apiKey 从环境变量 MY_API_KEY 读取，不落盘。

providers 数组把 my-provider 这个路由注册给 MyAdapter。

agent-loop 的 agents.main 配置 provider 与 model，生成请求时就会命中新适配器。


## 实战参考

仓库里有现成的两个完整实现可以对照。

llm-deepseek 适配 DeepSeek API，走 OpenAI 兼容格式。

llm-pi-ai 适配 Pi AI，是不同的 API 格式。

对比这两个适配器，可以看到同一套 harness 契约如何在不同提供方 SDK 之上实现。

先读 llm-deepseek 再读 llm-pi-ai，最容易看出「契约不变、实现各异」的 seam 思想。


## 小结与自测

一句话总结：LLM 适配器 = 继承 LlmAdapter + 实现 stream() + registerAdapter 路由注册 + cordis.yml 配置。

自测题一：stream() 的返回值类型是什么？

自测题二：registerAdapter 的第一个参数代表什么？

自测题三：agent-loop 通过哪些配置项选择新适配器？


## 记忆卡片

- 一句话定义：`DeepSeek Harness LLM 适配器` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
