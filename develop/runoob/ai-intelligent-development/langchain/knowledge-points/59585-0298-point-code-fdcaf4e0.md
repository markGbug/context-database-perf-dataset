# 知识点 59585：LangChain：LangChain 智能客服 - 一、项目功能与需求分析

- 来源：[LangChain 智能客服](https://www.runoob.com/langchain/langchain-project-customer-service.html)
- 来源章节：[0298-langchain-project-customer-service-study.md](../chapters/0298-langchain-project-customer-service-study.md)
- 分类：AI / 智能开发
- 技术：LangChain
- 所在小节：一、项目功能与需求分析
- 知识类型：代码
- 原章节序号：0298

## 原文片段

```text
用户发送消息
       ↓
    智能客服
       ↓
  Middleware 检查
       ↓
     大语言模型
       ↓
   判断任务类型
       |
       ├── 课程问题 → RAG 检索知识库
       |
       ├── 订单问题 → 订单查询工具
       |
       ├── 人工转接 → interrupt() 暂停
       |                  ↓
       |               人工处理
       |                  ↓
       |           Command(resume)
       |
       └── 普通问题 → 模型回答
       ↓
   最终回复格式化
       ↓
    Checkpointer
       ↓
     返回用户
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `一、项目功能与需求分析` 这一小节和 `LangChain 智能客服` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
