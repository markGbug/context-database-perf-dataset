# 知识点 59526：LangChain：LangChain create_agent() 函数 - 一、create_agent() 的工作原理

- 来源：[LangChain create_agent() 函数](https://www.runoob.com/langchain/langchain-create_agent.html)
- 来源章节：[0279-langchain-create_agent-concept.md](../chapters/0279-langchain-create_agent-concept.md)
- 分类：AI / 智能开发
- 技术：LangChain
- 所在小节：一、create_agent() 的工作原理
- 知识类型：代码
- 原章节序号：0279

## 原文片段

```text
用户输入
    |
    v
  Model 节点
    |
    | 模型是否发起工具调用？
    |
    +-- 否 --> 返回最终结果
    |
    +-- 是
          |
          v
       Tools 节点
          |
          | 执行工具
          | 将结果加入消息历史
          |
          v
       Model 节点
          |
          | 继续判断是否调用工具
          v
        ...
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `一、create_agent() 的工作原理` 这一小节和 `LangChain create_agent() 函数` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
