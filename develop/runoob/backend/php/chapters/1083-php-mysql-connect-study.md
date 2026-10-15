# PHP：PHP 连接 MySQL

- 来源：[PHP MySQL 连接](https://www.runoob.com/php/php-mysql-connect.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：学习笔记
- 章节序号：1083

## 本章内容

PHP 5 及以上版本建议使用以下方式连接 MySQL :

- MySQLi extension ("i" 意为 improved)
- PDO (PHP Data Objects)

在 PHP 早期版本中我们使用 MySQL 扩展。但该扩展在 2012 年开始不建议使用。


## 我是该用 MySQLi ，还是 PDO?

如果你需要一个简短的回答，即 "你习惯哪个就用哪个"。

MySQLi 和 PDO 有它们自己的优势：

PDO 应用在 12 种不同数据库中， MySQLi 只针对 MySQL 数据库。

所以，如果你的项目需要在多种数据库中切换，建议使用 PDO ，这样你只需要修改连接字符串和部分查询语句即可。 使用 MySQLi, 如果不同数据库，你需要重新编写所有代码，包括查询。

两者都是面向对象, 但 MySQLi 还提供了 API 接口。

两者都支持预处理语句。 预处理语句可以防止 SQL 注入，对于 web 项目的安全性是非常重要的。


## MySQLi 和 PDO 连接 MySQL 实例

在本章节及接下来的章节中，我们会使用以下三种方式来演示 PHP 操作 MySQL:

- MySQLi (面向对象)
- MySQLi (面向过程)
- PDO


## MySQLi 安装

Linux 和 Windows: 在 php5 mysql 包安装时 MySQLi 扩展多数情况下是自动安装的。

安装详细信息，请查看： http://php.net/manual/en/mysqli.installation.php

可以通过 phpinfo() 查看是否安装成功：


## PDO 安装

For 安装详细信息，请查看： http://php.net/manual/en/pdo.installation.php

可以通过 phpinfo() 查看是否安装成功：


## 连接 MySQL

在我们访问 MySQL 数据库前，我们需要先连接到数据库服务器：


## 实例 (MySQLi - 面向对象)

```text
<?php
$servername = "localhost";
$username = "username";
$password = "password";

// 创建连接
$conn = new mysqli($servername, $username, $password);

// 检测连接
if ($conn->connect_error) {
    die("连接失败: " . $conn->connect_error);
}
echo "连接成功";
?>
```


## 实例 (MySQLi - 面向过程)

```text
<?php
$servername = "localhost";
$username = "username";
$password = "password";

// 创建连接
$conn = mysqli_connect($servername, $username, $password);

// 检测连接
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}
echo "连接成功";
?>
```


## 实例 (PDO)

```text
<?php
$servername = "localhost";
$username = "username";
$password = "password";

try {
    $conn = new PDO("mysql:host=$servername;", $username, $password);
    echo "连接成功";
}
catch(PDOException $e)
{
    echo $e->getMessage();
}
?>
```


## 关闭连接

连接在脚本执行完后会自动关闭。你也可以使用以下代码来关闭连接：


## 实例 (MySQLi - 面向对象)


## 实例 (MySQLi - 面向过程)


## 实例 (PDO)


## 复习重点

- 能说明 `PHP MySQL 连接` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
