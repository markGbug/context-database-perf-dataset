# Perl：Perl 条件语句

- 来源：[Perl 条件语句](https://www.runoob.com/perl/perl-conditions.html)
- 分类：编程语言
- 技术：Perl
- 笔记类型：学习笔记
- 章节序号：3689

## 本章内容

Perl 条件语句是通过一条或多条语句的执行结果（True或者False）来决定执行的代码块。

可以通过下图来简单了解条件语句的执行过程:

注意，数字 0, 字符串 '0' 、 "" , 空 list() , 和 undef 为 false ，其他值均为 true。 true 前面使用 ! 或 not则返回 false 。

Perl 提供了下列条件语句：

if 语句

if...else 语句

if...elsif...else 语句

unless 语句

unless...else 语句。

unless...elsif..else statement

switch 语句


## 三元运算符 ? :

我们可以使用 条件运算 ? : 来简化 if...else 语句的操作。通常格式为：

```text
Exp1 ? Exp2 : Exp3;
```

如果 Exp1 表达式为 true ，则返回 Exp2 表达式计算结果，否则返回 Exp3。

实例如下所示：


## 实例

```java
#!/usr/local/bin/perl

$name = "菜鸟教程";
$favorite = 10;     # 喜欢数

$status = ($favorite > 60 )? "热门网站" : "不是热门网站";

print "$name - $status\n";
```

执行以上程序，输出结果为：

```text
菜鸟教程 - 不是热门网站
```


## 复习重点

- 能说明 `Perl 条件语句` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
