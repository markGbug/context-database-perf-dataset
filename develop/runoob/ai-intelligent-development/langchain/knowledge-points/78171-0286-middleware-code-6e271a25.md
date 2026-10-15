# 知识点 78171：LangChain：LangChain 中间件 - 一、什么是 Middleware？

- 来源：[LangChain 中间件](https://www.runoob.com/langchain/langchain-middleware-concepts.html)
- 来源章节：[0286-langchain-middleware-concepts-study.md](../chapters/0286-langchain-middleware-concepts-study.md)
- 分类：AI / 智能开发
- 技术：LangChain
- 所在小节：一、什么是 Middleware？
- 知识类型：代码
- 原章节序号：0286

## 原文片段

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

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `一、什么是 Middleware？` 这一小节和 `LangChain 中间件` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
