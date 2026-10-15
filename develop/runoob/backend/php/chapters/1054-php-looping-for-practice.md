# PHP：PHP 循环 - For 循环

- 来源：[PHP For 循环](https://www.runoob.com/php/php-looping-for.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：练习笔记
- 章节序号：1054

## 本章内容

循环执行代码块指定的次数，或者当指定的条件为真时循环执行代码块。


## for 循环

for 循环用于您预先知道脚本需要运行的次数的情况。


### 语法

```java
for (初始值; 条件; 增量)
{
    要执行的代码;
}
```

参数：

- 初始值：主要是初始化一个变量值，用于设置一个计数器（但可以是任何在循环的开始被执行一次的代码）。
- 条件：循环执行的限制条件。如果为 TRUE，则循环继续。如果为 FALSE，则循环结束。
- 增量：主要用于递增计数器（但可以是任何在循环的结束被执行的代码）。

注释：上面的初始值和增量参数可为空，或者有多个表达式（用逗号分隔）。


### 实例

下面的实例定义一个初始值为 i=1 的循环。只要变量 i 小于或者等于 5，循环将继续运行。循环每运行一次，变量 i 就会递增 1：


## 实例

```java
<?php
for ($i=1; $i<=5; $i++)
{
    echo "数字为 " . $i . PHP_EOL;
}
?>
```

输出：

```text
数字为 1
数字为 2
数字为 3
数字为 4
数字为 5
```


## foreach 循环

foreach 循环用于遍历数组。


### 语法

```text
foreach ($array as $value)
{
    要执行代码;
}
```

每进行一次循环，当前数组元素的值就会被赋值给 $value 变量（数组指针会逐一地移动），在进行下一次循环时，您将看到数组中的下一个值。

```text
foreach ($array as $key => $value)
{
    要执行代码;
}
```

每一次循环，当前数组元素的键与值就都会被赋值给 $key 和 $value 变量（数字指针会逐一地移动），在进行下一次循环时，你将看到数组中的下一个键与值。


### 实例

下面的实例演示了一个输出给定数组的值的循环：


## 实例

```text
<?php
$x=array("Google","Runoob","Taobao");
foreach ($x as $value)
{
    echo $value . PHP_EOL;
}
?>
```

输出：

```text
Google
Runoob
Taobao
```

下面的实例演示了一个输出给定数组键与值的循环：


## 实例

```text
<?php
$x=array(1=>"Google", 2=>"Runoob", 3=>"Taobao");
foreach ($x as $key => $value)
{
    echo "key  为 " . $key . "，对应的 value 为 ". $value . PHP_EOL;
}
?>
```

输出：

```text
key  为 1，对应的 value 为 Google
key  为 2，对应的 value 为 Runoob
key  为 3，对应的 value 为 Taobao
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PHP For 循环` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
