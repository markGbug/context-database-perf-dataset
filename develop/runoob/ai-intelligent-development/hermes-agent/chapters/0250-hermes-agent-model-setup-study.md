# Hermes Agent：Hermes Agent 配置

- 来源：[Hermes Agent 模型配置](https://www.runoob.com/hermes-agent/hermes-agent-model-setup.html)
- 分类：AI / 智能开发
- 技术：Hermes Agent
- 笔记类型：学习笔记
- 章节序号：0250

## 本章内容

了解如何配置 Hermes Agent，包括配置文件、LLM 提供商设置、工具配置和所有可用的配置选项。


### 选择模型提供商

Hermes 支持 300+ 个模型和十余个提供商。

Nous Portal 是 Nous Research 自己的订阅网关，一次 OAuth 登录，涵盖模型调用 + 工具网关（网页搜索、图像生成、TTS、浏览器自动化）：

```text
hermes setup --portal
```

以上条命令会打开浏览器完成 OAuth 授权，设置 Nous 作为推理提供商，并同时开启所有工具网关。

完整设置向导（自带 API Key）:

```text
hermes setup
```

向导提供三种模式：


### 手动选择提供商

使用以下命令，查看可以选择的提供商：

```text
hermes model
```

上下按键选择，回车选中配置：

常用提供商配置方式：

原则：先让基础对话跑通，再逐步开启网关、定时任务、语音等高级功能。


## 使用 CC Switch 一键配置


## 复习重点

- 能说明 `Hermes Agent 模型配置` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
