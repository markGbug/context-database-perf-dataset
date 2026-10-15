# MongoDB：MongoDB 简介

- 来源：[MongoDB 简介](https://www.runoob.com/mongodb/mongodb-intro.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：学习笔记
- 章节序号：1460

## 本章内容

## 什么是 MongoDB ?

MongoDB 是一个文档型数据库，数据以类似 JSON 的文档形式存储。

MongoDB 的设计理念是为了应对大数据量、高性能和灵活性需求。

MongoDB使用集合（Collections）来组织文档（Documents），每个文档都是由键值对组成的。

- 数据库（Database）：存储数据的容器，类似于关系型数据库中的数据库。
- 集合（Collection）：数据库中的一个集合，类似于关系型数据库中的表。
- 文档（Document）：集合中的一个数据记录，类似于关系型数据库中的行（row），以 BSON 格式存储。

MongoDB 将数据存储为一个文档，数据结构由键值(key=>value)对组成，文档类似于 JSON 对象，字段值可以包含其他文档，数组及文档数组：


## 主要特点

- 文档导向的存储：MongoDB 是一个面向文档的数据库，它以 JSON-like 的格式存储数据，使得数据结构更加灵活和丰富。
- 索引优化查询：MongoDB 允许用户为文档中的任意属性创建索引，例如 FirstName 和 Address，从而提高查询效率和排序性能。
- 数据镜像与扩展性：通过本地或网络创建数据的副本，MongoDB 实现了强大的数据冗余和扩展能力。
- 水平扩展与分片：面对增加的负载，MongoDB 可以通过分片技术将数据分布到计算机网络中的其他节点上，实现水平扩展。
- 强大的查询语言：MongoDB 使用 JSON 格式的查询语法，支持复杂的查询表达式，包括对内嵌对象和数组的查询。
- 数据更新：利用 update() 命令，MongoDB 能够替换整个文档或更新指定的数据字段，提供了灵活的数据更新方式。
- MapReduce 批量处理：MongoDB 的 MapReduce 功能专为大规模数据处理和聚合操作设计，通过 Map 函数的 emit(key, value) 调用和 Reduce 函数的逻辑处理，实现高效的数据汇总。
- MapReduce 脚本编写：Map 和 Reduce 函数使用 JavaScript 编写，可以通过 db.runCommand 或 mapreduce 命令在 MongoDB 中执行。
- GridFS 大文件存储：GridFS 是 MongoDB 内置的功能，用于存储和检索大于 BSON 文档大小限制的文件，如图片和视频。
- 服务端脚本执行：MongoDB 允许在服务端执行 JavaScript 脚本，提供了直接在服务端执行或存储函数定义以供后续调用的能力。
- 多语言支持：MongoDB 提供了对多种编程语言的支持，包括但不限于 RUBY、PYTHON、JAVA、C++、PHP 和 C#。
- 安装简单：MongoDB 的安装过程简单直观，便于用户快速部署和使用。


## 历史


## MongoDB 下载

你可以在 MongoDB 官网下载该安装包，地址为：https://www.mongodb.com/try/download/community。

MongoDB 支持以下平台:

- Linux：MongoDB 支持各种 Linux 发行版，包括但不限于 Ubuntu、Debian、CentOS、Red Hat Enterprise Linux（RHEL）、Fedora 等。
- Windows：MongoDB 提供了适用于 Windows 操作系统的官方版本，可以在 Windows Server 和 Windows 桌面操作系统上运行。
- macOS：MongoDB 可以在 macOS 上运行，并且提供了适用于 macOS 的官方安装程序。
- Docker：MongoDB 也可以作为 Docker 容器运行，这使得在各种平台上部署和管理 MongoDB 变得更加便捷。


## 语言支持

MongoDB 有官方的驱动如下：

- C
- C++
- C# / .NET
- Erlang
- Haskell
- Java
- JavaScript
- Lisp
- node.JS
- Perl
- PHP
- Python
- Ruby
- Scala
- Go


## MongoDB 工具

有几种可用于MongoDB的管理工具。


### 监控

MongoDB提供了网络和系统监控工具Munin，它作为一个插件应用于MongoDB中。

Gangila是MongoDB高性能的系统监视的工具，它作为一个插件应用于MongoDB中。

基于图形界面的开源工具 Cacti, 用于查看CPU负载, 网络带宽利用率,它也提供了一个应用于监控 MongoDB 的插件。


### GUI

- Fang of Mongo – 网页式,由Django和jQuery所构成。
- Futon4Mongo – 一个CouchDB Futon web的mongodb山寨版。
- Mongo3 – Ruby写成。
- MongoHub – 适用于OSX的应用程序。
- Opricot – 一个基于浏览器的MongoDB控制台, 由PHP撰写而成。
- Database Master — Windows的mongodb管理工具
- RockMongo — 最好的PHP语言的MongoDB管理工具，轻量级, 支持多国语言.


## MongoDB 应用案例

下面列举一些公司MongoDB的实际应用：

- Craiglist上使用MongoDB的存档数十亿条记录。
- FourSquare，基于位置的社交网站，在Amazon EC2的服务器上使用MongoDB分享数据。
- Shutterfly，以互联网为基础的社会和个人出版服务，使用MongoDB的各种持久性数据存储的要求。
- bit.ly, 一个基于Web的网址缩短服务，使用MongoDB的存储自己的数据。
- spike.com，一个MTV网络的联营公司， spike.com使用MongoDB的。
- Intuit公司，一个为小企业和个人的软件和服务提供商，为小型企业使用MongoDB的跟踪用户的数据。
- sourceforge.net，资源网站查找，创建和发布开源软件免费，使用MongoDB的后端存储。
- etsy.com ，一个购买和出售手工制作物品网站，使用MongoDB。
- 纽约时报，领先的在线新闻门户网站之一，使用MongoDB。
- CERN，著名的粒子物理研究所，欧洲核子研究中心大型强子对撞机的数据使用MongoDB。


## 复习重点

- 能说明 `MongoDB 简介` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
