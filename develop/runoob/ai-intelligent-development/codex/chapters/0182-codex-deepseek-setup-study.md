# Codex：Codex Deepseek 配置 -- 通过 CC Switch 中转

- 来源：[Codex DeepSeek (CCSwitch)](https://www.runoob.com/codex/codex-deepseek-setup.html)
- 分类：AI / 智能开发
- 技术：Codex
- 笔记类型：学习笔记
- 章节序号：0182

## 本章内容

本文介绍如何通过 CC Switch，让 Codex 能够使用第三方模型，比如 DeepSeek、Qwen、ZLM 等模型。

CC Switch 是一款免费开源的跨平台桌面工具，可以让你在 Codex 等 AI 编程助手中一键切换第三方 API 提供商，从而以更低的成本使用 AI 编程能力。

本文基于 CC Switch v3.16.0（最好安装最新版本），介绍如何为 Codex 配置 DeepSeek 作为后端 API，其他模型也可以参考这个配置。

除了官方API接口外，我们也可以通过Coding Plan/Token Plan套餐直接接入DeepSeek、Kimi、GLM、Doubao、MiniMax等主流大模型，无需单独购买各家API。


### 工作原理

CC Switch 在你的本机启动一个代理服务，把 Codex 发出的请求透明地转发到你指定的后端（比如 DeepSeek），然后把响应再回传给 Codex。

整个转发过程完全透明，对于 Codex 来说，它仍然认为自己正在访问 OpenAI 官方接口，而实际上，请求已经被 CC Switch 转发到了你指定的第三方模型服务。


### 前置条件

在开始配置之前，请确保你已满足以下条件：


## 第一步：安装 CC Switch

安装包下载地址为 https://github.com/farion1231/cc-switch/releases/latest，拉到页面底部，可以看到各个平台的下载链接：

根据你的操作系统选择对应的安装方式。


### macOS（推荐）

macOS 版本已通过公证，可直接使用 Homebrew 安装：

```text
# 使用 Homebrew 安装 CC Switch（已公证版本）
brew install --cask cc-switch
```


### Windows

从 GitHub Releases 下载 .msi 安装包，双击运行即可。


### Linux（Ubuntu/Debian）

```text
# 安装 CC Switch deb 包
sudo dpkg -i CC-Switch-*.deb
```

安装完成后启动 CC Switch，主界面会出现在桌面或系统托盘。

更多 CC Switch内容参考：https://www.runoob.com/ai-agent/cc-switch.html


## 第二步：添加 DeepSeek 提供商

在 CC Switch 中添加 DeepSeek 作为 API 提供商，让 Codex 的请求可以转发到 DeepSeek。

操作步骤如下：

- 打开 CC Switch，在顶部应用切换栏选择 Codex。
- 点击左侧「Providers」区域的 + Add Provider。
- 在预设列表中搜索 DeepSeek，选择对应的预设（v3.16.0 已内置 DeepSeek V4 flash 和 pro 两个版本）。
- 选中后，在下面的的表单中填入你的 DeepSeek API Key，其余字段使用默认值即可。
- 记得开启本地路由映射，然后点击 保存。


### 开启路由

切换到 DeepSeek，系统会提示我们开启路由，我们可以点击左上角的设置按钮进入设置页面开启：

点击路由设置菜单，开启路由：

然后选择 Codex：

接下来你重新打开 Codex，就可以看到 DeepSeek 的模型标志了：


## 选择模型：flash 还是 pro？

DeepSeek V4 提供两个版本，适用场景不同。选择合适的模型可以在成本和能力之间取得平衡。

在 CC Switch 的提供商编辑界面，可以随时修改使用的模型，修改后立即生效，无需重启 Codex。


## 常见问题


### 切换提供商后 Codex 报连接错误

确认 CC Switch 的 Local Routing 处于运行状态（绿色图标）。

如果刚安装，可能需要重启终端让环境变量生效。


### 想恢复使用官方 OpenAI 端点

在 CC Switch 中关闭 Local Routing 接管，或切换到官方 OpenAI 提供商，Codex 会自动使用原始配置。


### CC Switch 会记录我的 API Key 吗

CC Switch 是本地应用，所有配置存储在本机。API Key 不会上传到任何服务器。


## 更多资源


## 复习重点

- 能说明 `Codex DeepSeek (CCSwitch)` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
