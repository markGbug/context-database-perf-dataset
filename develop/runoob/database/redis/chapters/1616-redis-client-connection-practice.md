# Redis：Redis 客户端连接

- 来源：[Redis 客户端连接](https://www.runoob.com/redis/redis-client-connection.html)
- 分类：数据库
- 技术：Redis
- 笔记类型：练习笔记
- 章节序号：1616

## 本章内容

Redis 通过监听一个 TCP 端口或者 Unix socket 的方式来接收来自客户端的连接，当一个连接建立后，Redis 内部会进行以下一些操作：

- 首先，客户端 socket 会被设置为非阻塞模式，因为 Redis 在网络事件处理上采用的是非阻塞多路复用模型。
- 然后为这个 socket 设置 TCP_NODELAY 属性，禁用 Nagle 算法
- 然后创建一个可读的文件事件用于监听这个客户端 socket 的数据发送


## 最大连接数

在 Redis2.4 中，最大连接数是被直接硬编码在代码里面的，而在2.6版本中这个值变成可配置的。

maxclients 的默认值是 10000，你也可以在 redis.conf 中对这个值进行修改。

```text
config get maxclients

1) "maxclients"
2) "10000"
```


### 实例

以下实例我们在服务启动时设置最大连接数为 100000：

```text
redis-server --maxclients 100000
```


## 客户端命令


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Redis 客户端连接` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
