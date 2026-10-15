# DeepSeek Harness：DeepSeek Harness 第一次使用

- 来源：[DeepSeek Harness 使用](https://www.runoob.com/deepseek-harness/deepseek-harness-start.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：练习笔记
- 章节序号：0218

## 本章内容

上一节我们介绍了 DeepSeek Harness 安装，一键安装命令：

```text
npm install -g @deepseek-ai/dsh     # 后期方便使用 dsh 命令
```

或：

```text
npx @deepseek-ai/dsh web
```

注意，安装前先确保已经安装了 Node.js:

```text
node -v
```

输出版本号类似 v22.23.1，说明安装成功～

目前在内测，打开 http://127.0.0.1:3080/ 会看到内测声明，点击继续就好了：

整个界面如下，我们可以先点击设置配置 API key（申请地址：https://platform.deepseek.com/api_keys）：

创建一个目录 DeepSeekProjects 作为工作区：

```text
mkdir DeepSeekProjects
```

DeepSeek Harness 提供四种运行模式：标准模式、PTC模式、极简模式、创造模式。

- 标准模式：新手首选，内置完整代码 Agent 能力，文件操作、Shell、检索、任务规划、子 Agent 等插件预装，开箱即用。
- PTC 模式：能力同标准模式。支持用 TypeScript 批量编排工具调用，合并多轮交互，减少对话次数、节约 Token。依赖较强代码规划能力，调试难度更高；建议大量重复调用场景再切换。
- 极简模式：仅保留持久 Bash 与文件编辑器，移除附加功能。用于模型基准性能测试，不适合日常开发。
- 创造模式：具备标准模式全部能力，可探查 Cordis 运行环境，在线调试插件、创建新 Agent，实现功能自主扩展。

我们选定模式，点击新会话，输入需求即可开启对话：

使用过程还会帮我们分析需求：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DeepSeek Harness 使用` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
