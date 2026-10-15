# 知识点 50027：LangChain：LangChain 工具调用拦截 - 一、什么是 @wrap_tool_call？

- 来源：[LangChain 工具调用拦截](https://www.runoob.com/langchain/langchain-wrap-tool-call.html)
- 来源章节：[0289-langchain-wrap-tool-call-concept.md](../chapters/0289-langchain-wrap-tool-call-concept.md)
- 分类：AI / 智能开发
- 技术：LangChain
- 所在小节：一、什么是 @wrap_tool_call？
- 知识类型：代码
- 原章节序号：0289

## 原文片段

```text
用户发送问题
      ↓
模型生成工具调用请求
      ↓
wrap_tool_call：执行前检查
      ↓
handler(request)
      ↓
执行 Python 工具
      ↓
ToolMessage 或 Command
      ↓
wrap_tool_call：结果处理
      ↓
返回 Agent，继续执行
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `一、什么是 @wrap_tool_call？` 这一小节和 `LangChain 工具调用拦截` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
