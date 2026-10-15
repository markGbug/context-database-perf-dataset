# PHP：PHP MySQL Order By 关键词

- 来源：[PHP MySQL Order By](https://www.runoob.com/php/php-mysql-order-by.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：练习笔记
- 章节序号：1091

## 本章内容

ORDER BY 关键词用于对记录集中的数据进行排序。


## ORDER BY 关键词

ORDER BY 关键词用于对记录集中的数据进行排序。

ORDER BY 关键词默认对记录进行升序排序。

如果你想降序排序，请使用 DESC 关键字。


### 语法

```text
SELECT column_name(s)
FROM table_name
ORDER BY column_name(s) ASC|DESC
```

如需学习更多关于 SQL 的知识，请访问我们的 SQL 教程。


### 实例

下面的实例选取 "Persons" 表中存储的所有数据，并根据 "Age" 列对结果进行排序：

```java
<?php
$con=mysqli_connect("localhost","username","password","database");
// 检测连接
if (mysqli_connect_errno())
{
    echo "连接失败: " . mysqli_connect_error();
}

$result = mysqli_query($con,"SELECT * FROM Persons ORDER BY age");

while($row = mysqli_fetch_array($result))
{
    echo $row['FirstName'];
    echo " " . $row['LastName'];
    echo " " . $row['Age'];
    echo "<br>";
}

mysqli_close($con);
?>
```

以上结果将输出：

```text
Glenn Quagmire 33
Peter Griffin 35
```


## 根据两列进行排序

可以根据多个列进行排序。当按照多个列进行排序时，只有第一列的值相同时才使用第二列：

```text
SELECT column_name(s)
FROM table_name
ORDER BY column1, column2
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PHP MySQL Order By` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
