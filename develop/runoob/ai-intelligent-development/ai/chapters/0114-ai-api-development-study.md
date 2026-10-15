# AI（人工智能）：AI API 开发

- 来源：[AI API 开发](https://www.runoob.com/ai/ai-api-development.html)
- 分类：AI / 智能开发
- 技术：AI（人工智能）
- 笔记类型：学习笔记
- 章节序号：0114

## 本章内容

在 web 界面使用 AI 聊天工具很方便，但要把 AI 能力真正融入你自己的产品、工作流、自动化脚本中，你需要的是 API。

API（Application Programming Interface）是应用程序之间通信的桥梁，通过 API，你的代码可以直接向 AI 模型发送请求并获取回复，不需要手动打开网页复制粘贴。

想象一下这些场景：

- 你的电商网站自动为每件商品生成描述文案。
- 你的笔记应用自动总结用户输入的长文。
- 你的客服系统自动分类和回复用户咨询。
- 这些功能都可以通过 AI API 实现。

本模块的目标是让你从"只会用 AI 聊天"变成"能让 AI 在你的代码里干活"。


## API 基础概念

在写代码之前，先搞懂几个核心概念。


### 什么是 API

API 就是一套约定好的对话方式，我们按特定格式发送请求，对方按特定格式返回结果。

用点餐打个比方：

- 你走进餐厅，拿到菜单（API 文档），知道可以点什么、怎么点（请求格式）。
- 你对服务员说：一份宫保鸡丁，少辣（发送 API 请求）。
- 厨房做好菜给你端上来（返回 API 响应）。

在这个过程中，你不需要进厨房，不需要知道菜怎么做的——这就是 API 的价值：封装复杂细节，只暴露简单接口。


### REST API 基本原理

REST（Representational State Transfer）是目前最流行的 API 设计风格。

简单来说，就是用 HTTP 协议的方式来通信：

AI API 绝大多数是 POST 请求，因为我们要"发送内容给 AI 处理"。


### JSON 格式入门

JSON（JavaScript Object Notation）是 API 通信中最常用的数据格式。

JSON 的语法很简单，就是键值对的组合。


## 实例

这就是一个典型的 AI API 请求体。

几个核心规则：

- 对象用 { } 包裹，数组用 [ ] 包裹。
- 字符串用双引号 "，不能用单引号。
- 键值对用冒号 : 分隔，键必须是字符串。
- 多个键值对用逗号 , 分隔。

JSON 看起来和 Python 字典很像，但语法上有区别，写代码时要注意。


## 开发环境准备

工欲善其事，必先利其器。


### Python 安装与配置

Python 是调用 AI API 最常用的语言，生态完善，库丰富。

先检查你电脑上有没有安装 Python：

```text
# 检查 Python 版本（Windows、macOS、Linux 通用）
python --version
# 或者
python3 --version
```

推荐使用 Python 3.9 或更高版本。

如果还没安装，去 python.org 下载最新稳定版。


### pip 包管理

pip 是 Python 的包管理器，用来安装第三方库。

```text
# 检查 pip 版本
pip --version
# 或者
pip3 --version

# 升级 pip 到最新版本
pip install --upgrade pip

# 配置国内镜像源（可选，提升下载速度）
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```


### 代码编辑器选择

写 AI API 代码，推荐以下编辑器之一：

本教程的示例代码在任何编辑器中都能运行。


## OpenAI API 入门

OpenAI API 是最经典、生态最完善的 AI API，很多其他厂商也兼容它的格式。


### 注册与获取 API Key

API Key 是你的通行证，证明你的身份，记录你的用量，获取步骤：

- 1. 访问 platform.openai.com 注册账号
- 2. 进入 API Keys 页面
- 3. 点击 "Create new secret key"
- 4. 复制保存这个 Key（只显示一次！）

重要：永远不要把 API Key 提交到公开的代码仓库里。一旦泄露，别人可能用你的额度产生费用。


### 第一个 API 调用

先安装 OpenAI 的官方 SDK：

```text
pip install openai
```

现在写第一个 API 调用程序：


## 实例

如果没有 OpenAI 的 api_key ，也可以使用国内替代，国内很多模型都兼容 OpenAI，比如 DeepSeek，可以去 https://platform.deepseek.com/api_keys 申请 api_key 然后以下代码替换你的 api_key 和 model，DeepSeek 支持的模型为 deepseek-v4-flash、deepseek-v4-pro（思考模式） 即可使用 API 调用大模型：


## 实例

运行这个程序：

```text
python first_api_call.py
```

如果一切正常，你会看到类似这样的输出：

```text
完整响应：
ChatCompletion(
  id='chatcmpl-xxx',
  choices=[Choice(finish_reason='stop', index=0, message=ChatMessage(content='RUNOOB 菜鸟教程是一个专注于提供编程技术教程的学习平台...', role='assistant'))],
  model='gpt-3.5-turbo',
  usage=CompletionUsage(completion_tokens=30, prompt_tokens=18, total_tokens=48)
)

==================================================

AI 回复：
RUNOOB 菜鸟教程是一个专注于提供编程技术教程的学习平台，涵盖多种编程语言和技术领域。
```

恭喜！你已经成功调用了一次 AI API。


### 请求参数详解

OpenAI API 有很多参数可以调整，下面是最常用的几个：

重点说一下 temperature，这是最常用的调节参数：


## 实例

一个经验法则：

- temperature=0：事实回答、代码生成、需要精确结果的场景
- temperature=0.7：日常对话、通用任务
- temperature>1.0：创意写作、头脑风暴


## Anthropic Claude API

Claude 是 Anthropic 公司的大模型，以安全性和长文本处理能力著称。


### 与 OpenAI API 的异同

两者都能做文本生成，但设计理念有些区别：


### Claude Messages API 结构

先安装 Claude SDK：

```text
pip install anthropic
```

Claude API 的基本调用：


## 实例

同样的我们可以替换为国内兼容的大模型，比如 DeepSeek，指定 api_key 、 base_url、model 这三个参数：


## 实例


### System Prompt 设置

Claude API 中，System Prompt 是一个独立的参数，不是放在 messages 数组里：


## 实例


## 多轮对话管理

单轮对话简单，但真正有用的应用都需要"记住上下文"。


## 后续章节

- 对话历史的维护方式
- 实例
- 上下文窗口超限处理
- 实例
- 流式输出
- 什么是流式输出
- 实现打字机效果
- 实例
- 实例
- API 费用计算与优化
- Token 计费原理
- 如何控制 API 成本
- 实例
- 缓存策略
- 实例
- 错误处理与重试机制

## 复习重点

- 能说明 `AI API 开发` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
