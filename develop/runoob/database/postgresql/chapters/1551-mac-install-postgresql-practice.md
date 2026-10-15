# PostgreSQL：Mac OS 上安装 PostgreSQL

- 来源：[Mac OS 上安装 PostgreSQL](https://www.runoob.com/postgresql/mac-install-postgresql.html)
- 分类：数据库
- 技术：PostgreSQL
- 笔记类型：练习笔记
- 章节序号：1551

## 本章内容

## Mac OS 上安装 PostgreSQL

使用 EnterpriseDB 来下载安装，EnterpriseDB 是全球唯一一家提供基于 PostgreSQL 企业级产品与服务的厂商。

下载地址：https://www.enterprisedb.com/downloads/postgres-postgresql-downloads。

下载 postgresql-****-osx.dmg 文件，双击安装文件：

这时会要求你输入管理员密码，输入即可，之后弹出安装向导：

接下来就是一些基本的配置，比如：安装目录、扩展安装、数据库目录、用户密码、端口设置等，一般使用默认的就好，直接点 Next：

最后，点击 Finish 即可：

执行以下脚本启动 PostgreSQL。

以下几个选项你可以自己输入，或者用默认的，默认回车就行，密码的地方为刚才你在安装过程中设置的密码：

```text
$ /Library/PostgreSQL/11/scripts/runpsql.sh ;exit
Server [localhost]:
Database [postgres]:
Port [5432]:
Username [postgres]:
Password for user postgres:
psql (11.3)
Type "help" for help.

postgres=#
```


### pgAdmin 4

打开 pgAdmin 4：

或者在屏幕右上方点击大象头像的图标：

pgAdmin 主页如下

点击左侧的 Servers > Postgre SQL 10

输入密码，点击 OK 即可

控制面板如下


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Mac OS 上安装 PostgreSQL` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
