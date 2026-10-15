# Redis：Redis 字符串(String)

- 来源：[Redis 字符串(String)](https://www.runoob.com/redis/redis-strings.html)
- 分类：数据库
- 技术：Redis
- 笔记类型：练习笔记
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


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Redis 字符串(String)` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
