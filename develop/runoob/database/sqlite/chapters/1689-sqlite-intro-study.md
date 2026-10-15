# SQLite：SQLite 简介

- 来源：[SQLite 简介](https://www.runoob.com/sqlite/sqlite-intro.html)
- 分类：数据库
- 技术：SQLite
- 笔记类型：学习笔记
- 章节序号：1689

## 本章内容

本教程帮助您了解什么是 SQLite，它与 SQL 之间的不同，为什么需要它，以及它的应用程序数据库处理方式。

SQLite是一个软件库，实现了自给自足的、无服务器的、零配置的、事务性的 SQL 数据库引擎。SQLite是一个增长最快的数据库引擎，这是在普及方面的增长，与它的尺寸大小无关。SQLite 源代码不受版权限制。


## 什么是 SQLite？

SQLite是一个进程内的库，实现了自给自足的、无服务器的、零配置的、事务性的 SQL 数据库引擎。它是一个零配置的数据库，这意味着与其他数据库不一样，您不需要在系统中配置。

就像其他数据库，SQLite 引擎不是一个独立的进程，可以按应用程序需求进行静态或动态连接。SQLite 直接访问其存储文件。


## 为什么要用 SQLite？

- 不需要一个单独的服务器进程或操作的系统（无服务器的）。
- SQLite 不需要配置，这意味着不需要安装或管理。
- 一个完整的 SQLite 数据库是存储在一个单一的跨平台的磁盘文件。
- SQLite 是非常小的，是轻量级的，完全配置时小于 400KiB，省略可选功能配置时小于250KiB。
- SQLite 是自给自足的，这意味着不需要任何外部的依赖。
- SQLite 事务是完全兼容 ACID 的，允许从多个进程或线程安全访问。
- SQLite 支持 SQL92（SQL2）标准的大多数查询语言的功能。
- SQLite 使用 ANSI-C 编写的，并提供了简单和易于使用的 API。
- SQLite 可在 UNIX（Linux, Mac OS-X, Android, iOS）和 Windows（Win32, WinCE, WinRT）中运行。


## 历史

- 2000 -- D. Richard Hipp 设计 SQLite 是为了不需要管理即可操作程序。
- 2000 -- 在八月，SQLite1.0 发布 GNU 数据库管理器（GNU Database Manager）。
- 2011 -- Hipp 宣布，向 SQLite DB 添加 UNQl 接口，开发 UNQLite（面向文档的数据库）。


## SQLite 局限性

在 SQLite 中，SQL92 不支持的特性如下所示：


## SQLite 命令

与关系数据库进行交互的标准 SQLite 命令类似于 SQL。命令包括 CREATE、SELECT、INSERT、UPDATE、DELETE 和 DROP。这些命令基于它们的操作性质可分为以下几种：


## DDL - 数据定义语言


## DML - 数据操作语言


## DQL - 数据查询语言


## 复习重点

- 能说明 `SQLite 简介` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
