# Redis：Redis 安全

- 来源：[Redis 安全](https://www.runoob.com/redis/redis-security.html)
- 分类：数据库
- 技术：Redis
- 笔记类型：学习笔记
- 章节序号：1614

## 本章内容

我们可以通过 redis 的配置文件设置密码参数，这样客户端连接到 redis 服务就需要密码验证，这样可以让你的 redis 服务更安全。


### 实例

我们可以通过以下命令查看是否设置了密码验证：

```text
127.0.0.1:6379> CONFIG get requirepass
1) "requirepass"
2) ""
```

默认情况下 requirepass 参数是空的，这就意味着你无需通过密码验证就可以连接到 redis 服务。

你可以通过以下命令来修改该参数：

```text
127.0.0.1:6379> CONFIG set requirepass "runoob"
OK
127.0.0.1:6379> CONFIG get requirepass
1) "requirepass"
2) "runoob"
```

设置密码后，客户端连接 redis 服务就需要密码验证，否则无法执行命令。


### 语法

AUTH 命令基本语法格式如下：

```text
127.0.0.1:6379> AUTH password
```


### 实例

```text
127.0.0.1:6379> AUTH "runoob"
OK
127.0.0.1:6379> SET mykey "Test value"
OK
127.0.0.1:6379> GET mykey
"Test value"
```


## 复习重点

- 能说明 `Redis 安全` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
