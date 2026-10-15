# Hermes Agent：Hermes Agent 配置文件

- 来源：[Hermes Agent 配置文件](https://www.runoob.com/hermes-agent/hermes-agent-setup-file.html)
- 分类：AI / 智能开发
- 技术：Hermes Agent
- 笔记类型：学习笔记
- 章节序号：0249

## 本章内容

安装完成后，所有配置和数据都保存在 ~/.hermes/ 下：

```text
~/.hermes/
├── config.yaml      # 主配置文件（模型、工具、终端后端等）
├── .env             # API 密钥和 Secret（不提交到版本库）
├── auth.json        # OAuth 凭据（Nous Portal 等）
├── SOUL.md          # Agent 人格设定文件
├── memories/        # 持久记忆（MEMORY.md、USER.md）
├── skills/          # 技能文件（Agent 自动创建和管理）
├── cron/            # 定时任务配置
├── sessions/        # 网关会话记录
└── logs/            # 日志（API 密钥自动脱敏）
```

重要原则：

- Secrets（API 密钥、Token、密码） → 存入 .env
- 普通配置（模型、工具、终端后端等） → 存入 config.yaml
- 使用 hermes config set KEY VALUE 命令会自动路由到正确的文件


## 选择模型提供商

运行以下命令进入交互式选择：

```text
hermes model
```


### 推荐路径：Nous Portal（最省事）

一个订阅覆盖 300+ 模型 + Tool Gateway（网页搜索、图片生成、TTS、云端浏览器），无需分别申请多个 API Key：

```text
hermes setup
```

执行后通过 OAuth 登录，自动完成提供商配置和工具网关的开启。


### 常用提供商一览

模型上下文窗口要求：Hermes 要求模型至少支持 64,000 tokens 的上下文。使用本地模型时，确保启动参数中设置了足够的上下文大小（如 --ctx-size 65536）。


### 切换提供商

随时可以切换，无需修改任何代码：

```text
hermes model
```


## 三种 Setup 模式

首次运行 hermes setup 时，会提示选择初始化模式：


### 模式一：Quick Setup（Nous Portal）

免费 OAuth 登录，自动配置模型 + Tool Gateway（网页搜索、图片生成、TTS、浏览器）。推荐新用户使用。


### 模式二：Full Setup

手动逐项配置提供商、工具集、消息平台等。适合有明确需求、自带 API Key 的用户。


### 模式三：Blank Slate（空白起点）

只保留最小运行集（提供商、文件工具、终端工具），其余一切关闭。适合需要精确控制 Agent 能力边界的高级用户。空白模式会显式写入配置，防止 hermes update 后自动开启新功能。


## 开启第一次对话

配置完成后，启动 Hermes：

```text
hermes          # 经典 CLI 模式
hermes --tui    # 现代 TUI 模式（推荐，支持鼠标、弹窗等）
```

启动后会显示欢迎横幅，包含当前模型、可用工具和已加载技能的信息。


### 验证一切正常

用一个简单但具体的提示词测试：

```text
检查我当前目录，告诉我里面有哪些文件，并识别主要的项目入口文件。
```

成功标志：

- 横幅正确显示你选择的模型/提供商
- Agent 正常响应，无报错信息
- 需要时能调用工具（终端、文件读取等）
- 对话可以持续超过一轮


### 验证会话恢复

确认跨会话连续性正常工作：

```text
检查我当前目录，告诉我里面有哪些文件，并识别主要的项目入口文件。
```


## TUI 界面基本操作

运行 hermes --tui 进入现代 TUI 模式后，常用操作：


### 核心斜杠命令


## 终端执行后端配置

Hermes 支持六种终端执行环境，决定 Agent 的 Shell 命令在哪里运行：


### 切换到 Docker 后端（推荐用于生产）

```text
hermes config set terminal.backend docker
```

或直接编辑 ~/.hermes/config.yaml：

```text
terminal:
  backend: docker
  docker_image: "nikolaik/python-nodejs:python3.11-nodejs20"
```

安全说明：默认的 local 后端让 Agent 拥有和你相同的文件系统权限。如果你希望限制 Agent 的操作范围，切换到 docker 后端是最简单有效的方式。


## 工具集管理

Hermes 将 70+ 内置工具分组为 28 个工具集，可以按需启用或关闭：

```text
hermes tools    # 打开可视化工具集管理界面（curses UI）
```


### 主要工具集

关闭某个工具集：该工具集从系统提示词中完全消失，不只是禁用——这样可以节省 Token，并防止 Agent 误用不该用的工具。


## 配置管理常用命令

```text
# 查看当前完整配置
hermes config

# 用编辑器打开 config.yaml
hermes config edit

# 设置单个配置值（自动路由到正确文件）
hermes config set model anthropic/claude-sonnet-4-6
hermes config set terminal.backend docker
hermes config set OPENROUTER_API_KEY sk-or-...   # 自动存入 .env

# 检查是否有新版本引入的配置项未填写
hermes config check

# 交互式补全缺失配置
hermes config migrate

# 诊断所有配置问题
hermes doctor

# 更新到最新版本
hermes update
```


## 常见问题排查


### 问题一：hermes: command not found

```text
# 刷新 Shell 配置
source ~/.bashrc   # 或 source ~/.zshrc

# 如果仍然找不到，检查 PATH
echo $PATH
# 确保 ~/.local/bin 在其中
export PATH="$HOME/.local/bin:$PATH"
```


### 问题二：API key not set / 模型无响应

```text
# 重新配置提供商
hermes model

# 或直接设置 API Key
hermes config set OPENROUTER_API_KEY sk-or-...
```


### 问题三：回复为空或乱码

可能是提供商鉴权或模型选择有误：

```text
# 重新选择模型
hermes model

# 全面诊断
hermes doctor
```


### 问题四：上下文窗口不足报错

Hermes 要求模型至少支持 64K Token 上下文。切换到支持更大上下文的模型，或在使用本地模型时增大上下文参数（如 Ollama：OLLAMA_NUM_CTX=65536）。


### 问题五：hermes --continue 找不到旧会话

```text
# 查看所有会话
hermes sessions list

# 确认当前 Profile
hermes profile list
```


## 后续章节

- 万能恢复工具包
- 进阶配置预览
- 接入消息平台
- 启用语音模式
- 接入 MCP 服务器
- 编辑器集成（ACP）
- 快速命令参考

## 复习重点

- 能说明 `Hermes Agent 配置文件` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
