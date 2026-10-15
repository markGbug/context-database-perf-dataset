# Perl：Perl 正则表达式

- 来源：[Perl 正则表达式](https://www.runoob.com/perl/perl-regular-expressions.html)
- 分类：编程语言
- 技术：Perl
- 笔记类型：练习笔记
- 章节序号：3700

## 本章内容

正则表达式(regular expression)描述了一种字符串匹配的模式，可以用来检查一个串是否含有某种子串、将匹配的子串做替换或者从某个串中取出符合某个条件的子串等。

Perl语言的正则表达式功能非常强大，基本上是常用语言中最强大的，很多语言设计正则式支持的时候都参考Perl的正则表达式。

Perl的正则表达式的三种形式，分别是匹配，替换和转化:

- 匹配：m//（还可以简写为//，略去m）
- 替换：s///
- 转化：tr///

这三种形式一般都和 =~ 或 !~ 搭配使用， =~ 表示相匹配，!~ 表示不匹配。


## 匹配操作符

匹配操作符 m// 用于匹配一个字符串语句或者一个正则表达式，例如，要匹配 标量 $bar 中的 "run",代码如下所示：


## 实例

```java
#!/usr/bin/perl

$bar = "I am runoob site. welcome to runoob site.";
if ($bar =~ /run/){
   print "第一次匹配\n";
}else{
   print "第一次不匹配\n";
}

$bar = "run";
if ($bar =~ /run/){
   print "第二次匹配\n";
}else{
   print "第二次不匹配\n";
}
```

执行以上程序，输出结果为：

```text
第一次匹配
第二次匹配
```


### 模式匹配修饰符

模式匹配有一些常用的修饰符，如下表所示：


## 正则表达式变量

perl处理完后会给匹配到的值存在三个特殊变量名:

- $`: 匹配部分的前一部分字符串
- $&: 匹配的字符串
- $': 还没有匹配的剩余字符串

如果将这三个变量放在一起,你将得到原始字符串。

实例如下：


## 实例

```java
#!/usr/bin/perl

$string = "welcome to runoob site.";
$string =~ m/run/;
print "匹配前的字符串: $`\n";
print "匹配的字符串: $&\n";
print "匹配后的字符串: $'\n";
```

执行以上程序输出结果为：

```text
匹配前的字符串: welcome to
匹配的字符串: run
匹配后的字符串: oob site.
```


## 替换操作符

替换操作符 s/// 是匹配操作符的扩展，使用新的字符串替换指定的字符串。基本格式如下：

```text
s/PATTERN/REPLACEMENT/;
```

PATTERN 为匹配模式，REPLACEMENT 为替换的字符串。

例如我们将以下字符串的 "google" 替换为 "runoob":


## 实例

```java
#!/usr/bin/perl

$string = "welcome to google site.";
$string =~ s/google/runoob/;

print "$string\n";
```

执行以上程序输出结果为：

```text
welcome to runoob site.
```


### 替换操作修饰符

替换操作修饰符如下表所示：


## 转化操作符

以下是转化操作符相关的修饰符：

以下实例将变量 $string 中的所有小写字母转化为大写字母：


## 实例

```java
#!/usr/bin/perl

$string = 'welcome to runoob site.';
$string =~ tr/a-z/A-Z/;

print "$string\n";
```

执行以上程序输出结果为：

```text
WELCOME TO RUNOOB SITE.
```

以下实例使用 /s 将变量 $string 重复的字符删除：


## 实例

```java
#!/usr/bin/perl

$string = 'runoob';
$string =~ tr/a-z/a-z/s;

print "$string\n";
```

执行以上程序输出结果为：

```text
runob
```

更多实例：

```text
$string =~ tr/\d/ /c;     # 把所有非数字字符替换为空格
$string =~ tr/\t //d;     # 删除tab和空格
$string =~ tr/0-9/ /cs    # 把数字间的其它字符替换为一个空格。
```


## 更多正则表达式规则


### 更多参考内容

正则表达式：https://www.runoob.com/regexp/regexp-tutorial.html

Perl 正则表达式：https://perldoc.perl.org/perlre#Regular-Expressions


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Perl 正则表达式` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
