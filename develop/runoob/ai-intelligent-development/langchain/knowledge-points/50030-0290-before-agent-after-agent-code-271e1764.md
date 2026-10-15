# 知识点 50030：LangChain：LangChain @before_agent - 一、before_agent 与 after_agent 的区别

- 来源：[LangChain @before_agent](https://www.runoob.com/langchain/langchain-before-after-agent.html)
- 来源章节：[0290-langchain-before-after-agent-concept.md](../chapters/0290-langchain-before-after-agent-concept.md)
- 分类：AI / 智能开发
- 技术：LangChain
- 所在小节：一、before_agent 与 after_agent 的区别
- 知识类型：代码
- 原章节序号：0290

## 原文片段

```text
用户输入
    ↓
before_agent
    ↓
before_model
    ↓
模型调用
    ↓
after_model
    ↓
是否调用工具？
    ├── 是 → 执行工具 → 再次调用模型
    └── 否 → 继续
    ↓
after_agent
    ↓
返回最终结果
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `一、before_agent 与 after_agent 的区别` 这一小节和 `LangChain @before_agent` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
