# MySQL：MySQL Java 连接与使用

- 来源：[MySQL Java](https://www.runoob.com/mysql/mysql-java-intro.html)
- 分类：数据库
- 技术：MySQL
- 笔记类型：练习笔记
- 章节序号：1547

## 本章内容

MySQL 是最流行的开源关系型数据库之一，而 Java 是企业级应用开发中最常用的编程语言。将 Java 与 MySQL 结合使用，可以构建强大的数据驱动型应用程序。

本文将详细介绍如何在 Java 程序中连接和使用 MySQL 数据库，包括：

本文介绍了 Java 连接和使用 MySQL 数据库的基本步骤，包括：

- 加载 JDBC 驱动
- 建立数据库连接
- 执行 SQL 查询和更新
- 使用 PreparedStatement 防止 SQL 注入
- 事务管理
- 资源关闭
- 最佳实践


## 准备工作


### 下载 MySQL JDBC 驱动

Java 通过 JDBC (Java Database Connectivity) 技术与数据库交互。要连接 MySQL，你需要下载 MySQL Connector/J 驱动：

- 访问 MySQL Connector/J 下载页面
- 选择与你的 Java 版本兼容的驱动版本
- 下载 JAR 文件（如 mysql-connector-java-8.0.xx.jar）


### 将驱动添加到项目

根据你使用的开发工具或构建工具（如 Eclipse、IntelliJ IDEA、Maven 或 Gradle），将下载的 JAR 文件添加到项目的类路径中。


## 建立数据库连接


### 加载驱动程序

在 Java 代码中，首先需要加载 MySQL JDBC 驱动：


## 实例


### 创建连接

使用 DriverManager.getConnection()方法建立与数据库的连接：


## 实例

- jdbc:mysql://localhost:3306/：MySQL 服务器的默认地址和端口
- useSSL=false：禁用 SSL 连接（开发环境）
- serverTimezone=UTC：设置服务器时区，避免时区问题


## 执行 SQL 操作


### 创建 Statement 对象

Statement 对象用于执行静态 SQL 语句：


## 实例


### 执行查询

使用 executeQuery() 方法执行 SELECT 语句：


## 实例


### 执行更新

使用 executeUpdate() 方法执行 INSERT、UPDATE 或 DELETE 语句：


## 实例


### 使用 PreparedStatement

PreparedStatement 可以防止 SQL 注入，提高性能：


## 实例


## 事务管理


### 基本概念


### 事务操作示例


## 实例


## 关闭资源


### 为什么需要关闭资源

数据库连接是有限的资源，使用后必须关闭以避免资源泄漏。


### 如何正确关闭资源


## 后续章节

- 实例
- 6.3 使用 try-with-resources
- 实例
- 最佳实践
- 使用连接池
- 实例
- 处理异常
- 实例
- 7.3 使用 DAO 模式
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MySQL Java` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
