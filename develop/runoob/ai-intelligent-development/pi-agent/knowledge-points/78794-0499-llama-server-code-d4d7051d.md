# 知识点 78794：Pi Agent：Pi Agent 与 llama.cpp 本地模型 - 启动 llama-server 路由器

- 来源：[Pi Agent 与 llama.cpp 本地模型](https://www.runoob.com/pi-agent/pi-agent-llamacpp.html)
- 来源章节：[0499-pi-agent-llamacpp-practice.md](../chapters/0499-pi-agent-llamacpp-practice.md)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 所在小节：启动 llama-server 路由器
- 知识类型：代码
- 原章节序号：0499

## 原文片段

```text
llama-server \
  --models-dir ~/models \
  --no-models-autoload \
  --jinja \
  --host 127.0.0.1 \
  --port 8080 \
  -ngl 999 \
  -c 32768
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `启动 llama-server 路由器` 这一小节和 `Pi Agent 与 llama.cpp 本地模型` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
