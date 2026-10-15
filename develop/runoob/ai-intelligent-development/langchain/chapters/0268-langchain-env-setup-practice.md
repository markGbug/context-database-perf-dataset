# LangChain：LangChain 环境搭建

- 来源：[LangChain 环境搭建](https://www.runoob.com/langchain/langchain-env-setup.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：练习笔记
- 章节序号：0268

## 本章内容

本篇将带你完成 LangChain 的安装和配置，确保你能顺利运行第一个 LangChain 程序。


## 环境要求

检查 Python 版本：

```text
$ python --version
Python 3.12.7
```

如果你还没有安装 Python，可以参考我们的 Python3 环境搭建。

Python 包与环境管理工具参考： uv 入门教程。


## 安装 LangChain

LangChain 采用模块化设计，核心功能和第三方集成分开安装。


### 安装核心包

```text
$ pip install langchain
```

这个命令会安装 langchain 主包，它包含了 init_chat_model()、create_agent() 等核心 API，同时会自动安装 langchain-core 作为依赖。


### 安装模型提供商包

LangChain 本身不包含具体的模型实现，你需要根据使用的模型安装对应的提供商包：


### 一键安装

建议初学者直接安装以下组合：

```text
$ pip install langchain langchain-openai python-dotenv
```

python-dotenv 用于从 .env 文件加载 API Key，这是管理敏感信息的最佳实践，可以避免将 Key 硬编码在代码中。


## 配置 API Key


### 获取 API Key

以 OpenAI 为例，你需要先注册账号并获取 API Key：

- 访问 https://platform.openai.com 注册或登录
- 进入 API Keys 页面，点击 "Create new secret key"
- 复制生成的 Key（格式为 sk-xxxxxxxx）

API Key 只会显示一次，请立即保存到安全的地方。不要将 Key 提交到 Git 仓库或分享给他人。

其他提供商的获取方式类似，请参考对应文档。


### 设置环境变量

推荐使用 .env 文件管理 API Key。在项目根目录创建 .env 文件：


## 实例

然后创建 .gitignore 文件，确保 .env 不会被提交：

```text
# .gitignore
.env
__pycache__/
*.pyc
```


### 在代码中加载


## 实例


## 验证安装

运行以下脚本验证安装是否成功：


## 实例

运行结果：

```text
langchain 版本: 1.3.0
langchain-openai 已安装
API Key 配置成功: sk-proj-z...xxxx
模型回复: 菜鸟教程（RUNOOB）是一个面向编程初学者的中文技术学习平台。
```

如果最后一步报错，请检查：(1) API Key 是否正确；(2) 是否有网络代理影响连接；(3) 账户余额是否充足。

国内我们可以采用 DeepSeek 大模型来测试，如果还没有需要先去 https://platform.deepseek.com/api_keys 创建一个 API key。

DeepSeek 的 API 文档参考：https://api-docs.deepseek.com/zh-cn/。

如果你需要统一管理多个第三方模型，可以选择安装 LiteLLM 作为模型网关：

```text
pip install -U litellm
```

不过本文的示例直接使用 ChatOpenAI 配合 openai_api_base 参数连接 DeepSeek，无需额外安装 LiteLLM。


## 实例

执行以上代码，就会输出内容：

```text
你好！很高兴认识你！

我是DeepSeek，由深度求索公司创造的AI助手。我的特点包括：
。。。
```


## 项目目录建议

推荐的项目目录结构：

```text
langchain-learning/
├── .env                  # API Key 配置（不提交到 Git）
├── .gitignore            # Git 忽略规则
├── config.py             # 公共配置加载
├── 01_hello_world.py     # 第一篇的示例
├── 02_first_agent.py     # Agent 示例
└── ...                   # 更多练习
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `LangChain 环境搭建` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
