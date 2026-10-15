# Python：Python OpenAI

- 来源：[Python OpenAI](https://www.runoob.com/python3/python-openai.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4145

## 本章内容

openai 是一个强大的 Python 库，用于与 OpenAI 的一系列模型和服务进行交互。

openai 封装了所有 RESTful API 调用，让开发者能轻松地在自己的 Python 应用中集成强大的 AI 能力，例如自然语言处理、图像生成和语音识别等。

主要功能：

- 文本生成：使用 GPT-4 或 GPT-5 等模型生成文章、代码、摘要、对话等。
- 图像生成：通过 DALL-E 模型根据文本描述创建图像。
- 嵌入（Embeddings）：将文本转换成向量表示，常用于语义搜索、文本分类和聚类等任务。
- 语音转文本：使用 Whisper 模型将音频文件转录成文本。
- 微调（Fine-tuning）：通过提供自己的数据集来训练一个更具针对性的模型。
- 助手（Assistants）API：构建能够理解上下文、调用工具并进行长期交互的复杂应用。

openai 开源地址：https://github.com/openai/openai-python


## 如何使用？

环境要求：

- Python 版本：3.9 及以上。
- 依赖库：httpx（默认）、aiohttp（可选）、websockets（Realtime API 需）。

首先，你需要用 pip 安装 openai 库：

```text
pip install openai

或

pip3 install openai
```

然后需要去 OpenAI 官网 https://platform.openai.com/ 注册账号，并在 API 密钥页面生成一个 API Key。

查看安装版本:

```text
import openai
print(openai.__version__)  # 输出当前 SDK 版本
```


## 实例

参数说明：


## 第三方模型

我们国内目前访问 openai 还是有点麻烦，国内很多也支持 openai，比如 DeepSeek、千问、GLM。


### DeepSeek

DeepSeek API 完全兼容 OpenAI 的 API 格式，只需修改少量配置，即可直接使用 OpenAI SDK 或兼容工具访问 DeepSeek API。

必填，要设置的模型：

- deepseek-v4-flash：对应 DeepSeek 的非思考模式，响应速度快，适合常规问答。
- deepseek-v4-pro：对应 DeepSeek 的思考模式，推理能力更强，适合复杂问题求解。


## 实例


## 使用方式

接下来我们使用 OpenAI SDK 访问百炼服务上的通义千问模型。


### 非流式调用示例


## 实例

运行代码可以获得以下结果：

```text
我是通义千问，阿里巴巴集团旗下的通义实验室自主研发的超大规模语言模型。我可以帮助你回答问题、创作文字，比如写故事、写公文、写邮件、写剧本、逻辑推理、编程等等，还能表达观点，玩游戏等。如果你有任何问题或需要帮助，欢迎随时告诉我！
```


### 流式调用示例


## 实例

运行代码可以获得以下结果：

```text
我是通义千问，阿里巴巴集团旗下的通义实验室自主研发的超大规模语言模型。我可以帮助你回答问题、创作文字，比如写故事、写公文、写邮件、写剧本、逻辑推理、编程等等，还能表达观点，玩游戏等。如果你有任何问题或需要帮助，欢迎随时告诉我！
```


## 特色功能


### 视觉（Vision）功能

支持图片输入（URL 或 Base64 编码），实现多模态交互。

图片 URL 输入:


## 实例

Base64 编码图片输入:


## 实例


### 异步使用（Async usage）

替换 OpenAI 为 AsyncOpenAI，并通过 await 调用 API：

基础异步示例:


## 实例

异步场景优化（aiohttp 后端），安装扩展版本：

```text
pip install openai[aiohttp]
```

aiohttp 后端优化:


## 实例


### 流式响应（Streaming responses）

基于 Server Side Events (SSE) 实时获取响应，同步 / 异步接口一致。

同步流式示例:


## 实例

异步流式示例:


## 实例


### 实时 API（Realtime API）

低延迟多模态对话（文本 / 音频），基于 WebSocket 实现，依赖 websockets 库。

基础文本示例:


## 实例

实时 API 错误处理:


## 实例


## 参考手册

以下表格包含的内容为：

- 核心初始化：同步用 OpenAI、异步用 AsyncOpenAI、Azure 用 AzureOpenAI，推荐通过环境变量配置 API Key。
- 文本生成：新版优先用 responses.create()，经典场景用 chat.completions.create()，流式输出需设置 stream=True。
- 高级能力：支持多模态（图片输入）、实时 API、文件上传/微调，错误处理需捕获 APIError 子类，超时/重试可灵活配置。


## 后续章节

- 安装与导入
- 创建客户端
- 文本生成（Responses API）
- 多轮对话
- 结构化输出（JSON Schema）
- 工具调用（Function Calling）
- 流式输出（Streaming）
- 异步调用（AsyncOpenAI）
- 实时 API（Realtime）
- 图像生成
- 嵌入生成（Embeddings）
- 音频转文本（Speech to Text）
- 文本转语音（Text to Speech）
- 文件管理（Files API）
- 模型微调（Fine-tuning Jobs）
- Webhook 验证

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python OpenAI` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
