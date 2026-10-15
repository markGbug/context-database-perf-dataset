# Ollama：Ollama 编程语言调用

- 来源：[Ollama 编程语言调用](https://www.runoob.com/ollama/ollama-programming-access.html)
- 分类：AI / 智能开发
- 技术：Ollama
- 笔记类型：概念卡
- 章节序号：0403

## 本章内容

本篇系统梳理调用 Ollama 的四条代码路线：Python 官方库、JavaScript 官方库、原生 HTTP、以及 OpenAI / Anthropic 兼容 SDK，并用两个实战项目把它们串起来。


## 官方 SDK：Python 与 JavaScript

官方提供两个一手维护的库，接口设计保持一致，会一个就等于会两个。


## 安装

两个库的核心方法对照：

Python 中一次带全参数的 chat 调用，覆盖前面几篇学过的大部分能力：


## 实例

JavaScript 中的等价写法：


## 实例

连接非默认地址（如远程服务器或 Ollama Cloud）时，用 host 与 headers 指定：


## 实例


## 原生 HTTP：curl 速查

写脚本、调试接口、排查问题时，curl 是最快的工具。


## 复用 OpenAI / Anthropic SDK

已有项目迁移时，兼容层比重写省事得多。

JavaScript 项目里用 OpenAI SDK 接入本地模型：


## 实例

Python 项目里用 Anthropic SDK 同理：


## 实例

选择建议：新项目直接用官方 SDK（能力最全）；存量项目按现有 SDK 走兼容层（改动最小）；被某个只认 OpenAI 协议的框架集成时，兼容层是唯一通路。


## 实战一：命令行聊天脚本

用不到 40 行 Python，把前面学的 chat、流式、历史管理拼成一个可用的终端聊天工具。


## 实例

```text
$ python cli_chat.py
开始对话（模型 qwen3.5:4b），输入 exit 退出。

你：什么是 Python 的切片？
助手：切片是用 [start:stop:step] 从序列中取子序列的语法，
例如 s[1:3] 取索引 1 到 2 的元素。

你：给个 RUNOOB 风格的例子
助手：s = "RUNOOB"
print(s[1:4])   # 输出 UNO

你：exit
```

核心只有一处：每轮把 user 消息和 assistant 完整回答都 append 进 messages。模型本身无状态，"记忆"完全来自这个列表。


## 实战二：带记忆的多轮对话 Web 应用

把同样的思路搬上浏览器，需要一个后端居中协调：管理会话历史、调用 Ollama、把流式结果转发给前端。


### 后端：Flask 封装 Ollama 流式接口


## 实例


### 前端：fetch 流式读取


## 实例


### 运行与验证


## 实例

第二次请求中模型能顺着"切片"话题继续作答，说明服务端管理的会话历史生效了；换一个 session 参数则是一个全新会话，互不干扰。

这个几十行的骨架已经覆盖了类 ChatGPT 应用的三大要素：会话隔离（session 参数）、流式体验（NDJSON 转发）、记忆持久（历史写回）。加上数据库存储和多会话列表，就是完整实战项目的雏形，Web 应用实战章节会继续扩展它。


## 记忆卡片

- 一句话定义：`Ollama 编程语言调用` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
