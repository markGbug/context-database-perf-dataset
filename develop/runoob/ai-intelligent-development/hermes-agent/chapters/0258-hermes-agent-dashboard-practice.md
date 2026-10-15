# Hermes Agent：Hermes Agent 部署模式与 Dashboard

- 来源：[Hermes Agent 部署模式](https://www.runoob.com/hermes-agent/hermes-agent-dashboard.html)
- 分类：AI / 智能开发
- 技术：Hermes Agent
- 笔记类型：练习笔记
- 章节序号：0258

## 本章内容

Hermes 支持从笔记本到 GPU 集群的全场景部署。

本章逐一介绍六种部署模式的配置方法、适用场景和对比，以及 Web Dashboard 的可视化管理功能。


## 六种部署模式详解


### 模式一：本地 CLI

最简单的部署方式，Agent 与你同机运行，零配置。

直接对话：

```text
hermes chat
```

TUI 界面：

```text
hermes --tui
```

桌面应用：

```text
hermes desktop
```

特点：最简单，零配置，适合开发和个人日常使用。


### 模式二：网关服务

让 Agent 作为 24/7 在线 Bot 持续运行，随时响应消息平台的消息，支持定时任务。

前台调试运行，日志直接输出控制台：

```text
hermes gateway
```

注册系统服务并后台启动，用于生产常驻：

```text
hermes gateway install && hermes gateway start
```

查看网关运行状态：

```text
hermes gateway status
```

其他命令：

```text
# 停止服务
hermes gateway stop
# 重启服务
hermes gateway restart
# 卸载系统服务
hermes gateway uninstall
```

特点：Agent 持续在线，适合个人 Bot、团队助手等场景。


### 模式三：Docker 容器

官方镜像支持多 Profile 网关，由 s6-overlay 管理进程。

拉取官方镜像：

```text
docker pull nousresearch/hermes-agent:latest
```

运行（挂载配置目录）：

```text
docker run -d \
  --name hermes \
  -v ~/.hermes:/root/.hermes \
  -e OPENROUTER_API_KEY=sk-or-... \
  -e TELEGRAM_BOT_TOKEN=... \
  nousresearch/hermes-agent:latest
```

Docker 内多 Profile 网关由 s6-overlay 自动监督。

hermes profile create 会自动注册 s6 服务槽位，Docker 重启后自动恢复之前运行中的所有网关。

让 Agent 的终端命令也在容器内执行：


## 实例

特点：进程和命令双重容器隔离，适合 CI/CD 和生产环境。


### 模式四：SSH 远程服务器

Agent 在本地运行，但所有终端命令在远程服务器上执行。


## 实例

典型场景：在本地发送消息，让 Agent 在远程 GPU 服务器上训练模型、处理大数据集。


### 模式五：Modal Serverless

Agent 在 Modal 云沙箱（VM）中执行命令，空闲时几乎不产生费用。


## 实例

特点：按需计费，适合偶发性的高强度计算任务。


### 模式六：Daytona 托管工作区

Hermes 进程和终端沙箱都在云端，完全不依赖本地机器。


## 实例

特点：完全云端，托管的云开发环境。


### 六种模式对比


## Web Dashboard

Dashboard 是 Hermes 的可视化管理界面，可以管理任意 Profile 的配置、模型、技能、MCP 和会话。


### 启动 Dashboard

使用以下命令启动 Dashboard：

```text
hermes dashboard
```

启动界面如下：

查看 skills：

相关命令：

```text
# 启动 Dashboard（默认 Profile）
hermes dashboard

# 启动并预选指定 Profile
coder dashboard

# 指定端口
hermes dashboard --port 8080
```


### Dashboard 功能一览


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Hermes Agent 部署模式` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
