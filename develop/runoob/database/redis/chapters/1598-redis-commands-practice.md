# Redis：Redis 命令

- 来源：[Redis 命令](https://www.runoob.com/redis/redis-commands.html)
- 分类：数据库
- 技术：Redis
- 笔记类型：练习笔记
- 章节序号：1598

## 本章内容

Redis 命令用于在 redis 服务上执行操作。

要在 redis 服务上执行命令需要一个 redis 客户端。Redis 客户端在我们之前下载的的 redis 的安装包中。


### 语法

Redis 客户端的基本语法为：

```text
$ redis-cli
```


### 实例

以下实例讲解了如何启动 redis 客户端：

启动 redis 服务器，打开终端并输入命令 redis-cli，该命令会连接本地的 redis 服务。

```text
$ redis-cli
redis 127.0.0.1:6379>
redis 127.0.0.1:6379> PING

PONG
```

在以上实例中我们连接到本地的 redis 服务并执行 PING 命令，该命令用于检测 redis 服务是否启动。


## 在远程服务上执行命令

如果需要在远程 redis 服务上执行命令，同样我们使用的也是 redis-cli 命令。


### 语法

```text
$ redis-cli -h host -p port -a password
```


### 实例

以下实例演示了如何连接到主机为 127.0.0.1，端口为 6379 ，密码为 mypass 的 redis 服务上。

```text
$redis-cli -h 127.0.0.1 -p 6379 -a "mypass"
redis 127.0.0.1:6379>
redis 127.0.0.1:6379> PING

PONG
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Redis 命令` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
