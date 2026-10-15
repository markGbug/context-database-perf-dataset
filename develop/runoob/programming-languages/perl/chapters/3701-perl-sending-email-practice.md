# Perl：Perl 发送邮件

- 来源：[Perl 发送邮件](https://www.runoob.com/perl/perl-sending-email.html)
- 分类：编程语言
- 技术：Perl
- 笔记类型：练习笔记
- 章节序号：3701

## 本章内容

如果你的程序在 Linux/Unix 系统上运行，你就可以在 Perl 中使用 sendmail 工具来发送邮件。

以下是一个简单的脚本实例用于发送邮件：


## 实例

```java
#!/usr/bin/perl

# 接收邮箱，这里我设置为我的 QQ 邮箱，你需要修改它为你自己的邮箱
$to = '429240967@qq.com';
#发送者邮箱
$from = 'test@runoob.com';
#标题
$subject = '菜鸟教程 Perl 发送邮件测试';
$message = '这是一封使用 Perl 发送的邮件。';

open(MAIL, "|/usr/sbin/sendmail -t");

# 邮件头部
print MAIL "To: $to\n";
print MAIL "From: $from\n";
print MAIL "Subject: $subject\n\n";
# 邮箱信息
print MAIL $message;

close(MAIL);
print "邮件发送成功\n";
```

执行以上程序，输出结果为：

```text
邮件发送成功
```

正常情况下，以上邮件会被 QQ 邮箱拦截，我么可以把它加入白名单，操作方式可以点击：https://kf.qq.com/faq/120322fu63YV130805rYRFzu.html

加入白名单后就可以正常接收邮件了。


### 发送 HTML 格式邮件

我们可以在邮件头部添加 Content-type: text/html\n 来发送 HTML 格式的邮件，实例如下：


## 实例

```java
#!/usr/bin/perl

# 接收邮箱，这里我设置为我的 QQ 邮箱，你需要修改它为你自己的邮箱
$to = '429240967@qq.com';
#发送者邮箱
$from = 'test@runoob.com';
#标题
$subject = '菜鸟教程 Perl 发送邮件测试';
$message = '<h1>这是一封使用 Perl 发送的邮件<h1><p>你好，我来自菜鸟教程，地址是:http://www.runoob.com。</p>';

open(MAIL, "|/usr/sbin/sendmail -t");

# 邮件头部
print MAIL "To: $to\n";
print MAIL "From: $from\n";
print MAIL "Subject: $subject\n";
print MAIL "Content-type: text/html\n";
# 邮箱信息
print MAIL $message;

close(MAIL);
print "邮件发送成功\n";
```

执行成功后，查看邮件内容，如下所示：


## 使用 MIME::Lite 模块

如果你使用的是 window 系统，没有 sendmail 工具。这时你就可以使用 perl 的 MIME:Lite 模块作为邮件客户端来发送邮件。

MIME:Lite 模块 下载地址为：MIME-Lite-3.030.tar.gz。

这里我们直接用 cpan 来安装(需要 root 权限)，不用下载：

```text
$ cpan -i MIME::Lite
……
  /usr/bin/make install  -- OK
```

安装成功后，我们来演示一个实例：


## 实例

```java
#!/usr/bin/perl
use MIME::Lite;

# 接收邮箱，这里我设置为我的 QQ 邮箱，你需要修改它为你自己的邮箱
$to = '429240967@qq.com';
# 抄送者，多个使用逗号隔开
# $cc = 'test1@runoob.com, test2@runoob.com';

#发送者邮箱
$from = 'test@runoob.com';
#标题
$subject = '菜鸟教程 Perl 发送邮件测试';
$message = '这是一封使用 Perl 发送的邮件，使用了 MIME::Lite 模块。';

$msg = MIME::Lite->new(
                 From     => $from,
                 To       => $to,
                 Cc       => $cc,
                 Subject  => $subject,
                 Data     => $message
                 );

$msg->send;
print "邮件发送成功\n";
```

执行成功后，查看邮件内容，如下所示：


### 发送 HTML 格式邮件

我们可以在邮件头部添加 Content-type: text/html\n 来发送 HTML 格式的邮件，实例如下：


## 实例

```java
#!/usr/bin/perl
use MIME::Lite;

# 接收邮箱，这里我设置为我的 QQ 邮箱，你需要修改它为你自己的邮箱
$to = '429240967@qq.com';
# 抄送者，多个使用逗号隔开
# $cc = 'test1@runoob.com, test2@runoob.com';

#发送者邮箱
$from = 'test@runoob.com';
#标题
$subject = '菜鸟教程 Perl 发送邮件测试';
$message = '<h1>这是一封使用 Perl 发送的邮件<h1><p>使用了 MIME::Lite 模块。</p><p>来自菜鸟教程，地址是:http://www.runoob.com。</p>';

$msg = MIME::Lite->new(
                 From     => $from,
                 To       => $to,
                 Cc       => $cc,
                 Subject  => $subject,
                 Data     => $message
                 );

# 添加头部信息
$msg->attr("content-type" => "text/html");
$msg->send;
print "邮件发送成功\n";
```

执行成功后，查看邮件内容，如下所示：


### 发送带有附件的邮件

发送带有附件的邮件实例如下：


## 实例

```java
#!/usr/bin/perl
use MIME::Lite;

# 接收邮箱，这里我设置为我的 QQ 邮箱，你需要修改它为你自己的邮箱
$to = '429240967@qq.com';
# 抄送者，多个使用逗号隔开
# $cc = 'test1@runoob.com, test2@runoob.com';

#发送者邮箱
$from = 'test@runoob.com';
#标题
$subject = '菜鸟教程 Perl 发送邮件测试';
$message = '这是一封使用 Perl 发送的邮件，使用了 MIME::Lite 模块，包含了附件。';

$msg = MIME::Lite->new(
                 From     => $from,
                 To       => $to,
                 Cc       => $cc,
                 Subject  => $subject,
                 Type     => 'multipart/mixed'   # 附件标记
                 );


$msg->attach (
              Type => 'TEXT',
              Data => $message
);# 指定附件信息
$msg->attach(Type        => 'TEXT',
             Path        => './runoob.txt',   # 当前目录下
             Filename    => 'runoob.txt',
             Disposition => 'attachment'
            );
$msg->send;
print "邮件发送成功\n";
```

执行成功后，查看邮件内容，如下所示：

你可以通过使用多个 $msg->attach 来添加多个附件。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Perl 发送邮件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
