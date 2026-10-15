# PHP：PHP MySQL 创建数据库

- 来源：[PHP MySQL 创建数据库](https://www.runoob.com/php/php-mysql-create.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：学习笔记
- 章节序号：1084

## 本章内容

数据库存有一个或多个表。

你需要 CREATE 权限来创建或删除 MySQL 数据库。


## 使用 MySQLi 和 PDO 创建 MySQL 数据库

CREATE DATABASE 语句用于在 MySQL 中创建数据库。

在下面的实例中，创建了一个名为 "myDB" 的数据库：


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

// 创建数据库
$sql = "CREATE DATABASE myDB";
if ($conn->query($sql) === TRUE) {
    echo "数据库创建成功";
} else {
    echo "Error creating database: " . $conn->error;
}

$conn->close();
?>
```


## 实例 (MySQLi Procedural)

```text
<?php
$servername = "localhost";
$username = "username";
$password = "password";

// 创建连接
$conn = mysqli_connect($servername, $username, $password);
// 检测连接
if (!$conn) {
    die("连接失败: " . mysqli_connect_error());
}

// 创建数据库
$sql = "CREATE DATABASE myDB";
if (mysqli_query($conn, $sql)) {
    echo "数据库创建成功";
} else {
    echo "Error creating database: " . mysqli_error($conn);
}

mysqli_close($conn);
?>
```

注意： 以下使用 PDO 实例创建数据库 myDBPDO :


## 实例

使用 PDO：

提示： 使用 PDO 的最大好处是在数据库查询过程出现问题时可以使用异常类来 处理问题。如果 try{ } 代码块出现异常，脚本会停止执行并会跳到第一个 catch(){ } 代码块执行代码。 在以上捕获的代码块中我们输出了 SQL 语句并生成错误信息。


## 复习重点

- 能说明 `PHP MySQL 创建数据库` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
