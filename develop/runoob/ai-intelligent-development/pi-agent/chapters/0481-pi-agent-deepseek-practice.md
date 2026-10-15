# Pi Agent：Pi Agent 接入 DeepSeek

- 来源：[Pi Agent DeepSeek](https://www.runoob.com/pi-agent/pi-agent-deepseek.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：练习笔记
- 章节序号：0481

## 本章内容

DeepSeek 提供 OpenAI 兼容接口，可以复用 Pi 现成的 OpenAI 适配层，无需为 DeepSeek 单独开发适配器。

接入的核心工作只有两件：在 models.json 中声明供应商与模型参数，通过环境变量提供 API Key。

整体架构如下图所示：

所谓「OpenAI 兼容接口」，指供应商的 HTTP 接口协议与 OpenAI 保持一致。只要协议兼容，任何支持 OpenAI 的工具都可以直接调用，DeepSeek 就属于这一类。


## 安装 Pi

Pi 依赖 Node.js 运行环境，安装前请先确认 Node.js 已就绪。


### 安装 Node.js

从 Node.js 官网下载对应系统的安装包，使用默认选项安装即可。


### 安装 Pi CLI

在终端通过 npm 全局安装：

```text
npm install -g --ignore-scripts @earendil-works/pi-coding-agent
```

Linux 和 macOS 用户也可以使用官方安装脚本一键安装：

```text
curl -fsSL https://pi.dev/install.sh | sh
```


### 验证安装

执行以下命令，能正常打印出版本号即表示安装成功：

```text
pi --version
```

输出类似：

```text
0.83.0
```


## 配置 DeepSeek 供应商

Pi 通过 models.json 定义自定义模型供应商，本节把 DeepSeek 以 OpenAI 兼容接口的形式接入。


### 配置文件路径

不同操作系统的配置路径不同，请按系统对号入座：


### 编写 models.json

把以下内容写入配置文件：

```text
{
  "providers": {
    "deepseek": {
      "baseUrl": "https://api.deepseek.com",
      "api": "openai-completions",
      "apiKey": "$DEEPSEEK_API_KEY",
      "models": [
        {
          "id": "deepseek-v4-pro",
          "name": "DeepSeek V4 Pro",
          "contextWindow": 1000000,
          "maxTokens": 384000,
          "input": ["text"],
          "reasoning": true,
          "cost": {
            "input": 1.74,
            "output": 3.48,
            "cacheRead": 0.145,
            "cacheWrite": 0
          },
          "compat": {
            "requiresReasoningContentOnAssistantMessages": true,
            "thinkingFormat": "deepseek",
            "reasoningEffortMap": {
              "minimal": "high",
              "low": "high",
              "medium": "high",
              "high": "high",
              "xhigh": "max"
            }
          }
        },
        {
          "id": "deepseek-v4-flash",
          "name": "DeepSeek V4 Flash",
          "contextWindow": 1000000,
          "maxTokens": 384000,
          "input": ["text"],
          "reasoning": true,
          "cost": {
            "input": 0.14,
            "output": 0.28,
            "cacheRead": 0.028,
            "cacheWrite": 0
          },
          "compat": {
            "requiresReasoningContentOnAssistantMessages": true,
            "thinkingFormat": "deepseek",
            "reasoningEffortMap": {
              "minimal": "high",
              "low": "high",
              "medium": "high",
              "high": "high",
              "xhigh": "max"
            }
          }
        }
      ]
    }
  }
}
```


### 配置项解析

下面对 models.json 中用到的主要字段逐一说明：

reasoningEffortMap 把 Pi 的五个推理档位（minimal / low / medium / high / xhigh）映射到 DeepSeek 支持的档位，除 xhigh 映射为 max 外，其余全部收敛到 high。


### 模型选择

配置声明了两个 DeepSeek 模型，主要区别如下：

单价单位为每百万 tokens（美元）。


### 获取并设置 API Key

先在 DeepSeek 开放平台申请 API Key：https://platform.deepseek.com/api_keys。

Linux / macOS 在终端导出环境变量：

```text
export DEEPSEEK_API_KEY="你的 DeepSeek API Key"
```

Windows（PowerShell）设置方式：

```text
$env:DEEPSEEK_API_KEY="你的 DeepSeek API Key"
```

建议把导出命令写入 shell 配置（如 ~/.bashrc、~/.zshrc 或 PowerShell Profile），避免每次开新终端都重新设置。

请把示例中的「你的 DeepSeek API Key」替换为真实密钥。API Key 属于敏感信息，请妥善保管，切勿提交到版本库。


## 运行与测试

配置完成后，就可以启动 Pi 并切换到 DeepSeek 模型。


### 启动 Pi

进入项目目录:

```text
cd ~/runoob-test/
```

直接执行 pi 命令：

```text
pi
```


### 切换到 DeepSeek 模型

进入交互界面后，按以下步骤切换：

- 输入 /model 打开模型选择器。
- 选择 deepseek 供应商，选择 DeepSeek-V4-Pro 或 DeepSeek-V4-Flash。
- 接下来询问当前模型

切换完成后，就可以直接在这个极简终端框架里开始编码了。


### 建议的测试步骤

按下面的清单逐项验证接入是否完整可用：

其中「多轮工具调用」是验证 requiresReasoningContentOnAssistantMessages 配置是否正确的关键场景。


## 常见问题排查

接入过程中遇到问题，可对照下面的清单快速定位。


### 模型选择器里看不到 DeepSeek

检查 models.json 路径是否正确，Windows 与 Linux / macOS 的路径不同。

同时确认 JSON 格式没有语法错误，比如多余的逗号、未闭合的引号。


### 鉴权失败

确认 DEEPSEEK_API_KEY 环境变量已经正确设置。

注意：执行 pi 命令的终端会话，必须与设置环境变量的会话是同一个。


### 多轮工具调用报错

优先检查 requiresReasoningContentOnAssistantMessages 与 thinkingFormat 是否已按上文配置齐全。


### 需要更多自定义能力

可以参考 Pi 官方 models 文档，了解更完整的配置项。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pi Agent DeepSeek` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
