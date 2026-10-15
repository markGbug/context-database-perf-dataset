# Redis：Redis 发布订阅

- 来源：[Redis 发布订阅](https://www.runoob.com/redis/redis-pub-sub.html)
- 分类：数据库
- 技术：Redis
- 笔记类型：练习笔记
- 章节序号：1606

## 本章内容

Redis 发布订阅 (pub/sub) 是一种消息通信模式：发送者 (pub) 发送消息，订阅者 (sub) 接收消息。

Redis 客户端可以订阅任意数量的频道。

下图展示了频道 channel1 ， 以及订阅这个频道的三个客户端 —— client2 、 client5 和 client1 之间的关系：

当有新消息通过 PUBLISH 命令发送给频道 channel1 时， 这个消息就会被发送给订阅它的三个客户端：


## 实例

以下实例演示了发布订阅是如何工作的，需要开启两个 redis-cli 客户端。

在我们实例中我们创建了订阅频道名为 runoobChat:


## 第一个 redis-cli 客户端

现在，我们先重新开启个 redis 客户端，然后在同一个频道 runoobChat 发布两次消息，订阅者就能接收到消息。


## 第二个 redis-cli 客户端

gif 演示如下：

- 开启本地 Redis 服务，开启两个 redis-cli 客户端。
- 在第一个 redis-cli 客户端输入 SUBSCRIBE runoobChat，意思是订阅 runoobChat 频道。
- 在第二个 redis-cli 客户端输入 PUBLISH runoobChat "Redis PUBLISH test" 往 runoobChat 频道发送消息，这个时候在第一个 redis-cli 客户端就会看到由第二个 redis-cli 客户端发送的测试消息。


## Redis 发布订阅命令

下表列出了 redis 发布订阅常用命令：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Redis 发布订阅` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
