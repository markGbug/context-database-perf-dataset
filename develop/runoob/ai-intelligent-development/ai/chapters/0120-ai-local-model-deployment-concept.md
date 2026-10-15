# AI（人工智能）：本地模型部署

- 来源：[本地模型部署](https://www.runoob.com/ai/ai-local-model-deployment.html)
- 分类：AI / 智能开发
- 技术：AI（人工智能）
- 笔记类型：概念卡
- 章节序号：0120

## 本章内容

很多人以为 AI 只能在云端使用，用 ChatGPT 时，数据要传到 OpenAI 的服务器，用 Claude 时，请求要发送到 Anthropic 的数据中心。

其实，AI 模型完全可以在你自己的电脑上运行。

想象一下：没有网络也能用 AI，敏感数据不会离开你的电脑，不需要为每次调用付费，想怎么定制就怎么定制。

这就是本地模型部署的价值。

本模块将带你从零开始，在自己的电脑上跑起第一个本地 AI 模型。


## 为什么需要本地 AI

云端 AI 很方便，但本地 AI 有不可替代的优势。


### 数据隐私保护

这是很多人选择本地部署的首要原因。

如果你要处理的是合同、病历、财务数据、内部文档，把这些数据传到第三方服务器是有风险的。

本地运行时，所有数据都在你自己的电脑上处理，不会离开你的设备。


### 无网络环境使用

飞机上、火车上、网络不稳定的地方，云端 AI 用不了。

本地模型下载一次后，永久可用，不需要网络连接。


### 成本控制

云端 AI 按调用次数或 Token 收费，用得多了也是一笔不小的开支。

本地模型一次性下载，之后随便用，不需要额外付费。


### 定制化可能

云端模型你没法改，只能用人家提供的功能。

本地模型你可以微调、可以量化、可以修改提示词模板，可以完全按照自己的需求定制。

这些优势对比：

不是说云端 AI 不好，而是说两者各有适用场景。日常闲聊用云端，处理敏感数据用本地；简单任务用云端，特殊定制用本地。


## 硬件需求评估

本地模型能不能跑、跑得多快，主要看你的硬件配置。


### CPU 推理 vs GPU 推理

模型运行有两种方式：CPU 推理和 GPU 推理。

CPU 推理就是用电脑的主处理器跑模型，优点是兼容性好，几乎所有电脑都能跑；缺点是速度慢，大模型可能要等很久。

GPU 推理用显卡跑，核心优势是并行计算能力强，跑模型速度快几十倍。

对于 NVIDIA 显卡，需要安装 CUDA 工具包；对于 AMD 显卡，可以用 ROCm；对于 Intel 显卡，可以用 OpenVINO。


### 显存需求与模型大小的关系

显存（VRAM）决定了你能跑多大的模型。

模型参数越多，需要的显存越大。但通过量化技术，可以用更小的显存跑更大的模型。


### Mac M 系列的优势

苹果 Silicon（M1、M2、M3 系列芯片）在本地 AI 方面有独特优势。

Apple 的 Metal 框架和统一内存架构，让 Mac 跑本地模型效率很高。

统一内存意味着CPU 和 GPU 共享内存，显存不够时可以自动借用内存。

一台 16GB 统一内存的 MacBook Pro，就能流畅跑 7B、13B 的量化模型。


### 推荐配置方案

根据不同的预算和需求，这里有几个配置方案：

不要被大模型这个词吓倒。今天的量化技术已经能让 7B 模型在普通电脑上流畅运行，而 7B 模型的能力对于大多数日常任务已经足够。


## Ollama：最简单的本地 AI 工具

- Ollama 官网：https://ollama.com/
- Ollama 支持模型列表：https://ollama.com/search
- Ollama 教程：https://www.runoob.com/ollama/ollama-tutorial.html

Ollama 是目前最流行的本地模型工具，一句话概括：像安装 App 一样安装模型，像用命令行一样用 AI。


### 安装与配置

Ollama 支持 macOS、Linux、Windows，安装过程非常简单。

安装包下载地址：https://ollama.com/download

一条命令安装：

```text
curl -fsSL https://ollama.com/install.sh | sh
```

macOS 用户可以直接下载安装包，或者用 Homebrew 安装：

```text
# macOS 使用 Homebrew 安装
brew install ollama

# 或者下载安装包：https://ollama.com/download
```

Windows 用户直接从官网下载安装包运行即可。

安装完成后，启动 Ollama 服务：

```text
ollama serve
```

看到服务启动成功后，就可以开始用了。


### 下载模型

Ollama 的模型库非常丰富，包括 Llama、Qwen、Gemma、Mistral 等主流模型。

下载模型只用一条命令：


## 实例

也可以使用 ollama run + 模型名 命令，如果没有指定的模型会主动下载：

```text
ollama run qwen
```

运行 qwen 模型，如果没有会下载。

每个模型有不同的版本，比如 8B、70B，或者不同的量化版本。

你可以用 ollama list 查看已经下载的模型：

```text
ollama list
```

输出类似：

```text
NAME              ID              SIZE      MODIFIED
qwen3.5:latest    6488c96fa5fa    6.6 GB    3 months ago
```


### 命令行使用

模型下载后，直接运行就可以开始对话：

```text
# 运行 Llama 3，没有会下载
ollama run llama3

# 运行 Qwen，没有会下载
ollama run qwen3.5
```

qwen3.5 用来做普通任务还是绰绰有余的：

然后你就可以直接和模型对话了：

```text
>>> 你好，请介绍一下你自己
你好！我是 Llama 3，由 Meta 开发的 AI 助手。我可以帮你回答问题、
写作、编程、分析数据等。有什么我可以帮你的吗？

>>> 用 Python 写一个 Hello World 程序
好的，这是一个简单的 Python Hello World 程序：

print("Hello, World!")

>>> /bye  # 输入 /bye 退出
```

常用命令：


### API 接口调用

Ollama 自带 HTTP API，你可以用代码调用，而不只是在命令行用。

默认情况下，Ollama 在 http://localhost:11434 提供 API 服务。

用 Python 调用 Ollama API：


## 实例

运行这个脚本：


## 实例

如果你想用更高级的封装，可以使用 Ollama 的官方 Python 库：


## 实例


### 与 Open WebUI 集成

命令行虽然方便，但图形界面更友好。

Open WebUI 是一个非常漂亮的 Web 界面，可以连接 Ollama，让你像用 ChatGPT 一样用本地模型。

安装 Open WebUI：


## 实例

安装完成后，在浏览器打开 http://localhost:3000，你就能看到一个和 ChatGPT 很像的界面了。

Ollama + Open WebUI 是目前最推荐的本地 AI 组合——安装简单、界面友好、功能强大，适合绝大多数用户。


## LM Studio：图形界面操作

如果你不喜欢命令行，LM Studio 是一个很好的选择——纯图形界面，下载模型、运行模型都在窗口里完成。


### 安装 LM Studio

LM Studio 支持 Windows、macOS、Linux。

从官网 https://lmstudio.ai 下载安装包，直接安装即可。


### 模型下载与管理

打开 LM Studio，左侧就是模型库。

你可以按模型名称搜索，比如搜 "llama"、"qwen"、"mistral"，找到想要的模型，点击下载。

LM Studio 会自动列出同一个模型的不同版本：

下载好的模型会出现在 "My Models" 列表里。


## 后续章节

- 本地 API 服务
- 实例
- 模型量化入门
- 什么是量化
- GGUF 格式详解
- Q4/Q8 量化的区别
- AWQ/GPTQ 量化方案
- 模型选择指南
- 7B/13B/70B 模型对比
- 中文支持较好的模型推荐
- 任务特定模型选择
- 实战：搭建完全离线的本地知识库
- 技术方案
- 用 Ollama + LangChain 实现
- 实例
- 实例

## 记忆卡片

- 一句话定义：`本地模型部署` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
