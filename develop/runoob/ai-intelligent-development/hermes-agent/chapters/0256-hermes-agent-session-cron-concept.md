# Hermes Agent：Hermes Agent Session 生命周期与定时任务

- 来源：[Hermes Agent 定时任务](https://www.runoob.com/hermes-agent/hermes-agent-session-cron.html)
- 分类：AI / 智能开发
- 技术：Hermes Agent
- 笔记类型：概念卡
- 章节序号：0256

## 本章内容

## Session 重置策略

重置策略控制会话何时自动「失忆」——获得一个新的 session_id，旧的上下文被归档。

合理配置重置策略可以避免 Agent 上下文无限膨胀，同时确保用户体验不受影响。


### 四种重置模式


### 配置重置策略


## 实例


### 重置效果

当会话触发重置时，会发生以下事情：

- 旧会话在 SQLite 中被标记为结束（reason: "session_reset"）
- 生成新的 session_id（格式：YYYYMMDD_HHMMSS_8位随机hex）
- 新 SessionEntry 的 was_auto_reset 标记为 true
- 缓存的 Agent 实例被清理
- 用户在下一条消息中会收到「会话已重置」的提示

有活跃后台进程的会话永远不会被重置。Hermes 会检查 has_active_processes 回调，确保不会中断正在运行的任务。


## 重启恢复机制

Hermes Gateway 的重启恢复机制确保在意外崩溃或计划内重启后，正在进行的会话不会丢失。


### 两种恢复标记


### 启动恢复流程

当 Gateway 启动时，恢复流程如下：

第一步：检查 .clean_shutdown 标记。

如果存在，说明上次是正常关闭，跳过恢复流程。

第二步：如果不存在 .clean_shutdown 标记，说明上次是异常退出。

Gateway 调用 suspend_recently_active()，将最近 120 秒内有活动的会话标记为 resume_pending。

第三步：检测 stuck-loop（卡死循环）。

如果某个会话在连续 3 次重启后仍然处于活跃状态，说明它可能陷入了死循环，Gateway 会将其标记为 suspended。

第四步：恢复待处理会话。

Gateway 为每个 resume_pending 的会话合成一条 MessageEvent，触发 Agent 自动继续。


### Drain 超时标记

在正常关闭/重启过程中，如果某个会话正在处理中但超过了 drain 等待时间，Gateway 会将其标记为 resume_pending。

不同场景的标记原因：

resume_pending 标记不会在 get_or_create_session() 时被清除——它会在下一次成功的 Agent 回复后被清除。如果恢复后的会话再次中断，标记保留，允许下次重启时重试。连续 3 次失败后升级为 suspended。


## 消息队列机制

当用户在 Agent 处理消息期间连续发送多条消息时，Gateway 的消息队列机制确保消息不会丢失。


### 队列结构

Gateway 使用两级队列设计：

- 单槽 pending（_pending_messages）：每个会话只有一个「下一条」槽位，重复发送会覆盖
- 溢出队列（_queued_events）：当槽位被占用时，后续消息追加到溢出队列尾部


### /queue 命令

/queue 命令让你可以批量提交任务，每个任务都会产生一个完整的 Agent 回合。


## 实例

队列中的每个任务按 FIFO 顺序依次执行，每个任务产生一个完整的 Agent 回合，不会合并。

使用 /new 或 /reset 命令可以清空当前会话的消息队列。

在 Agent 处理消息期间连续发送多条消息，中间的会被覆盖（只保留最后一条），/queue 命令中的消息则不会被覆盖——每个 /queue 任务都会按顺序执行。


## 定时任务（Cron）

Hermes 内置了 first-class 的定时任务支持，让你可以配置 Agent 定期执行特定任务。

定时任务可以绑定 Skill，并将结果投递到指定平台。


### 配置定时任务

定时任务在 jobs.json 中定义，支持多种调度格式。

```text
{
  "jobs": [
    {
      "id": "daily-news-summary",
      "schedule": "0 8 * * *",
      "description": "每天早上 8 点抓取 AI 行业新闻并生成摘要",
      "skill": "ai-news-summarizer",
      "deliver_to": {
        "platform": "telegram",
        "chat_id": "-1001234567890"
      }
    },
    {
      "id": "weekly-code-review",
      "schedule": "0 10 * * 1",
      "description": "每周一早上 10 点审查项目代码变更",
      "skill": "code-review-assistant",
      "deliver_to": {
        "platform": "discord",
        "chat_id": "123456789"
      }
    },
    {
      "id": "health-check",
      "schedule": "*/30 * * * *",
      "description": "每 30 分钟检查服务器健康状态",
      "skill": "server-health-checker",
      "deliver_to": {
        "platform": "telegram",
        "chat_id": "123456789"
      }
    }
  ]
}
```


### 支持的调度格式

可以在桌面版配置, 点击左下角的排程：

点击新建定时任务：

创建任务：

定时任务绑定 Skill 后，执行的输出会自动格式化为 Skill 定义的输出格式。这确保了定时任务的结果在投递到消息平台时，呈现方式一致且可读。


## Chronos 托管 Cron（进阶）

Chronos 是 Hermes 的托管式定时任务方案，专为 scale-to-zero 部署模式设计。

当你的 Gateway 在空闲时完全停止运行，Chronos 仍然可以确保定时任务按时触发。


### 为什么需要 Chronos？

内置的 cron ticker 需要 Gateway 进程持续运行——如果 Gateway 缩容到零，定时任务就不会触发。

Chronos 将定时任务的管理委托给 NAS（Nous Account Service），通过外部调度器在任务触发时唤醒 Gateway。


### Chronos 工作流程

Chronos 的工作流程分为四个步骤：

第一步：Agent 计算下次触发时间，向 NAS 注册一个 one-shot 定时器。

第二步：NAS 使用外部调度器（如 Fly Machines 的定时触发）在指定时间触发回调。

第三步：外部调度器回调 NAS，NAS 生成一个短时效的 JWT Token。

第四步：NAS 使用 JWT Token 调用 Agent 的 /api/cron/fire 端点，Agent 验证后执行任务并重新注册下一个 one-shot。


### At-most-once 保证

Chronos 通过 store 级的 CAS（Compare-And-Set）操作保证每个定时任务只执行一次。

即使调度器因为网络重试发送了重复的触发请求，Agent 也能通过 CAS 去重，确保任务不会重复执行。


### 配置 Chronos


## 实例

Chronos 是托管 Hermes 部署的推荐定时任务方案。如果你使用自托管部署且 Gateway 不会缩容到零，内置的 cron ticker 完全够用。如果 callback_url 为空或 Agent 没有 Nous 登录，系统会自动回退到内置 ticker。


## 记忆卡片

- 一句话定义：`Hermes Agent 定时任务` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
