# Redis：Redis 集合(Set)

- 来源：[Redis 集合(Set)](https://www.runoob.com/redis/redis-sets.html)
- 分类：数据库
- 技术：Redis
- 笔记类型：练习笔记
- 章节序号：1603

## 本章内容

Redis 的 Set 是 String 类型的无序集合。集合成员是唯一的，这就意味着集合中不能出现重复的数据。 集合对象的编码可以是 intset 或者 hashtable。

Redis 中集合是通过哈希表实现的，所以添加，删除，查找的复杂度都是 O(1)。

集合中最大的成员数为 232 - 1 (4294967295, 每个集合可存储40多亿个成员)。


### 实例

```text
redis 127.0.0.1:6379> SADD runoobkey redis
(integer) 1
redis 127.0.0.1:6379> SADD runoobkey mongodb
(integer) 1
redis 127.0.0.1:6379> SADD runoobkey mysql
(integer) 1
redis 127.0.0.1:6379> SADD runoobkey mysql
(integer) 0
redis 127.0.0.1:6379> SMEMBERS runoobkey

1) "mysql"
2) "mongodb"
3) "redis"
```

在以上实例中我们通过 SADD 命令向名为 runoobkey 的集合插入的三个元素。


## Redis 集合命令

下表列出了 Redis 集合基本命令：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Redis 集合(Set)` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
