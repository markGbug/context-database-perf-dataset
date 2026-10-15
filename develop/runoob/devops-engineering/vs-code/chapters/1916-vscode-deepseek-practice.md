# VS Code：VSCode 接入 DeepSeek

- 来源：[VSCode DeepSeek](https://www.runoob.com/vscode/vscode-deepseek.html)
- 分类：DevOps / 工程化
- 技术：VS Code
- 笔记类型：练习笔记
- 章节序号：1916

## 本章内容

VSCode 拥有一个庞大的扩展市场，用户可以根据自己的需要安装各种扩展来增强编辑器的功能，包括语言支持、代码格式化工具、版本控制集成、主题和图标等。

VS Code 可以通过扩展很好的接入我们想要大模型，常用的扩展可以参考：VS Code AI 扩展。

接下来我们来学习下如何在 VS Code 上通过 Roo Code 扩展装上最近很火的 DeepSeek。

本文以 Roo Code 为例演示如何接入 DeepSeek。

除了官方API接口外，我们也可以通过Coding Plan/Token Plan套餐直接接入DeepSeek、Kimi、GLM、Doubao、MiniMax等主流大模型，无需单独购买各家API。


### 安装 Roo Code 扩展

Roo Code（前身为 Roo Cline）是一款基于 VS Code 的 AI 编程助手插件，通过集成多种 AI 模型和强大的自动化功能，为开发者提供高效、智能的编程体验。

Roo Code 可与 OpenAI、DeepSeek、Anthropic、Google Gemini 等主流 API 无缝对接，还支持通过 Ollama 使用本地模型，开发者能根据需求和预算灵活切换。

Roo Code 提供了多种预设模式，包括 Code（代码模式）、Architect（架构模式）和 Ask（问答模式），并支持用户自定。例如，用户可以创建一个专注于编写测试用例的 QA 工程师角色。

扩展搜索关键词：Roo Code

插件链接地址：https://marketplace.visualstudio.com/items?itemName=RooVeterinaryInc.roo-cline

Github 地址：https://github.com/RooVetGit/Roo-Code


### 设置 API Key

安装扩展后在左侧活动栏会有个小火箭的图标，打开就可以看到支持的大模型，我们可以选择 DeepSeek：

填写我们申请的 API Key：

我们可以在 DeepSeek 官网 API 开放平台 https://platform.deepseek.com/usage 申请 API Key：

安装成功后，我们就可以点击扩展右上角的加号 +，开启对话窗口：

我们也可以选择文件中的一小段代码，让大模型帮我们解析或修正：

使用 @ 符号为 AI 提供上下文。输入 @ 即可查看文件夹中所有文件和代码符号的列表。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `VSCode DeepSeek` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
