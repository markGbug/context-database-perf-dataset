# DeepSeek Harness：DeepSeek Harness 安装

- 来源：[DeepSeek Harness 安装](https://www.runoob.com/deepseek-harness/deepseek-harness-install.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：练习笔记
- 章节序号：0217

## 本章内容

本章节介绍三种安装方式：npm 一键安装、源码安装、Python SDK。


### 安装前准备

DeepSeek Harness 的运行时基于 Node.js，官方推荐的一键安装方式不需要任何额外依赖。

源码安装还需要 pnpm 与 Git。

Python SDK 方式需要 Python 3.10 及以上版本。

操作系统：Linux、macOS 或 Windows 均可

Python SDK 支持 Linux x64 / arm64 与 macOS 14+（arm64）。

先检查本机环境, 需要 Node.js，例如 v20+：

```text
node -v
```

源码安装时需要 git：

```text
git --version
```

安装方式：


## 方式一：npm 一键安装（推荐）

我们可以使用 npm 命令来全局安装：

```text
npm install -g @deepseek-ai/dsh
```

使用该方式安装后期方便使用 dsh 命令，安装完成后，输入以下命令即可启动：

```text
dsh web
```

也可以使用 npx 命令安装快速体验，在终端执行：

```text
npx @deepseek-ai/dsh web
```

命令会启动 Web UI，首次运行会自动初始化 web 配置模板，然后打印访问地址——默认是 http://127.0.0.1:3080。

验证是否成功：

1. 在浏览器打开终端打印的地址（默认 http://127.0.0.1:3080）；

2. 看到 DeepSeek Harness 的 Web 界面即安装成功；

3. 注意：新 Web UI 在添加工作区之前不会选中任何工作区——这是正常现象，下一步会配置。

小贴士：dsh 会把调用目录作为默认文件系统位置。建议先 cd 到你的项目目录，再执行 npx @deepseek-ai/dsh web，这样后续选择工作区时最方便。


## 方式二：从源码安装

适合开发插件、阅读源码或参与贡献，克隆仓库后按顺序执行：

```text
git clone https://github.com/deepseek-ai/deepseek-harness.git
cd deepseek-harness
pnpm install     # 安装依赖（需要 pnpm，可用 npm install -g pnpm 安装）
pnpm run build   # 构建包与前端产物（生产运行需要）
pnpm dsh web     # 以源码方式启动 Web UI
```

从源码运行时的其他入口：

pnpm dsh --profile headless "run the tests" —— 一次性运行一个任务并打印最终答案；

pnpm dsh --profile web --dump-config —— 查看实际启动的完整配置树（开发插件时很有用）。


## 方式三：Python SDK 安装

前置要求：Python 3.10+、Git、DeepSeek 兼容的 API 端点与凭据、一个 agent 可以修改的隔离 workspace。创建虚拟环境并安装：

```text
git clone https://github.com/deepseek-ai/deepseek-harness.git
cd deepseek-harness
python -m venv .venv
. .venv/bin/activate
python -m pip install deepseek-harness-sdk
```

设置凭据后即可在程序中调用（SDK 自带运行时，不需要系统提供 Node.js）：

```text
export DEEPSEEK_API_KEY=sk-your-key-here
# 如果模型不是默认 DeepSeek 端点，而是 OpenAI 兼容代理，还需要：
# export DEEPSEEK_BASE_URL=http://127.0.0.1:8000/v1
# export DSH_MODEL=deepseek-v4-flash
```

在自己的 Python 程序中使用：

from deepseek_harness import DeepSeekHarness —— 仓库内置的 examples/jsonrpc-agent/minimal.py 是 SDK 调用的轻量包装，可直接参考；运行后会打印 assistant 的最终回复，会话目录会收到包含模型请求与工具调用的 JSONL 日志。


## 首次配置与第一个任务

无论哪种方式启动的 Web UI，首次使用都只需三步：

第一个任务建议从轻量指令开始："Summarize this repository and identify its main packages."

先让 agent 熟悉工作区，再逐步交付真实任务。—— 官方快速入门指南建议


## 常用命令速查

关于 Profile：web 与 headless 两个 profile 会在首次使用时从内置模板自动初始化；其余 profile 需要通过 dsh plugin 创建。dsh 的启动参数在前，应用参数在后，例如 dsh --profile web --port 8080 中 --port 属于 Web 应用。


## 常见问题与排错

问题 1：浏览器打不开 http://127.0.0.1:3080

确认终端里 dsh 进程仍在运行且没有报错；若端口被占用，可以用 dsh --profile web --port 8080 换一个端口；检查防火墙是否放行本地端口。

问题 2：npx 找不到 @deepseek-ai/dsh 或版本过旧

先确认 Node.js 已安装且版本较新（node -v）；项目处于开发者预览阶段、迭代很快，必要时清空 npx 缓存后重试，或改用源码安装。

问题 3：源码安装时 pnpm install / build 失败

确认已安装 pnpm（npm install -g pnpm）；网络受限时可为 npm/pnpm 配置镜像源；构建要求 Node.js 版本满足仓库 package.json 的 engines 声明。

问题 4：会话输入框不可用 / agent 无法读写文件

最常见原因是没有选择工作区——回到「选择工作区」添加并选中项目目录；确认已在「设置 → 模型」中保存有效的 API 密钥，模型路由无需重启即可生效。

问题 5：Python SDK 运行时找不到 Node.js

SDK 自带运行时、正常情况下不需要系统 Node.js；如果报运行时缺失，请确认安装的是与 SDK 同版本的完整包（python -m pip install deepseek-harness-sdk），并按官方前置要求使用 Linux x64 / arm64 或 macOS 14+（arm64）。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DeepSeek Harness 安装` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
