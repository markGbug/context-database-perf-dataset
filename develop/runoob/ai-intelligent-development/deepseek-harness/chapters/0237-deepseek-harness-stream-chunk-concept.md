# DeepSeek Harness：DeepSeek Harness StreamChunk 协议与错误处理

- 来源：[DeepSeek Harness 错误处理](https://www.runoob.com/deepseek-harness/deepseek-harness-stream-chunk.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：概念卡
- 章节序号：0237

## 本章内容

适配器的 stream() 到底往外出什么样的数据？

答案是 StreamChunk，一种有严格顺序的分片协议。

这篇讲分片序列、关键规则，以及传输出错时怎么处理。


## StreamChunk 协议

StreamChunk 是 Harness 与适配器之间的流式协议。

一个内容块先用 block-start 开始，中间用 delta 增量传输，最后用 block-end 结束。

文本与工具调用是两类不同的内容块，各自走一遍 start / delta / end。

所有分片收尾时，先发 usage 报告 token 用量，再发 finish 声明结束原因。

上图自上而下是一次完整的分片序列。

先是一个文本块：block-start → text-delta × 2 → block-end。

再是一个工具调用块：block-start → tool-call-delta → block-end。

最后是 usage 与 finish。

finish 的 reason 为 stop 表示正常结束，为 tool-calls 表示请求执行工具。


## 完整分片序列

官方文档给了 exampleChunks，把一次生成的全部 chunk 按顺序产出。

text-delta 可以拆成多个分片，增量拼接成完整文本。

tool-call-delta 的 argumentsDelta 则是原始 JSON 文本的增量。


## 实例

CallId 是协议自带的工厂函数，用来生成工具调用 id。

argumentsDelta 可以在一个分片里完整生成，也可以分多个分片增量生成。


## 关键规则

协议有五条硬性规则，违反任何一条都会让消费方解析出错。

text-delta 与 tool-call-delta 都要带上所属块的 index，内容块之间不要交叉。


## 错误处理：用 LlmError 表达失败

适配器应通过带稳定 code 的 LlmError 抛出传输和协议故障。

agent-loop 会保留该错误及其 code，用于诊断和策略处理。

不要依赖普通 Error 被自动转换。

稳定的 code 让上层可以精确匹配错误类型，而不是解析错误字符串。

每个提供方 HTTP 请求还必须合并 attributionHeaders()。

同时要把 options.signal 传给 fetch，让取消和资源释放过程完全停稳。


## 实例

attributionHeaders() 把归属信息合并进请求头。

options.signal 存在时作为 fetch 的 signal 传入，取消请求时立即停止。

response.ok 为 false 时抛出 LlmError，code 是 PROVIDER_HTTP_ERROR。

骨架只 yield 一个 finish，真实适配器会在这里解析响应体。

LlmError 的第一个参数是消息，第二个参数是稳定 code。

上层按 code 做策略判断，因此 code 一旦发布就不要改动。


## 不能静默丢弃的字段

GenerateOptions 里若有适配器无法支持的字段，同样要抛 LlmError，不要静默丢弃。

推理元数据包含有序的不透明 ID、展示名称和可选的配置默认值。

请保留适配器给出的权威可选列表，包括其上游能力 API 返回的 off。

不要把可选推理强度提升为核心枚举，否则适配器会失去上游的灵活性。

服务会校验聚合结果，并在调用 stream() 前拒绝显式指定但不受支持的推理强度。

省略 reasoning 表示该模型没有可选的推理强度能力。


## 小结与自测

一句话总结：StreamChunk 协议用成对的块描述内容，用 usage 与 finish 收尾；失败时用带稳定 code 的 LlmError 表达。

自测题一：一个文本块最少需要哪几个分片？

自测题二：usage 与 finish 的先后顺序是什么？

自测题三：请求失败时，为什么用带 code 的 LlmError 而不是普通 Error？


## 记忆卡片

- 一句话定义：`DeepSeek Harness 错误处理` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
