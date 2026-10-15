# MongoDB：MongoDB - 连接

- 来源：[MongoDB 连接](https://www.runoob.com/mongodb/mongodb-connections.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：练习笔记
- 章节序号：1467

## 本章内容

在本教程我们将讨论 MongoDB 的不同连接方式。


### 启动 MongoDB 服务

在前面的教程中，我们已经讨论了如何启动 MongoDB 服务，你只需要在 MongoDB 安装目录的 bin 目录下执行 mongodb 即可。

执行启动操作后，mongodb 在输出一些必要信息后不会输出任何信息，之后就等待连接的建立，当连接被建立后，就会开始打印日志信息。

你可以使用 MongoDB shell 来连接 MongoDB 服务器。你也可以使用 PHP 来连接 MongoDB。本教程我们会使用 MongoDB shell 来连接 Mongodb 服务，之后的章节我们将会介绍如何通过 PHP、Python 以及 Node.js 来连接 MongoDB 服务。

标准 URI 连接语法：

```text
mongodb://[username:password@]host1[:port1][,...hostN[:portN]][/[defaultauthdb][?options]]
```

- mongodb://：协议头，表示使用 MongoDB。
- [username:password@]：（可选）认证信息，包括用户名和密码。
- host1[:port1][,...hostN[:portN]]：服务器地址和端口，可以是一个或多个 MongoDB 服务器的地址和端口。
- /[defaultauthdb]：（可选）默认认证数据库。
- [?options]：（可选）连接选项。

标准的连接格式包含了多个选项(options)，如下所示：

- authSource：指定认证数据库。
- replicaSet：指定副本集的名称。
- ssl：启用 SSL 连接（true 或 false）。
- readPreference：指定读偏好，如 primary, primaryPreferred, secondary, secondaryPreferred, nearest。
- connectTimeoutMS：指定连接超时时间（毫秒）。
- socketTimeoutMS：指定套接字超时时间（毫秒）。

连接到本地 MongoDB 实例（默认端口 27017）：

```text
mongodb://localhost
```

连接到本地 MongoDB 实例，指定数据库：

```text
mongodb://localhost/mydatabase
```

使用用户名和密码连接到本地 MongoDB 实例：

```text
mongodb://username:password@localhost/mydatabase
```

连接到远程 MongoDB 实例：

```text
mongodb://remotehost:27017
```

连接到副本集（Replica Set）：

```text
mongodb://host1:27017,host2:27017,host3:27017/mydatabase?replicaSet=myReplicaSet
```

使用 SSL 连接到 MongoDB：


### Python (PyMongo)


## 实例


### Node.js (Mongoose)


## 实例


### PHP (Mongoose)


## 实例


### Java


## 实例


### 实例

使用默认端口来连接 MongoDB 的服务。

```text
mongodb://localhost
```

通过 shell 连接 MongoDB 服务：

```text
./mongosh
Current Mongosh Log ID:    66792d6b87657ebec9ed70f1
Connecting to:        mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.2.9
Using MongoDB:        7.0.11
Using Mongosh:        2.2.9
```

这时候你返回查看运行 ./mongod 命令的窗口，可以看到是从哪里连接到MongoDB的服务器，您可以看到如下信息：

```text
……省略信息……
2015-09-25T17:22:27.336+0800 I CONTROL  [initandlisten] allocator: tcmalloc
2015-09-25T17:22:27.336+0800 I CONTROL  [initandlisten] options: { storage: { dbPath: "/data/db" } }
2015-09-25T17:22:27.350+0800 I NETWORK  [initandlisten] waiting for connections on port 27017
2015-09-25T17:22:36.012+0800 I NETWORK  [initandlisten] connection accepted from 127.0.0.1:37310 #1 (1 connection now open)  # 该行表明一个来自本机的连接

……省略信息……
```


## MongoDB 连接命令格式

使用用户名和密码连接到 MongoDB 服务器，你必须使用 'username:password@hostname/dbname' 格式，'username'为用户名，'password' 为密码。

使用用户名和密码连接登录到默认数据库：

```text
$ ./mongosh
MongoDB shell version: 4.0.9
connecting to: test
```

使用用户 admin 使用密码 123456 连接到本地的 MongoDB 服务上。输出结果如下所示：

```text
> mongodb://admin:123456@localhost/
...
```

使用用户名和密码连接登录到指定数据库，格式如下：

```text
mongodb://admin:123456@localhost/test
```


### 更多连接实例

连接本地数据库服务器，端口是默认的。

```text
mongodb://localhost
```

使用用户名fred，密码foobar登录localhost的admin数据库。

```text
mongodb://fred:foobar@localhost
```

使用用户名fred，密码foobar登录localhost的baz数据库。

```text
mongodb://fred:foobar@localhost/baz
```

连接 replica pair, 服务器1为example1.com服务器2为example2。

```text
mongodb://example1.com:27017,example2.com:27017
```

连接 replica set 三台服务器 (端口 27017, 27018, 和27019):

```text
mongodb://localhost,localhost:27018,localhost:27019
```

连接 replica set 三台服务器, 写入操作应用在主服务器 并且分布查询到从服务器。

```text
mongodb://host1,host2,host3/?slaveOk=true
```

直接连接第一个服务器，无论是replica set一部分或者主服务器或者从服务器。

```text
mongodb://host1,host2,host3/?connect=direct;slaveOk=true
```

当你的连接服务器有优先级，还需要列出所有服务器，你可以使用上述连接方式。

安全模式连接到localhost:

```text
mongodb://localhost/?safe=true
```

以安全模式连接到replica set，并且等待至少两个复制服务器成功写入，超时时间设置为2秒。

```text
mongodb://host1,host2,host3/?safe=true;w=2;wtimeoutMS=2000
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MongoDB 连接` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
