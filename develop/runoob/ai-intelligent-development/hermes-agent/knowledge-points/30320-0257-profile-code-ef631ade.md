# 知识点 30320：Hermes Agent：Hermes Agent Profile - 什么是 Profile

- 来源：[Hermes Agent Profile](https://www.runoob.com/hermes-agent/hermes-agent-profile.html)
- 来源章节：[0257-hermes-agent-profile-practice.md](../chapters/0257-hermes-agent-profile-practice.md)
- 分类：AI / 智能开发
- 技术：Hermes Agent
- 所在小节：什么是 Profile
- 知识类型：代码
- 原章节序号：0257

## 原文片段

```text
~/.hermes/profiles/<name>/
├── config.yaml     # 模型、工具、终端后端等所有设置
├── .env            # API Key、Bot Token（各档案各自独立）
├── SOUL.md         # Agent 人格与身份设定
├── memories/       # 独立的持久记忆（MEMORY.md、USER.md）
├── skills/         # 独立的技能目录
├── cron/           # 独立的定时任务
└── state.db        # 独立的会话历史数据库
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `什么是 Profile` 这一小节和 `Hermes Agent Profile` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
