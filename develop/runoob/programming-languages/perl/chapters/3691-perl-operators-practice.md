# Perl：Perl 运算符

- 来源：[Perl 运算符](https://www.runoob.com/perl/perl-operators.html)
- 分类：编程语言
- 技术：Perl
- 笔记类型：练习笔记
- 章节序号：3691

## 本章内容

运算符是一种告诉编译器执行特定的数学或逻辑操作的符号，如: 3+2=5。

Perl 语言内置了丰富的运算符，我们来看下常用的几种：

- 算术运算符
- 比较运算符
- 逻辑运算符
- 赋值运算符
- 位运算符
- 引号运算符
- 其他运算符
- 运算符优先级


## 算术运算符

表格实例中我们设置变量 $a 为 10， $b 为 20。


## 实例

```java
#!/usr/bin/perl

$a = 10;
$b = 20;

print "\$a = $a , \$b = $b\n";

$c = $a + $b;
print '$a + $b = ' . $c . "\n";

$c = $a - $b;
print '$a - $b = ' . $c . "\n";

$c = $a * $b;
print '$a * $b = ' . $c . "\n";

$c = $a / $b;
print '$a / $b = ' . $c . "\n";

$c = $a % $b;
print '$a % $b = ' . $c. "\n";

$a = 2;
$b = 4;
$c = $a ** $b;
print '$a ** $b = ' . $c . "\n";
```

以上程序执行输出结果为：

```text
$a = 10 , $b = 20
$a + $b = 30
$a - $b = -10
$a * $b = 200
$a / $b = 0.5
$a % $b = 10
$a ** $b = 16
```


## 比较运算符

表格实例中我们设置变量 $a 为 10， $b 为 20。


## 实例

```java
#!/usr/bin/perl

$a = 10;
$b = 20;

print "\$a = $a , \$b = $b\n";

if( $a == $b ){
   print "$a == \$b 结果 true\n";
}else{
   print "\$a == \$b 结果 false\n";
}

if( $a != $b ){
   print "\$a != \$b 结果 true\n";
}else{
   print "\$a != \$b 结果 false\n";
}

$c = $a <=> $b;
print "\$a <=> \$b 返回 $c\n";

if( $a > $b ){
   print "\$a > \$b 结果 true\n";
}else{
   print "\$a > \$b 结果 false\n";
}

if( $a >= $b ){
   print "\$a >= \$b 结果 true\n";
}else{
   print "\$a >= \$b 结果 false\n";
}

if( $a < $b ){
   print "\$a < \$b 结果 true\n";
}else{
   print "\$a < \$b 结果 false\n";
}

if( $a <= $b ){
   print "\$a <= \$b 结果 true\n";
}else{
   print "\$a <= \$b 结果 false\n";
}
```

以上程序执行输出结果为：

```text
$a = 10 , $b = 20
$a == $b 结果 false
$a != $b 结果 true
$a <=> $b 返回 -1
$a > $b 结果 false
$a >= $b 结果 false
$a < $b 结果 true
$a <= $b 结果 true
```

以下表格实例中设置变量 $a 为 "abc" ， $b 为 "xyz" ，然后使用比较运算符来计算结果。


## 实例

```java
#!/usr/bin/perl

$a = "abc";
$b = "xyz";

print "\$a = $a ，\$b = $b\n";

if( $a lt $b ){
   print "$a lt \$b 返回 true\n";
}else{
   print "\$a lt \$b 返回 false\n";
}

if( $a gt $b ){
   print "\$a gt \$b 返回 true\n";
}else{
   print "\$a gt \$b 返回 false\n";
}

if( $a le $b ){
   print "\$a le \$b 返回 true\n";
}else{
   print "\$a le \$b 返回 false\n";
}

if( $a ge $b ){
   print "\$a ge \$b 返回 true\n";
}else{
   print "\$a ge \$b 返回 false\n";
}

if( $a ne $b ){
   print "\$a ne \$b 返回 true\n";
}else{
   print "\$a ne \$b 返回 false\n";
}

$c = $a cmp $b;
print "\$a cmp \$b 返回 $c\n";
```

以上程序执行输出结果为：

```text
$a = abc ，$b = xyz
abc lt $b 返回 true
$a gt $b 返回 false
$a le $b 返回 true
$a ge $b 返回 false
$a ne $b 返回 true
$a cmp $b 返回 -1
```


## 赋值运算符

表格实例中我们设置变量 $a 为 10， $b 为 20。


## 实例

```java
#!/usr/bin/perl

$a = 10;
$b = 20;

print "\$a = $a ，\$b = $b\n";

$c = $a + $b;
print "赋值后 \$c = $c\n";

$c += $a;
print "\$c = $c ，运算语句 \$c += \$a\n";

$c -= $a;
print "\$c = $c ，运算语句 \$c -= \$a\n";

$c *= $a;
print "\$c = $c ，运算语句 \$c *= \$a\n";

$c /= $a;
print "\$c = $c ，运算语句 \$c /= \$a\n";

$c %= $a;
print "\$c = $c ，运算语句 \$c %= \$a\n";

$c = 2;
$a = 4;
print "\$a = $a ， \$c = $c\n";
$c **= $a;
print "\$c = $c ，运算语句 \$c **= \$a\n";
```

以上程序执行输出结果为：

```text
$a = 10 ，$b = 20
赋值后 $c = 30
$c = 40 ，运算语句 $c += $a
$c = 30 ，运算语句 $c -= $a
$c = 300 ，运算语句 $c *= $a
$c = 30 ，运算语句 $c /= $a
$c = 0 ，运算语句 $c %= $a
$a = 4 ， $c = 2
$c = 16 ，运算语句 $c **= $a
```


## 位运算

位运算符作用于位，并逐位执行操作。

设置 $a = 60，$b = 13，现在以二进制格式表示，它们如下所示：

```text
$a = 0011 1100

$b = 0000 1101

-----------------

$a&$b = 0000 1100

$a|$b = 0011 1101

$a^$b = 0011 0001

~$a  = 1100 0011
```

Perl 支持的位运算符如下表所示：


## 实例

```java
#!/usr/bin/perl

use integer;

$a = 60;
$b = 13;

print "\$a = $a , \$b = $b\n";

$c = $a & $b;
print "\$a & \$b = $c\n";

$c = $a | $b;
print "\$a | \$b = $c\n";

$c = $a ^ $b;
print "\$a ^ \$b = $c\n";

$c = ~$a;
print "~\$a = $c\n";

$c = $a << 2;
print "\$a << 2 = $c\n";

$c = $a >> 2;
print "\$a >> 2 = $c\n";
```

以上程序执行输出结果为：

```text
$a = 60 , $b = 13
$a & $b = 12
$a | $b = 61
$a ^ $b = 49
~$a = -61
$a << 2 = 240
$a >> 2 = 15
```


## 逻辑运算符

Perl 逻辑运算符如下表所示。

表格实例中我们设置变量 $a 为 true, $b 为 false。


## 实例

```java
#!/usr/bin/perl

$a = true;
$b = false;

print "\$a = $a , \$b = $b\n";

$c = ($a and $b);
print "\$a and \$b = $c\n";

$c = ($a  && $b);
print "\$a && \$b = $c\n";

$c = ($a or $b);
print "\$a or \$b = $c\n";

$c = ($a || $b);
print "\$a || \$b = $c\n";

$a = 0;
$c = not($a);
print "not(\$a)= $c\n";
```

以上程序执行输出结果为：

```text
$a = true , $b = false
$a and $b = false
$a && $b = false
$a or $b = true
$a || $b = true
not($a)= 1
```


## 引号运算

Perl 引号运算符如下表所示。


## 实例

```java
#!/usr/bin/perl

$a = 10;

$b = q{a = $a};
print "q{a = \$a} = $b\n";

$b = qq{a = $a};
print "qq{a = \$a} = $b\n";

# 使用 unix 的 date 命令执行
$t = qx{date};
print "qx{date} = $t\n";
```

以上程序执行输出结果为：

```text
q{a = $a} = a = $a
qq{a = $a} = a = 10
qx{date} = 2016年 6月10日 星期五 16时22分33秒 CST
```


## 其他运算符

除了以上我们提到的运算符外，Perl 还支持以下运算符：


## 实例

```java
#!/usr/bin/perl

$a = "run";
$b = "oob";

print "\$a  = $a ， \$b = $b\n";

$c = $a . $b;
print "\$a . \$b = $c\n";

$c = "-" x 3;
print "\"-\" x 3 = $c\n";

@c = (2..5);
print "(2..5) = @c\n";

$a = 10;
$b = 15;
print "\$a  = $a ， \$b = $b\n";

$a++;
$c = $a ;
print "\$a 执行 \$a++ = $c\n";

$b--;
$c = $b ;
print "\$b 执行 \$b-- = $c\n";
```

以上程序执行输出结果为：

```text
$a  = run ， $b = oob
$a . $b = runoob
"-" x 3 = ---
(2..5) = 2 3 4 5
$a  = 10 ， $b = 15
$a 执行 $a++ = 11
$b 执行 $b-- = 14
```


## 运算符优先级

下表列出了 Perl 语言的运算符优先级：


## 实例

```java
#!/usr/bin/perl

$a = 20;
$b = 10;
$c = 15;
$d = 5;
$e;

print "\$a  = $a, \$b = $b, \$c = $c ，\$d = $d\n";

$e = ($a + $b) * $c / $d;
print "(\$a + \$b) * \$c / \$d  = $e\n";

$e = (($a + $b) * $c )/ $d;
print "((\$a + \$b) * \$c) / \$d  = $e\n";

$e = ($a + $b) * ($c / $d);
print "(\$a + \$b) * (\$c / \$d )  = $e\n";

$e = $a + ($b * $c ) / $d;
print "\$a + (\$b * \$c )/ \$d  = $e\n";
```

以上程序执行输出结果为：

```text
$a  = 20, $b = 10, $c = 15 ，$d = 5
($a + $b) * $c / $d  = 90
(($a + $b) * $c) / $d  = 90
($a + $b) * ($c / $d )  = 90
$a + ($b * $c )/ $d  = 50
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Perl 运算符` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
