# MongoDB：MongoDB 用户管理

- 来源：[MongoDB 用户管理](https://www.runoob.com/mongodb/mongodb-user.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：学习笔记
- 章节序号：1466

## 本章内容

在 MongoDB 中进行用户管理涉及用户的创建、分配角色、认证和登录等操作。

下面是一个详细的说明，包含如何使用 MongoDB Shell (mongo) 或 MongoDB Compass 来管理用户。


### 使用 MongoDB Shell (mongo) 管理用户

以下是使用 MongoDB Shell (mongosh) 进行用户管理的详细说明，包括创建用户、分配角色、认证和登录的具体步骤。

1. 连接到 MongoDB

首先，打开你的终端并使用 mongosh 命令连接到 MongoDB 服务器：

```html
mongosh --host <hostname> --port <port>
```

说明：

- mongosh：启动 MongoDB Shell 命令行工具。
- --host <hostname>：指定 MongoDB 服务器的主机名或 IP 地址。<hostname>：MongoDB 服务器的主机名（如 localhost）或 IP 地址（如 127.0.0.1）。
- --port <port>：指定 MongoDB 服务器的端口号。<port>：MongoDB 服务器监听的端口号，默认端口是 27017。

2. 切换到目标数据库

在 MongoDB 中，用户是针对特定数据库创建的，使用 use 命令切换到你要创建用户的数据库：

```html
use <database_name>
```

- database_name - 为要切换的数据库。

3. 创建用户

使用 db.createUser 命令创建用户并分配角色。

例如，创建一个名为 testuser 的用户，密码为 password123，并赋予 readWrite 和 dbAdmin 角色：

```html
db.createUser({
  user: "testuser",
  pwd: "password123",
  roles: [
    { role: "readWrite", db: "<database_name>" },
    { role: "dbAdmin", db: "<database_name>" }
  ]
})
```

4. 验证用户

创建用户后，你可以使用 db.auth 命令验证用户身份：

```text
db.auth("testuser", "password123")
```

5. 启用身份验证

为了确保只有经过身份验证的用户才能访问 MongoDB，需要启用身份验证。

编辑 MongoDB 配置文件 mongod.conf，并在其中添加以下内容：

```text
security:
  authorization: "enabled"
```

然后重启 MongoDB 服务以应用更改。

6. 使用用户身份登录

启用身份验证后，你需要使用创建的用户身份连接到 MongoDB：

```html
mongosh --host <hostname> --port <port> -u "testuser" -p "password123" --authenticationDatabase "<database_name>"
```

7. 删除用户


### 实例操作

以下是一个完整的示例操作流程：

启动 MongoDB Shell 并连接到服务器：

```text
mongosh --host localhost --port 27017
```

切换到 testdb 数据库：

```text
use testdb
```

创建 testuser 用户：

```text
db.createUser({
  user: "testuser",
  pwd: "password123",
  roles: [{ role: "readWrite", db: "testdb" }]
})
```

启用身份验证并重启 MongoDB 实例

编辑 mongod.conf 文件，添加以下内容：

```text
security:
  authorization: "enabled"
```

重启 MongoDB 服务：

```text
sudo systemctl restart mongod
```

使用 testuser 用户进行身份验证连接：

```text
mongosh --host localhost --port 27017 -u "testuser" -p "password123" --authenticationDatabase "testdb"
```

删除 testuser 用户：

```text
db.dropUser("testuser")
```


## 复习重点

- 能说明 `MongoDB 用户管理` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
