# PHP：PHP 数组

- 来源：[PHP 数组](https://www.runoob.com/php/php-arrays.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：学习笔记
- 章节序号：1050

## 本章内容

数组能够在单个变量中存储多个值：


## 实例

```text
<?php
$cars=array("Volvo","BMW","Toyota");
echo "I like " . $cars[0] . ", " . $cars[1] . " and " . $cars[2] . ".";
?>
```


## 数组是什么？

数组是一个能在单个变量中存储多个值的特殊变量。

如果您有一个项目清单（例如：车名字的清单），将其存储到单个变量中，如下所示：

然而，如果您想要遍历数组并找出特定的一个呢？如果数组的项不只 3 个而是 300 个呢？

解决办法是创建一个数组！

数组可以在单个变量中存储多个值，并且您可以根据键访问其中的值。


## 在 PHP 中创建数组

在 PHP 中，array() 函数用于创建数组：

在 PHP 中，有三种类型的数组：

- 数值数组 - 带有数字 ID 键的数组
- 关联数组 - 带有指定的键的数组，每个键关联一个值
- 多维数组 - 包含一个或多个数组的数组


## PHP 数值数组

这里有两种创建数值数组的方法：

自动分配 ID 键（ID 键总是从 0 开始）：

人工分配 ID 键：

下面的实例创建一个名为 $cars 的数值数组，并给数组分配三个元素,然后打印一段包含数组值的文本：


## 实例

```text
<?php
$cars=array("Volvo","BMW","Toyota");
echo "I like " . $cars[0] . ", " . $cars[1] . " and " . $cars[2] . ".";
?>
```


## 获取数组的长度 - count() 函数

count() 函数用于返回数组的长度（元素的数量）：


## 实例

```text
<?php
$cars=array("Volvo","BMW","Toyota");
echo count($cars);
?>
```


## 遍历数值数组

遍历并打印数值数组中的所有值，您可以使用 for 循环，如下所示：


## 实例

```java
<?php
$cars=array("Volvo","BMW","Toyota");
$arrlength=count($cars);

for($x=0;$x<$arrlength;$x++)
{
    echo $cars[$x];
    echo "<br>";
}
?>
```


## PHP 关联数组

关联数组是使用您分配给数组的指定的键的数组。

这里有两种创建关联数组的方法：

or:

随后可以在脚本中使用指定的键：


## 实例

```text
<?php
$age=array("Peter"=>"35","Ben"=>"37","Joe"=>"43");
echo "Peter is " . $age['Peter'] . " years old.";
?>
```


## 遍历关联数组

遍历并打印关联数组中的所有值，您可以使用 foreach 循环，如下所示：


## 实例

```html
<?php
$age=array("Peter"=>"35","Ben"=>"37","Joe"=>"43");

foreach($age as $x=>$x_value)
{
    echo "Key=" . $x . ", Value=" . $x_value;
    echo "<br>";
}
?>
```


## 多维数组

多维数组 将在 PHP 高级教程部分做详细介绍。


## 完整的 PHP Array 参考手册

如需查看所有数组函数的完整参考手册，请访问我们的 PHP Array 参考手册。

该参考手册提供了每个函数的简要描述和应用实例！


## 复习重点

- 能说明 `PHP 数组` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
