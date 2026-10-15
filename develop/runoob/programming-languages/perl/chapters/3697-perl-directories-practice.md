# Perl：Perl 目录操作

- 来源：[Perl 目录操作](https://www.runoob.com/perl/perl-directories.html)
- 分类：编程语言
- 技术：Perl
- 笔记类型：练习笔记
- 章节序号：3697

## 本章内容

以下列出了一些操作目录的标准函数：

```text
opendir DIRHANDLE, EXPR  # 打开目录
readdir DIRHANDLE        # 读取目录
rewinddir DIRHANDLE      # 定位指针到开头
telldir DIRHANDLE        # 返回目录的当前位置
seekdir DIRHANDLE, POS   # 定位指定到目录的 POS 位置
closedir DIRHANDLE       # 关闭目录
```


## 显示所有的文件

显示目录下的所有文件，以下实例使用了 glob 操作符，演示如下：


## 实例

```java
#!/usr/bin/perl

# 显示 /tmp 目录下的所有文件
$dir = "/tmp/*";
my @files = glob( $dir );

foreach (@files ){
   print $_ . "\n";
}

# 显示 /tmp 目录下所有以 .c 结尾的文件
$dir = "/tmp/*.c";
@files = glob( $dir );

foreach (@files ){
   print $_ . "\n";
}

# 显示所有隐藏文件
$dir = "/tmp/.*";
@files = glob( $dir );
foreach (@files ){
   print $_ . "\n";
}

# 显示 /tmp 和 /home 目录下的所有文件
$dir = "/tmp/* /home/*";
@files = glob( $dir );

foreach (@files ){
   print $_ . "\n";
}
```

以下实例可以列出当前目录下的所有文件：


## 实例

```java
#!/usr/bin/perl

opendir (DIR, '.') or die "无法打开目录, $!";
while ($file = readdir DIR) {
  print "$file\n";
}
closedir DIR;
```

如果你要显示 /tmp 目录下所有以 .c 结尾的文件，可以使用以下代码：


## 实例

```java
#!/usr/bin/perl

opendir(DIR, '.') or die "无法打开目录, $!";
foreach (sort grep(/^.*\.c$/,readdir(DIR))){
   print "$_\n";
}
closedir DIR;
```


## 创建一个新目录

我们可以使用 mkdir 函数来创建一个新目录，执行前你需要有足够的权限来创建目录：


## 实例

```java
#!/usr/bin/perl

$dir = "/tmp/perl";

# 在 /tmp 目录下创建 perl 目录
mkdir( $dir ) or die "无法创建 $dir 目录, $!";
print "目录创建成功\n";
```


## 删除目录

我们可以使用 rmdir 函数来删除目录，执行该操作需要有足够权限。另外要删除的目录必须的空目录：


## 实例

```java
#!/usr/bin/perl

$dir = "/tmp/perl";

# 删除 /tmp 目录下的 perl 目录
rmdir( $dir ) or die "无法删除 $dir 目录, $!";
print "目录删除成功\n";
```


## 切换目录

我们可以使用chdir 函数来切换当期目录，执行该操作需要有足够权限。实例如下：


## 实例

```java
#!/usr/bin/perl

$dir = "/home";

# 将当期目录移动到 /home 目录下
chdir( $dir ) or die "无法切换目录到 $dir , $!";
print "你现在所在的目录为 $dir\n";
```

执行以上程序，输出结果为：

```text
你现在所在的目录为 /home
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Perl 目录操作` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
