# MySQL：MySQL 选择数据库

- 来源：[MySQL 选择数据库](https://www.runoob.com/mysql/mysql-select-database.html)
- 分类：数据库
- 技术：MySQL
- 笔记类型：练习笔记
- 章节序号：1513

## 本章内容

在你连接到 MySQL 数据库后，可能有多个可以操作的数据库，所以你需要选择你要操作的数据库。


## 从命令提示窗口中选择 MySQL 数据库

在 mysql> 提示窗口中可以很简单的选择特定的数据库。

在 MySQL 中，要选择要使用的数据库，可以使用 USE 语句，以下是基本的语法：

```text
USE database_name;
```

参数说明：

- database_name 是你要选择的数据库的名称。

选择来数据库后，你的后续 SQL 查询和操作在指定的数据库 database_name 上执行。


### 实例

以下实例选取了数据库 RUNOOB:

```text
[root@host]# mysql -u root -p
Enter password:******
mysql> use RUNOOB;
Database changed
mysql>
```

执行以上命令后，你就已经成功选择了 RUNOOB 数据库，在后续的操作中都会在 RUNOOB 数据库中执行。

在命令行中，你可以通过以下方式选择数据库：

```text
mysql -u your_username -p -D your_database
```

- -D 参数用于指定要选择的数据库。

例如：

```text
mysql -u root -p -D RUNOOB
```

在输入密码后，你将进入 MySQL 提示符，并且任何后续的查询和操作都将在 RUNOOB 数据库上执行。

请确保选择的数据库存在，否则你将收到错误消息。你可以使用 SHOW DATABASES; 查询可用的数据库，确保你要选择的数据库在列表中。


## 使用 PHP 脚本选择 MySQL 数据库

PHP 提供了函数 mysqli_select_db 来选取一个数据库。函数在执行成功后返回 TRUE ，否则返回 FALSE 。


### 语法

```text
mysqli_select_db(connection,dbname);
```


### 实例

以下实例展示了如何使用 mysqli_select_db 函数来选取一个数据库：


## 选择数据库

```text
<?php
$dbhost = 'localhost';  // mysql服务器主机地址
$dbuser = 'root';            // mysql用户名
$dbpass = '123456';          // mysql用户名密码
$conn = mysqli_connect($dbhost, $dbuser, $dbpass);
if(! $conn )
{
    die('连接失败: ' . mysqli_error($conn));
}
echo '连接成功';
mysqli_select_db($conn, 'RUNOOB' );
mysqli_close($conn);
?>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MySQL 选择数据库` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
