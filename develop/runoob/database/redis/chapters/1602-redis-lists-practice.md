# Redis：Redis 列表(List)

- 来源：[Redis 列表(List)](https://www.runoob.com/redis/redis-lists.html)
- 分类：数据库
- 技术：Redis
- 笔记类型：练习笔记
- 章节序号：1602

## 本章内容

Redis列表是简单的字符串列表，按照插入顺序排序。你可以添加一个元素到列表的头部（左边）或者尾部（右边）

一个列表最多可以包含 232 - 1 个元素 (4294967295, 每个列表超过40亿个元素)。


### 实例

```text
redis 127.0.0.1:6379> LPUSH runoobkey redis
(integer) 1
redis 127.0.0.1:6379> LPUSH runoobkey mongodb
(integer) 2
redis 127.0.0.1:6379> LPUSH runoobkey mysql
(integer) 3
redis 127.0.0.1:6379> LRANGE runoobkey 0 10

1) "mysql"
2) "mongodb"
3) "redis"
```

在以上实例中我们使用了 LPUSH 将三个值插入了名为 runoobkey 的列表当中。


### Redis 列表命令

下表列出了列表相关的基本命令：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Redis 列表(List)` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
