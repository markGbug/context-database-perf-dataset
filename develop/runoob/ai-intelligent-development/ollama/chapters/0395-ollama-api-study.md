# Ollama：Ollama REST API 编程接入

- 来源：[Ollama API 交互](https://www.runoob.com/ollama/ollama-api.html)
- 分类：AI / 智能开发
- 技术：Ollama
- 笔记类型：学习笔记
- 章节序号：0395

## 本章内容

Ollama 安装后在本地 11434 端口提供一整套 REST API，覆盖文本生成、对话、向量嵌入和模型管理，并提供 OpenAI、Anthropic 两套兼容协议。

本篇逐个讲透核心接口：请求结构、流式处理、用量统计、错误处理，让任何语言都能接入本地模型。


## 两个 Base URL 与认证方式

Ollama 的 API 有本地和云端两个入口，认证规则不同。

本地服务默认免认证，开箱即用；直连 ollama.com 的云端接口时，先在官网设置页创建 API Key 并放入请求头。


## 文本生成：/api/generate

generate 是最基础的单轮生成接口，传入模型名和提示词即可：


## 实例

stream 设为 false 时返回单个 JSON 对象：

```text
{
  "model": "qwen3.5",
  "created_at": "2026-08-29T03:20:00.499127Z",
  "response": "RUNOOB（菜鸟教程）是一个面向编程初学者的免费中文教程网站。",
  "done": true,
  "total_duration": 10706818083,
  "load_duration": 6338219291,
  "prompt_eval_count": 26,
  "prompt_eval_duration": 130079000,
  "eval_count": 42,
  "eval_duration": 4232710000
}
```

常用参数如下：

两个实用小技巧：发送空 prompt 可以把模型预加载进内存，消除首次请求的加载等待；把 keep_alive 设为 0 并配合空 prompt 则可以立即卸载模型释放显存。


## 实例


## 对话生成：/api/chat

chat 是多轮对话接口，消息历史由调用方自己维护，这是与 generate 的本质区别。


## 实例

消息对象支持的字段：

多轮对话的正确姿势：把模型每轮返回的 assistant 消息追加回 messages 数组，再带上新一轮问题发送，模型就能"记住"完整上下文。

messages 完全由你管理，意味着历史可以持久化到数据库、可以做摘要压缩、也可以跨会话恢复——第 5 篇提到的"命令行退出即失忆"问题，在这里就有了工程解法。


## 向量嵌入：/api/embed

embed 接口把文本转成向量，是 RAG 与语义搜索的原料车间。


## 实例

响应中的 embeddings 是二维数组，每个向量已做 L2 归一化（单位长度），可直接用余弦相似度比较。

两个值得注意的参数：dimensions 可以指定输出向量维度（模型支持时可降维省存储）；truncate 默认 true 会自动截断超长文本，设为 false 则超长时报错。


## 流式与非流式：如何处理响应

生成类接口默认流式返回，格式是 NDJSON：每一行一个独立的 JSON 对象。

```text
{"model":"qwen3.5","created_at":"...","response":"RUNOOB","done":false}
{"model":"qwen3.5","created_at":"...","response":"（菜鸟教程）","done":false}
{"model":"qwen3.5","created_at":"...","response":"是编程初学者的入门网站。","done":false}
{"model":"qwen3.5","created_at":"...","response":"","done":true,"done_reason":"stop"}
```

客户端逐行读取、把 response 字段拼接起来就是完整回答，拼接过程可以实时渲染到界面上。

两种模式的取舍：

流式模式下错误可能发生在输出中途，此时 HTTP 状态码已无法更改，错误会以一行 {"error": "..."} 出现在数据流末尾，客户端解析时要检查这一行。


## 用量统计与错误处理

每个生成响应的末尾都带性能统计字段，是评估推理开销的第一手数据。

生成速度（token/s）的计算公式：eval_count / eval_duration * 10^9，字段时间单位均为纳秒。

错误处理方面，接口用标准 HTTP 状态码表达结果：

错误响应体固定为 {"error": "错误描述"} 结构，客户端统一取 error 字段即可。


## 模型管理接口速览

命令行能做的模型管理，API 全部对应一份，适合做管理后台或自动化脚本。

以 /api/tags 为例，响应包含每个模型的规格细节：

```text
{
  "models": [
    {
      "name": "qwen3.5:latest",
      "size": 6600000000,
      "details": {
        "family": "qwen3.5",
        "parameter_size": "9B",
        "quantization_level": "Q4_K_M"
      }
    }
  ]
}
```

quantization_level、parameter_size 这些字段可以直接用于做模型选择器界面。


## OpenAI 兼容接口

存量 OpenAI 应用切换到本地模型，通常只需要改一个 base_url。


## 实例

兼容范围覆盖五个端点：

两个高频差异点要留意：

其一，OpenAI 协议没有 num_ctx 概念，需要改上下文时先建一个带 PARAMETER num_ctx 的模型再用新名字调用（用第 7 篇的 Modelfile 或 cp 借名皆可）。

其二，部分字段暂不支持：tool_choice、logit_bias、n、logprobs 等，迁移前建议核对手册的支持清单。


## Anthropic 兼容接口

Ollama 同样提供 Anthropic Messages API 兼容层，Claude Code 等工具因此可以直接使用本地模型。


## 实例

接入 Claude Code 这类工具时，只需设置两个环境变量：


## 实例

需要注意的能力边界：tool_choice 强制指定、提示词缓存、批量接口、PDF 输入等 Anthropic 特性暂不支持；token 计数为近似值。


## 复习重点

- 能说明 `Ollama API 交互` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
