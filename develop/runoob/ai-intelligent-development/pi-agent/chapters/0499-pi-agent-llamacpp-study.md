# Pi Agent：Pi Agent 与 llama.cpp 本地模型

- 来源：[Pi Agent 与 llama.cpp 本地模型](https://www.runoob.com/pi-agent/pi-agent-llamacpp.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：学习笔记
- 章节序号：0499

## 本章内容

Pi Agent 内置了对 llama.cpp 的支持，让你可以在本地运行开源大模型，无需云端 API。


## 什么是 llama.cpp

llama.cpp 是一个高性能的 LLM 推理引擎，可以在消费级硬件上运行开源大语言模型。

它支持 CPU 推理（通过量化技术大幅降低内存需求）和 GPU 加速（CUDA、Metal、Vulkan 等）。

Pi Agent 通过 llama.cpp 路由器服务器 与本地模型通信。


## 配置 llama.cpp

配置分三步：先启动 llama-server 路由器，再注册 llama.cpp 提供商，最后加载并选择模型。


### 启动 llama-server 路由器

不带 -m 或 --model 参数启动 llama-server，就会进入路由器模式。

一旦传了模型参数，llama-server 会进入单模型模式，不再扫描模型目录。

路由器会按需加载或卸载 --models-dir 目录下的 GGUF 模型，常用参数有 --models-dir（模型目录）、--no-models-autoload（关闭自动加载）、--jinja（启用对话模板与工具调用支持）、-ngl（卸载到 GPU 的层数）和 -c 32768（每个模型的上下文窗口）。

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

启动后可以用 /health 与 /models 两个接口自检路由器是否可达、模型是否被发现。


### 登录 llama.cpp

在 Pi Agent 交互模式中：

```text
/login llama.cpp
```

此步仅注册本地提供商，无需账号鉴权，但需要填写路由器地址（默认 http://127.0.0.1:8080）。

执行后 Pi 会要求填写路由器 URL 与可选的 API Key，本地服务通常把 API Key 留空即可。


### 管理本地模型

使用 /llama 命令打开模型管理菜单：

```text
/llama
```

在菜单中选中一个未加载的模型并回车，就会把它加载进内存。

选中一个已加载的模型并回车，则会把它卸载。

选择菜单项 Download model... 可以搜索 Hugging Face 并下载新模型，加载或下载过程中按 Escape 可确认取消。

菜单始终显示路由器当前的真实状态，而只有已加载的模型才会出现在 /model 选择器里。


### 切换到本地模型

使用 /model 命令选择已加载的本地模型。

快捷键方面，Ctrl+L 打开模型选择器，Ctrl+P 在模型间循环切换。


## 推荐的开源模型

以下是一些适合本地运行的开源编码模型：

本地模型的编码能力通常弱于云端顶级模型（如 Claude Sonnet、GPT-4o），但在网络受限、数据敏感性要求高或需要频繁使用的场景下是非常好的替代方案。


## 模型存储

模型目录由 llama-server 启动参数 --models-dir 决定（如 ~/models），模型下载也由 llama.cpp 服务端执行。

模型文件通常较大（几 GB 到几十 GB），请确保该目录有足够的磁盘空间。


## 自定义 llama.cpp 服务器

如果你的 llama.cpp 服务器运行在非默认端口或远程机器上，有两种接入方式。

零代码方式是设置环境变量 LLAMA_BASE_URL 与 LLAMA_API_KEY 指向自定义 llama.cpp 服务器，无需写扩展，也不用 /login。

```text
export LLAMA_BASE_URL=http://192.168.1.20:8080
export LLAMA_API_KEY=optional-secret
pi
```

若服务器启用了 API Key，llama-server 启动时要带上相同的 --api-key 值，并保留 --host 127.0.0.1 以限制本机访问。

只需接入 OpenAI 兼容 API 时，models.json 方式更简单，见《接入 DeepSeek》一章；需要完整控制请求流程时才用扩展方式。

在扩展中注册 llama.cpp 提供商：


## 实例

这个动态发现模式让 Pi Agent 能实时获取 llama.cpp 服务器上当前已加载的模型列表。

把文件保存到 ~/.pi/agent/extensions/ 目录并重启 Pi Agent，扩展会自动加载并注册这个提供商。

生效后打开 /model 选择器，就能看到 llama.cpp 服务器上当前已加载的模型并直接对话。


## 本地模型的局限性

使用本地模型时需要注意以下几点：

- 工具调用能力：部分开源模型的工具调用（tool calling）能力较弱，可能无法正确使用 Pi Agent 的内置工具
- 推理速度：在没有 GPU 加速的情况下，推理速度可能较慢
- 上下文长度：本地模型的有效上下文窗口通常小于云端模型
- 推理等级：非推理型模型始终以 off 运行，无法使用推理等级功能

工具调用能力弱时，最常见的表现是模型把工具调用当成文字输出，而不是真正触发工具。

```javascript
> 查看 src/index.ts 的内容

好的，下面是 src/index.ts 的内容：
import { createAgent } from "pi";
export const agent = createAgent();
...
```

消息区域没有出现工具调用卡片，说明模型并没有真正调用 read 工具，而是在自己编造文件内容。

遇到这种情况可以换用工具调用支持更好的模型，或者把任务拆成更小的步骤。

推荐的混合策略：在需要深度推理和复杂编码时使用云端模型（如 Claude Sonnet），在日常简单任务或网络受限时切换到本地模型。

使用 Ctrl+P 可以快速在两个模型间切换。


## 复习重点

- 能说明 `Pi Agent 与 llama.cpp 本地模型` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
