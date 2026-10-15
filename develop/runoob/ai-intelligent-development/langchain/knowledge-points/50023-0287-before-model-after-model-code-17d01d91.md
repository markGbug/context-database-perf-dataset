# 知识点 50023：LangChain：LangChain 中间件钩子 - 一、before_model 与 after_model 的区别

- 来源：[LangChain 中间件钩子](https://www.runoob.com/langchain/langchain-before-after-model.html)
- 来源章节：[0287-langchain-before-after-model-study.md](../chapters/0287-langchain-before-after-model-study.md)
- 分类：AI / 智能开发
- 技术：LangChain
- 所在小节：一、before_model 与 after_model 的区别
- 知识类型：代码
- 原章节序号：0287

## 原文片段

```text
用户输入
    ↓
before_model
    ↓
模型调用
    ↓
after_model
    ↓
是否需要调用工具？
    ├── 是 → 执行工具 → 回到 before_model
    └── 否 → 返回最终结果
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `一、before_model 与 after_model 的区别` 这一小节和 `LangChain 中间件钩子` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
