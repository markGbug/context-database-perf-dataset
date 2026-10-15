# Redis：Redis 字符串(String)

- 来源：[Redis 字符串(String)](https://www.runoob.com/redis/redis-strings.html)
- 分类：数据库
- 技术：Redis
- 笔记类型：学习笔记
- 章节序号：1600

## 本章内容

Redis 字符串数据类型的相关命令用于管理 redis 字符串值，基本语法如下：


### 语法

```text
redis 127.0.0.1:6379> COMMAND KEY_NAME
```


### 实例

```text
redis 127.0.0.1:6379> SET runoobkey redis
OK
redis 127.0.0.1:6379> GET runoobkey
"redis"
```

在以上实例中我们使用了 SET 和 GET 命令，键为 runoobkey。


## Redis 字符串命令

下表列出了常用的 redis 字符串命令：

更多命令请参考：https://redis.io/commands


## 复习重点

- 能说明 `Redis 字符串(String)` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
