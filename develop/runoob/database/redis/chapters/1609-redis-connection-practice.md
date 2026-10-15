# Redis：Redis 连接

- 来源：[Redis 连接](https://www.runoob.com/redis/redis-connection.html)
- 分类：数据库
- 技术：Redis
- 笔记类型：练习笔记
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


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Redis 连接` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
