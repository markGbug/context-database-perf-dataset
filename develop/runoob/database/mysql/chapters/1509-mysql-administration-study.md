# MySQL：MySQL 管理

- 来源：[MySQL 管理](https://www.runoob.com/mysql/mysql-administration.html)
- 分类：数据库
- 技术：MySQL
- 笔记类型：学习笔记
- 章节序号：1509

## 本章内容

## 启动及关闭 MySQL 服务器


### Windows 系统下

启动 MySQL 服务器:

1、通过 "服务" 管理工具： 打开"运行"对话框（Win + R），输入 services.msc，找到"MySQL"服务，右击选择"启动"。

2、通过命令提示符： 打开命令提示符（以管理员身份），输入以下命令：

```text
net start mysql
```

关闭MySQL服务器:

1、通过 "服务" 管理工具：同样打开"运行"对话框，输入 services.msc，找到 "MySQL" 服务，右击选择"停止"。

2、通过命令提示符： 打开命令提示符（以管理员身份），输入以下命令：

```text
net stop mysql
```


### Linux 系统下

1、启动 MySQL 服务：

使用 systemd命令（适用于大多数现代 Linux 发行版，如 Ubuntu、CentOS 等）：

```text
sudo systemctl start mysql
```

使用 service 命令（在一些较旧的发行版中）：

```text
sudo service mysql start
```

2、关闭 MySQL 服务：

使用 systemd：

```text
sudo systemctl stop mysql
```

使用 service 命令：

```text
sudo service mysql stop
```

3、重启 MySQL 服务：

```text
sudo systemctl restart mysql
```

使用 service 命令：

```text
sudo service mysql restart
```

4、检查 MySQL 服务状态：

使用 systemd命令：

```text
sudo systemctl status mysql
```

使用 service 命令：

```text
sudo service mysql status
```


### Mac OS 系统

启动 MySQL 服务：

使用命令行：

```text
sudo /usr/local/mysql/support-files/mysql.server start
```

关闭 MySQL 服务：

使用命令行：

```text
sudo /usr/local/mysql/support-files/mysql.server stop
```

重启 MySQL 服务：

使用命令行：

```text
sudo /usr/local/mysql/support-files/mysql.server restart
```

检查 MySQL 服务状态：

使用命令行：

```text
sudo /usr/local/mysql/support-files/mysql.server status
```

以上命令中，mysql 可能会因为安装路径或版本的不同而有所变化。

在 Mac OS 中，MySQL 的安装路径通常是 /usr/local/mysql/，因此启动和关闭 MySQL 服务需要使用这个路径下的 mysql.server 脚本。


## MySQL 用户设置

在 MySQL 中，用户设置包括创建用户、设置权限、管理用户等操作。以下是一些常用的 MySQL 用户设置操作，包括创建用户、设置权限、查看和删除用户等。


### 创建用户

要创建一个新用户，你可以使用以下 SQL 命令：

```text
CREATE USER 'username'@'host' IDENTIFIED BY 'password';
```

- username：用户名。
- host：指定用户可以从哪些主机连接。例如，localhost 仅允许本地连接，% 允许从任何主机连接。
- password：用户的密码。


## 实例


### 授权权限

创建用户后，你需要授予他们访问权限，使用 GRANT 命令来授予权限：

```text
GRANT privileges ON database_name.* TO 'username'@'host';
```


## 复习重点

- 能说明 `MySQL 管理` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
