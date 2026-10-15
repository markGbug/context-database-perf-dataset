# Codex：Codex 高级配置

- 来源：[Codex 高级配置](https://www.runoob.com/codex/codex-config-advanced.html)
- 分类：AI / 智能开发
- 技术：Codex
- 笔记类型：练习笔记
- 章节序号：0185

## 本章内容

Codex CLI 的高级配置层让我们可以精细控制模型提供商、沙箱权限、Hooks 钩子、遥测数据与终端行为。

如果你是第一次接触 Codex，先阅读 Config basics（配置基础）建立整体认知；本文默认你已了解 ~/.codex/config.toml 的存在与作用。


## 配置层级全景

Codex 的配置由多层叠加而成，理解这一点是后续所有高级用法的基石。

从底层到顶层依次是：系统层 → 用户层（~/.codex/config.toml） → Profile 层 → 项目层（.codex/config.toml） → CLI 命令行参数。

上层会覆盖下层同名配置，离当前工作目录最近的项目配置优先级最高。

判断当前生效配置最稳妥的方式是 codex --help 配合日志，或者显式使用 codex exec "show my current config" 让模型帮你解读。


## Profiles 命名配置层

Profile 是 Codex 推荐的"场景化切换"方案：把一组配置另存为 TOML 文件，按需通过 --profile 加载。

Profile 文件位于 ~/.codex/<name>.config.toml，其中 <name> 只能包含字母、数字、连字符、下划线。


### 创建并使用一个 Profile

假设你经常进行深度代码审查，希望使用更强的推理能力：


## 实例

使用 Profile 启动 Codex：


## 实例


### Profile 的合并语义

Profile 文件不是完整配置，它是在用户级 ~/.codex/config.toml 之上的一层增量覆盖。

这意味着 Profile 里只需要写"和默认配置不同"的字段，其它字段会自动继承用户级设置。

如果用户级和 Profile 同时设置 model_catalog_json，Profile 的值会优先生效。

从 Codex 0.134.0 开始，--profile 不再读取 config.toml 里的 [profiles.<name>] 表，也不再支持顶层的 profile = "name" 选择器。所有历史 Profile 设置必须迁移到独立的 ~/.codex/<name>.config.toml 文件。


### 从旧配置迁移到 Profile

如果你之前的 config.toml 长这样：


## 实例

需要拆分为两个文件：

```text
# 文件路径：~/.codex/config.toml（保留非 profile 部分）
# 注意：删除了 profile = "deep-review" 选择器
```

```text
# 文件路径：~/.codex/deep-review.config.toml
model = "gpt-5.5"
model_reasoning_effort = "xhigh"
```

迁移完成后，原来的 codex --profile deep-review 命令行用法保持不变。


## 命令行一次性覆盖

有时你只想临时改一两个字段跑一次任务，不想污染配置文件。这时可以用 CLI 覆盖：


### 优先使用专用标志

如果官方提供了专用参数（如 --model），优先用专用标志，可读性最好：


## 实例


### 使用 --config 覆盖任意键

对于没有专用标志的字段，用 -c 或 --config 覆盖。值是 TOML 格式，不是 JSON。


## 实例

几条易踩坑的规则：

- 使用点号语法定位嵌套字段，例如 mcp_servers.context7.enabled=false
- --config 的值会被当作 TOML 解析，含空格的字符串务必加引号
- 解析失败时，Codex 会把整个值当成字符串处理

判断一次覆盖是否生效，最快的办法是在命令后跟一个简单问题："what model are you using?"，让 Codex 主动报告当前配置。


## 配置文件与状态位置

Codex 把所有本地状态都放在 CODEX_HOME 目录下，默认是 ~/.codex。

常见文件与含义：


### 只想换 OpenAI 基础 URL？

很多同学用 LLM 代理、路由器或数据驻留项目，只需要修改 openai 内置提供商的 base URL。

此时直接设置 openai_base_url，不要新建 [model_providers.openai]，因为内置 ID 不可覆盖：


## 实例


## 项目级配置 .codex/config.toml

项目级配置放在仓库根的 .codex/config.toml，用于团队共享默认值。

Codex 会从工作目录向上逐级查找，离当前工作目录最近的文件优先级最高。


### 项目级配置的边界

出于安全考虑，只有项目被标记为"已信任"时才会加载项目级 .codex/ 层（包括 config.toml、本地 hooks、本地 rules）。

未受信任的项目中，下表里的敏感键会被忽略并打印启动警告：

这些键必须放在用户级 ~/.codex/config.toml 中。

相对路径（如 model_instructions_file）相对于其 .codex/ 所在目录解析。

如果项目未受信任而你设置了 model_provider = "proxy"，启动时 Codex 会打印警告并使用默认 provider；这是安全设计，不是 bug。


## Hooks 生命周期钩子

Hooks 让你在工具调用、回合开始等关键节点插入自定义脚本，适合做审计、敏感词过滤、commit 检查等。

Hooks 配置支持两种形式，且事件结构完全相同：

四个最常用的加载位置：

- ~/.codex/hooks.json
- ~/.codex/config.toml
- <repo>/.codex/hooks.json
- <repo>/.codex/config.toml

项目级 hooks 仅在项目受信任时加载，用户级 hooks 始终独立加载。


### 内联 TOML Hook 示例

下面是一个在 Bash 工具调用前执行的预检钩子：


## 实例

如果同一层既存在 hooks.json 又存在内联 [hooks] 表，Codex 会同时加载两者并打印警告。建议每层只选一种形式，避免维护成本翻倍。


## 自定义模型提供商

当你需要让 Codex 接入 LLM 代理、Ollama、Mistral、Azure 等非 OpenAI 官方端点时，model_providers 是入口。

内置 provider ID（openai、ollama、lmstudio）不能复用，否则会冲突。


### 基本定义


## 实例


## 后续章节

- 添加 HTTP 头
- 实例
- 命令式认证（Command-backed Auth）
- 实例
- Amazon Bedrock 内置提供商
- 实例
- OSS 本地模式
- 实例
- 实例
- Azure 提供商与微调
- 实例
- ChatGPT 数据驻留项目
- 实例
- 模型推理、详细度与上下文
- 实例
- 审批策略与沙箱模式

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Codex 高级配置` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
