# Hermes Agent：Hermes Agent 平台消息接入

- 来源：[Hermes Agent 平台消息](https://www.runoob.com/hermes-agent/hermes-agent-gateway.html)
- 分类：AI / 智能开发
- 技术：Hermes Agent
- 笔记类型：概念卡
- 章节序号：0255

## 本章内容

消息网关（Messaging Gateway）让同一个 Agent——同样的记忆、技能和工具——在 20+ 平台上无缝运行。

本章将介绍 Gateway 的配置与部署、会话生命周期、多用户隔离策略以及安全访问控制。


## 消息网关概览

消息网关是一个常驻后台进程，统一管理所有消息平台的连接、会话、定时任务和媒体投递。

你在 CLI 中教给 Agent 的一切——记忆、技能、偏好——在所有平台上完全一致。


### 支持的平台

Hermes 支持 20+ 消息平台：CLI、Telegram、Discord、Slack、WhatsApp、Signal、Matrix、Mattermost、Email、SMS、钉钉、飞书/Lark、企业微信、微信、QQ、元宝、BlueBubbles（iMessage）、Home Assistant、Microsoft Teams、Google Chat 等。


### 平台能力对比

跨平台会话连续性：同一个 Agent 可以在不同平台之间保持上下文。比如你在 Telegram 上跟 Agent 聊了一半，切换到 Discord 后 Agent 仍然记得之前的对话。


## Gateway 启动与配置


### 桌面版配置

打开左侧菜单的消息平台，可以看到支持的平台，点击对应平台即可对应配置：


### 交互模式下配置

使用交互式向导完成所有平台的初始配置：

```text
hermes gateway setup
```

向导会引导你完成每个平台的配置：选择平台、填写 Bot Token、设置允许用户列表等。

比如选择飞书，进入后，可以选择扫描二维码创建机器人或通过 APP ID 创建：


### 网关管理命令


## 实例


### Telegram Bot 接入实战

以 Telegram 为例，完成一个完整的 Bot 接入流程。

步骤一：创建 Telegram Bot。

在 Telegram 中搜索 @BotFather，发送 /newbot 命令，按提示设置 Bot 名称和用户名。

BotFather 会返回一个 Bot API Token，格式类似：1234567890:ABCdefGHIjklMNOpqrsTUVwxyz。

步骤二：配置 Hermes Gateway。


## 实例

步骤三：启动并测试。


## 实例

首次接入建议使用白名单模式（allowed_users），只允许你自己的账号与 Agent 交互，待验证一切正常后再开放给其他人。


### 平台内可用的斜杠命令

在任何消息平台内，都可以使用以下命令：


## 会话生命周期

Session 是 Hermes Gateway 中管理对话的核心概念。

理解 Session 的工作原理，有助于你配置合适的会话隔离策略和重置规则。


### SessionSource：消息来源描述符

每条进入 Gateway 的消息都附带一个 SessionSource，它记录了这条消息「从哪里来」。


### Session Key 生成规则

Session Key 是由 SessionSource 中的字段组合而成的确定性字符串。

它决定了哪些消息属于同一个会话，格式如下：

```text
agent:main:{platform}:{chat_type}:{chat_id}:{thread_id}:{user_id}
```

不同场景下的 Session Key 示例：

Session Key 的生成规则是网关最重要的配置之一。如果配置不当，可能导致不同用户的会话「串线」——两个不同的人看到对方的对话内容。


### SessionEntry：活跃会话记录

每个 Session Key 对应一个 SessionEntry，它记录了会话的元数据和状态。


## 多用户隔离策略

多用户隔离决定了多个用户在同一个群组或频道中，是共享一个会话还是各自独立。

这个配置直接影响用户体验——共享会话意味着用户 A 可以看到用户 B 的对话上下文。


### 隔离策略配置


### 不同场景的行为


### 共享会话的系统提示词变化

当会话是共享模式（shared_multi_user_session = true）时，系统提示词会发生变化：

- 不再固定一个用户名，而是提示「多用户会话——消息前缀有发送者名称」
- 每条用户消息前会加上发送者的显示名称，让 Agent 知道是谁在说话
- 这种设计保持了提示词缓存的有效性（系统提示词不随发送者变化而变化）

默认的隔离策略（群组 per-user，线程 shared）是经过大量实践验证的最佳实践。除非有特殊需求，否则不建议修改。


## 网关安全配置


### 用户访问控制

默认情况下，网关拒绝所有未在白名单中的用户——这是拥有终端访问权限的 Bot 的安全默认设置。

配置允许访问的用户（在 .env 文件中）：


## 实例


### DM 配对（替代白名单）

无需手动配置用户 ID，新用户私信 Bot 时会收到一次性配对码：


## 后续章节

- 实例
- 沉默令牌
- 会话重置策略
- 实例
- 常用命令速查
- 实例

## 记忆卡片

- 一句话定义：`Hermes Agent 平台消息` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
