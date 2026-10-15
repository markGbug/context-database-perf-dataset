# Redis：Redis 连接

- 来源：[Redis 连接](https://www.runoob.com/redis/redis-connection.html)
- 分类：数据库
- 技术：Redis
- 笔记类型：学习笔记
- 章节序号：1609

## 本章内容

Redis 连接命令主要是用于连接 redis 服务。


### 实例

以下实例演示了客户端如何通过密码验证连接到 redis 服务，并检测服务是否在运行：

```text
redis 127.0.0.1:6379> AUTH "password"
OK
redis 127.0.0.1:6379> PING
PONG
```


## Redis 连接命令

下表列出了 redis 连接的基本命令：


## 复习重点

- 能说明 `Redis 连接` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
