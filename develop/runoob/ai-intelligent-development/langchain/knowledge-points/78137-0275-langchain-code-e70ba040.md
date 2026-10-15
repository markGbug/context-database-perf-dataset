# 知识点 78137：LangChain：LangChain 消息类型 - 一、LangChain 的核心消息类型

- 来源：[LangChain 消息类型](https://www.runoob.com/langchain/langchain-messages.html)
- 来源章节：[0275-langchain-messages-practice.md](../chapters/0275-langchain-messages-practice.md)
- 分类：AI / 智能开发
- 技术：LangChain
- 所在小节：一、LangChain 的核心消息类型
- 知识类型：代码
- 原章节序号：0275

## 原文片段

```text
HumanMessage
    ↓
AIMessage（包含 tool_calls）
    ↓
ToolMessage（工具执行结果）
    ↓
AIMessage（最终回答）
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `一、LangChain 的核心消息类型` 这一小节和 `LangChain 消息类型` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
