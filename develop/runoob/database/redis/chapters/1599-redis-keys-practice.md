# Redis：Redis 键(key)

- 来源：[Redis 键(key)](https://www.runoob.com/redis/redis-keys.html)
- 分类：数据库
- 技术：Redis
- 笔记类型：练习笔记
- 章节序号：1599

## 本章内容

Redis 键命令用于管理 redis 的键。


### 语法

Redis 键命令的基本语法如下：

```text
redis 127.0.0.1:6379> COMMAND KEY_NAME
```


### 实例

```text
redis 127.0.0.1:6379> SET runoobkey redis
OK
redis 127.0.0.1:6379> DEL runoobkey
(integer) 1
```

在以上实例中 DEL 是一个命令， runoobkey 是一个键。 如果键被删除成功，命令执行后输出 (integer) 1，否则将输出 (integer) 0


## Redis keys 命令

下表给出了与 Redis 键相关的基本命令：

更多命令请参考：https://redis.io/commands


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Redis 键(key)` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
