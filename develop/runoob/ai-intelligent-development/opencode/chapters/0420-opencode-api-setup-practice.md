# OpenCode：OpenCode API 设置

- 来源：[OpenCode API 设置](https://www.runoob.com/opencode/opencode-api-setup.html)
- 分类：AI / 智能开发
- 技术：OpenCode
- 笔记类型：练习笔记
- 章节序号：0420

## 本章内容

通过 OpenCode，你可以接入任意 LLM（大语言模型）提供商，例如 OpenAI、Claude、DeepSeek、阿里百炼等，从而获得更强的 AI 编程能力。

如果你是第一次使用，建议优先选择 OpenCode Zen，它是 OpenCode 官方精选的一组模型，已经过测试和优化，开箱即用，适合新手。

OpenCode Zen 里面也包含了大量的免费大模型，所以基本上可以直接用，不用充钱。


### 步骤 1：启动配置

直接运行：

```text
opencode
```

如果出现 EACCES: permission denied, open '' 是权限问题，请使用管理员权限执行，比如：

```text
sudo opencode
```

你会看到终端界面（TUI）:

在 OpenCode 终端界面中输入：

```text
/connect
```

注：使用 /connect 命令添加提供商的 API 密钥后，凭据会存储在 ~/.local/share/opencode/auth.json 中。

然后选择：opencode

如果有其他的大模型 Key，你也可以通过这个列表选择配置。


### 步骤 2：获取 API Key

打开以下页面并登录： https://opencode.ai/auth

- 登录账号
- 添加账单信息
- 创建 API Key


### 步骤 3：粘贴 API Key

回到终端，将获取到的 API Key 粘贴进去：

完成后，即可开始使用 OpenCode。

我们可以按下 Ecs 退出配置 LLM 提供商，然后在对话窗口输入 /model 命令来查看支持的模型：

看到有 Free 字样的就是免费的模型：

选择完成后按下 Ecs 退出配置，就可以看到当前用的大模型：


### 国内 Coding Plan 套餐

现在市面上有很多大模型厂商， 国外的有 Anthropic、Open AI、Grok、Gemini等，但是访问国外现在不方便，国内的有 DeepSeek、千问、ZLM、Minimax 等。

我们使用Claude Code 写代码最费钱的就是 token 了，海外的访问不方便，而且还贵，国内的现在都有包月套餐，如果长期用建议买包月套餐划算。


## 接入阿里百炼

OpenCode 是开源的 AI 编程工具，可配合阿里云百炼提供的模型推理服务实现高效代码开发。

我们可以先使用阿里云主账号访问百炼模型服务平台 https://bailian.console.aliyun.com/，然后点击右上角登录，登录成功后点击右上角的齿轮⚙️图标，选择 API key，然后复制 API key，如果没有也可以创建 API key：

可以直接购买资源包，这样用起来更划算：https://cn.aliyun.com/benefit?from_alibabacloud=&userCode=i5mn5r7m


### 在 OpenCode 中设置

在输入框输入 /connect 并单击 Enter。

在 Connect a Provider 列表的搜索框中输入 alibaba 进行搜索，选中 Alibaba (China) 并单击 Enter。

输入我们申请的 API Key 后按 Enter：

然后我们可以输入 /model 查看阿里支持的模型，并选择需要的：

本文档仅适用于按量付费模式，Coding Plan 用户请使用专属 Base URL 和 API Key 接入，详情请参考 OpenCode Coding Plan 说明文档进行配置。


## 国内 API 配置

国内厂商 API 申请地址：

进入对应控制台后，注册/登录 → 完成实名认证 → 创建 API Key 即可开始调用。


### API 管理工具

平台一多，配置起来就麻烦，我们可以使用第三方工具 CC Switch 可以帮我们轻松管理这几个热门工具的 API 配置：https://github.com/farion1231/cc-switch/，Windows / macOS / Linux 全支持。

CC Switch 是一个 Claude Code / Codex / Gemini CLI 的全方位辅助工具。

CC Switch 可以帮我们轻松管理这几个热门工具的 API 配置，就好比给你的开发工具箱来了个智能整理助手，所有工具的配置都能在它这有序管理。

各平台安装包下载地址：https://github.com/farion1231/cc-switch/releases。

这里我们选择 OpenCode 图标，然后点击右上角的添加按钮：

默认有很多供应商，我这里选 DeepSeek 演示：

设置你获取的 API key：

设置模型 deepseek-v4-pro：

设置完后，我们就可以到终端测试下：

```text
sudo opencode run 解释一下 JavaScript 中闭包的原理
```

更多具体的操作设置参考文章：https://www.runoob.com/ai-agent/cc-switch.html


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `OpenCode API 设置` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
