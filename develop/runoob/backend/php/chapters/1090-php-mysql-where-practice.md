# PHP：PHP MySQL Where 子句

- 来源：[PHP MySQL Where](https://www.runoob.com/php/php-mysql-where.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：练习笔记
- 章节序号：1090

## 本章内容

WHERE 子句用于过滤记录。


## WHERE 子句

WHERE 子句用于提取满足指定标准的的记录。


### 语法

```text
SELECT column_name(s)
FROM table_name
WHERE column_name operator value
```

如需学习更多关于 SQL 的知识，请访问我们的 SQL 教程。

为了让 PHP 执行上面的语句，我们必须使用 mysqli_query() 函数。该函数用于向 MySQL 连接发送查询或命令。


### 实例

下面的实例将从 "Persons" 表中选取所有 FirstName='Peter' 的行：

```java
<?php
$con=mysqli_connect("localhost","username","password","database");
// 检测连接
if (mysqli_connect_errno())
{
    echo "连接失败: " . mysqli_connect_error();
}

$result = mysqli_query($con,"SELECT * FROM Persons
WHERE FirstName='Peter'");

while($row = mysqli_fetch_array($result))
{
    echo $row['FirstName'] . " " . $row['LastName'];
    echo "<br>";
}
?>
```

以上代码将输出：

```text
Peter Griffin
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PHP MySQL Where` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
