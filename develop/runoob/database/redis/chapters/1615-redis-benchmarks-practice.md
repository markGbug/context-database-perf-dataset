# Redis：Redis 性能测试

- 来源：[Redis 性能测试](https://www.runoob.com/redis/redis-benchmarks.html)
- 分类：数据库
- 技术：Redis
- 笔记类型：练习笔记
- 章节序号：1615

## 本章内容

Redis 性能测试是通过同时执行多个命令实现的。


### 语法

redis 性能测试的基本命令如下：

```text
redis-benchmark [option] [option value]
```

注意：该命令是在 redis 的目录下执行的，而不是 redis 客户端的内部指令。


### 实例

以下实例同时执行 10000 个请求来检测性能：

```text
$ redis-benchmark -n 10000  -q

PING_INLINE: 141043.72 requests per second
PING_BULK: 142857.14 requests per second
SET: 141442.72 requests per second
GET: 145348.83 requests per second
INCR: 137362.64 requests per second
LPUSH: 145348.83 requests per second
LPOP: 146198.83 requests per second
SADD: 146198.83 requests per second
SPOP: 149253.73 requests per second
LPUSH (needed to benchmark LRANGE): 148588.42 requests per second
LRANGE_100 (first 100 elements): 58411.21 requests per second
LRANGE_300 (first 300 elements): 21195.42 requests per second
LRANGE_500 (first 450 elements): 14539.11 requests per second
LRANGE_600 (first 600 elements): 10504.20 requests per second
MSET (10 keys): 93283.58 requests per second
```

redis 性能测试工具可选参数如下所示：


### 实例

以下实例我们使用了多个参数来测试 redis 性能：

```text
$ redis-benchmark -h 127.0.0.1 -p 6379 -t set,lpush -n 10000 -q

SET: 146198.83 requests per second
LPUSH: 145560.41 requests per second
```

以上实例中主机为 127.0.0.1，端口号为 6379，执行的命令为 set,lpush，请求数为 10000，通过 -q 参数让结果只显示每秒执行的请求数。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Redis 性能测试` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
