# MongoDB：Mac OSX 平台安装 MongoDB

- 来源：[OSX MongoDB](https://www.runoob.com/mongodb/mongodb-osx-install.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：练习笔记
- 章节序号：1463

## 本章内容

MongoDB 提供了 OSX 平台上 64 位的安装包，你可以在官网下载安装包。

下载地址：https://www.mongodb.com/try/download/community

从 MongoDB 3.0 版本开始只支持 OS X 10.7 (Lion) 版本及更新版本的系统。

接下来我们使用 curl 命令来下载安装：

```text
# 进入 /usr/local
cd /usr/local

# 下载
sudo curl -O https://fastdl.mongodb.org/osx/mongodb-osx-ssl-x86_64-4.0.9.tgz

# 解压
sudo tar -zxvf mongodb-osx-ssl-x86_64-4.0.9.tgz

# 重命名为 mongodb 目录

sudo mv mongodb-osx-x86_64-4.0.9/ mongodb
```

安装完成后，我们可以把 MongoDB 的二进制命令文件目录（安装目录/bin）添加到 PATH 路径中：

```text
export PATH=/usr/local/mongodb/bin:$PATH
```

创建日志及数据存放的目录：

- 数据存放路径：sudo mkdir -p /usr/local/var/mongodb
- 日志文件路径：sudo mkdir -p /usr/local/var/log/mongodb

接下来要确保当前用户对以上两个目录有读写的权限：

```text
sudo chown runoob /usr/local/var/mongodb
sudo chown runoob /usr/local/var/log/mongodb
```

创建日志文件：

```text
sudo touch /usr/local/var/log/mongodb/mongo.log
sudo chown runoob /usr/local/var/log/mongodb/mongo.log
```

以上 runoob 是我电脑上的用户，你这边需要根据你当前对用户名来修改。

接下来我们使用以下命令在后台启动 mongodb：

```text
mongod --dbpath /usr/local/var/mongodb --logpath /usr/local/var/log/mongodb/mongo.log --fork
```

- --dbpath 设置数据存放目录


## 使用 brew 安装

此外你还可以使用 OSX 的 brew 来安装 mongodb：

```text
brew tap mongodb/brew
brew install mongodb-community@4.4
```

@ 符号后面的 4.4 是最新版本号。

安装信息：

- 配置文件：/usr/local/etc/mongod.conf
- 日志文件路径：/usr/local/var/log/mongodb
- 数据存放路径：/usr/local/var/mongodb


### 运行 MongoDB

我们可以使用 brew 命令或 mongod 命令来启动服务。

brew 启动：

```text
brew services start mongodb-community@4.4
```

brew 停止：

```text
brew services stop mongodb-community@4.4
```

mongod 命令后台进程方式：

```text
mongod --config /usr/local/etc/mongod.conf --fork
```

```text
> db.adminCommand({ "shutdown" : 1 })
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `OSX MongoDB` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
