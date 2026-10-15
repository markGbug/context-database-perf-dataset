# Perl：Perl 数组

- 来源：[Perl 数组](https://www.runoob.com/perl/perl-arrays.html)
- 分类：编程语言
- 技术：Perl
- 笔记类型：学习笔记
- 章节序号：3687

## 本章内容

Perl 数组一个是存储标量值的列表变量，变量可以是不同类型。

数组变量以 @ 开头。访问数组元素使用 $ + 变量名称 + [索引值] 格式来读取，实例如下：


## 实例

```java
#!/usr/bin/perl

@hits = (25, 30, 40);
@names = ("google", "runoob", "taobao");

print "\$hits[0] = $hits[0]\n";
print "\$hits[1] = $hits[1]\n";
print "\$hits[2] = $hits[2]\n";
print "\$names[0] = $names[0]\n";
print "\$names[1] = $names[1]\n";
print "\$names[2] = $names[2]\n";
```

程序中 $ 符号使用了 \ 来转义，让他原样输出。

执行以上程序，输出结果为：

```text
$hits[0] = 25
$hits[1] = 30
$hits[2] = 40
$names[0] = google
$names[1] = runoob
$names[2] = taobao
```


## 创建数组

数组变量以 @ 符号开始，元素放在括号内，也可以以 qw 开始定义数组。

```text
@array = (1, 2, 'Hello');
@array = qw/这是 一个 数组/;
```

第二个数组使用 qw// 运算符，它返回字符串列表，数组元素以空格分隔。当然也可以使用多行来定义数组：

```text
@days = qw/google
taobao
...
runoob/;
```

你也可以按索引来给数组赋值，如下所示：

```text
$array[0] = 'Monday';
...
$array[6] = 'Sunday';
```


## 访问数组元素

访问数组元素使用 $ + 变量名称 + [索引值] 格式来读取，实例如下：


## 实例

```java
@sites = qw/google taobao runoob/;

print "$sites[0]\n";
print "$sites[1]\n";
print "$sites[2]\n";
print "$sites[-1]\n";    # 负数，反向读取
```

执行以上程序，输出结果为：

```text
google
taobao
runoob
runoob
```

数组索引值从 0 开始，即 0 为第一个元素，1 为第二个元素，以此类推。


## 复习重点

- 能说明 `Perl 数组` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
