# Memcached：Memcached 连接

- 来源：[Memcached 连接](https://www.runoob.com/memcached/memcached-connection.html)
- 分类：数据库
- 技术：Memcached
- 笔记类型：练习笔记
- 章节序号：1440

## 本章内容

我们可以通过 telnet 命令并指定主机ip和端口来连接 Memcached 服务。


### 语法

```text
telnet HOST PORT
```

命令中的 HOST 和 PORT 为运行 Memcached 服务的 IP 和 端口。


### 实例

以下实例演示了如何连接到 Memcached 服务并执行简单的 set 和 get 命令。

本实例的 Memcached 服务运行的主机为 127.0.0.1（本机） 、端口为 11211。

```text
telnet 127.0.0.1 11211

Trying 127.0.0.1...

Connected to 127.0.0.1.

Escape character is '^]'.

set foo 0 0 3                                                   保存命令

bar                                                             数据

STORED                                                          结果

get foo                                                         取得命令

VALUE foo 0 3                                                   数据

bar                                                             数据

END                                                             结束行

quit                                                            退出
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Memcached 连接` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
