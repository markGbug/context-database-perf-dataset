# Ollama：Ollama Python 使用

- 来源：[Ollama Python 使用](https://www.runoob.com/ollama/ollama-python-sdk.html)
- 分类：AI / 智能开发
- 技术：Ollama
- 笔记类型：学习笔记
- 章节序号：0396

## 本章内容

Ollama 提供了 Python SDK，可以让我们能够在 Python 环境中与本地运行的模型进行交互。

通过 Ollama 的 Python SDK 能够轻松地将自然语言处理任务集成到 Python 项目中，执行各种操作，如文本生成、对话生成、模型管理等，且不需要手动调用命令行。


### 安装 Python SDK

首先，我们需要安装 Ollama 的 Python SDK。

可以使用 pip 安装：

```text
pip install ollama
```

确保你的环境中已安装了 Python 3.x，并且网络环境能够访问 Ollama 本地服务。


### 启动本地服务

在使用 Python SDK 之前，确保 Ollama 本地服务已经启动。

你可以使用命令行工具来启动它：

```text
ollama serve
```

启动本地服务后，Python SDK 会与本地服务进行通信，执行模型推理等任务。


### 使用 Ollama 的 Python SDK 进行推理

安装了 SDK 并启动了本地服务后，我们就可以通过 Python 代码与 Ollama 进行交互。

首先，从 ollama 库中导入 chat 和 ChatResponse：

```text
from ollama import chat
from ollama import ChatResponse
```

通过 Python SDK，你可以向指定的模型发送请求，生成文本或对话：


## 实例

执行以上代码，输出结果为：

```text
你好！我是 Qwen3.5，是通义千问系列中最新推出的大语言模型。我具备强大的语言理解与生成能力，能协助你完成多种任务！
```

llama SDK 还支持流式响应，我们可以在发送请求时通过设置 stream=True 来启用响应流式传输。


## 实例


## 自定义客户端

你还可以创建自定义客户端，来进一步控制请求配置，比如设置自定义的 headers 或指定本地服务的 URL。


### 创建自定义客户端

通过 Client，你可以自定义请求的设置（如请求头、URL 等），并发送请求。


## 实例


### 异步客户端

如果你希望异步执行请求，可以使用 AsyncClient 类，适用于需要并发的场景。


## 实例

步客户端支持与传统的同步请求一样的功能，唯一的区别是请求是异步执行的，可以提高性能，尤其是在高并发场景下。


### 异步流式响应

如果你需要异步地处理流式响应，可以通过将 stream=True 设置为异步生成器来实现。


## 实例

这里，响应将逐部分地异步返回，每部分都可以即时处理。


## 常用 API 方法

Ollama Python SDK 提供了一些常用的 API 方法，用于操作和管理模型。

1. chat 方法

与模型进行对话生成，发送用户消息并获取模型响应：

```text
ollama.chat(model='llama3.2', messages=[{'role': 'user', 'content': 'Why is the sky blue?'}])
```

2. generate 方法

用于文本生成任务。与 chat 方法类似，但是它只需要一个 prompt 参数：

```text
ollama.generate(model='llama3.2', prompt='Why is the sky blue?')
```

3. list 方法

列出所有可用的模型：

```text
ollama.list()
```

4. show 方法

显示指定模型的详细信息：

```text
ollama.show('llama3.2')
```

5. create 方法

从现有模型创建新的模型：

```text
ollama.create(model='example', from_='llama3.2', system="You are Mario from Super Mario Bros.")
```

6. copy 方法

复制模型到另一个位置：

```text
ollama.copy('llama3.2', 'user/llama3.2')
```

7. delete 方法

删除指定模型：

```text
ollama.delete('llama3.2')
```

8. pull 方法

从远程仓库拉取模型：

```text
ollama.pull('llama3.2')
```

9. push 方法

将本地模型推送到远程仓库：

```text
ollama.push('user/llama3.2')
```


## 错误处理

Ollama SDK 会在请求失败或响应流式传输出现问题时抛出错误。

我们可以使用 try-except 语句来捕获这些错误，并根据需要进行处理。


## 实例

在上述例子中，如果模型 does-not-yet-exist 不存在，抛出 ResponseError 错误，捕获后你可以选择拉取该模型或进行其他处理。


## 复习重点

- 能说明 `Ollama Python 使用` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
