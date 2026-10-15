# Perl：Perl CGI编程

- 来源：[Perl CGI编程](https://www.runoob.com/perl/perl-cgi-programming.html)
- 分类：编程语言
- 技术：Perl
- 笔记类型：学习笔记
- 章节序号：3705

## 本章内容

## 什么是CGI

CGI 目前由NCSA维护，NCSA定义CGI如下：

CGI(Common Gateway Interface),通用网关接口,它是一段程序,运行在服务器上如：HTTP服务器，提供同客户端HTML页面的接口。


## 网页浏览

为了更好的了解CGI是如何工作的，我们可以从在网页上点击一个链接或URL的流程：

- 1、使用你的浏览器访问URL并连接到HTTP web 服务器。
- 2、Web服务器接收到请求信息后会解析URL，并查找访问的文件在服务器上是否存在，如果存在返回文件的内容，否则返回错误信息。
- 3、浏览器从服务器上接收信息，并显示接收的文件或者错误信息。

CGI程序可以是Python脚本，PERL脚本，SHELL脚本，C或者C++程序等。


## CGI架构图


## Web服务器支持及配置

在你进行CGI编程前，确保您的Web服务器支持CGI及已经配置了CGI的处理程序。

Apache 支持CGI 配置：

设置好CGI目录：

```text
ScriptAlias /cgi-bin/ /var/www/cgi-bin/
```

所有的HTTP服务器执行CGI程序都保存在一个预先配置的目录。这个目录被称为CGI目录，并按照惯例，它被命名为/var/www/cgi-bin目录。

CGI文件的扩展名为.cgi，Perl 也可以使用.pl扩展名。

默认情况下，Linux服务器配置运行的cgi-bin目录中为/var/www。

如果你想指定其他运行CGI脚本的目录，可以修改httpd.conf配置文件，如下所示：

```html
<Directory "/var/www/cgi-bin">
   AllowOverride None
   Options +ExecCGI
   Order allow,deny
   Allow from all
</Directory>
```

在 AddHandler 中添加 .pl 后缀，这样我们就可以访问 .pl 结尾的 Perl 脚本文件：

```text
AddHandler cgi-script .cgi .pl .py
```


### 第一个 CGI 程序

以下我们创建一个 test.cgi 文件，代码如下所示：


## test.cgi 代码

```java
#!/usr/bin/perl

print "Content-type:text/html\r\n\r\n";
print '<html>';
print '<head>';
print '<meta charset="utf-8">';
print '<title>菜鸟教程(runoob.com)</title>';
print '</head>';
print '<body>';
print '<h2>Hello Word! </h2>';
print '<p>来自菜鸟教程第一个 CGI 程序。</p>';
print '</body>';
print '</html>';

1;
```

然后通过浏览器打开 http://localhost/cgi-bin/test.cgi，输出结果如下：

脚本第一行的输出内容"Content-type:text/html\r\n\r\n"发送到浏览器并告知浏览器显示的内容类型为"text/html"。


## HTTP头部

test.cgi文件内容中的" Content-type:text/html"即为HTTP头部的一部分，它会发送给浏览器告诉浏览器文件的内容类型。

HTTP头部的格式如下：

```text
HTTP 字段名: 字段内容
```

例如：

```text
Content-type:text/html\r\n\r\n
```

以下表格介绍了CGI程序中HTTP头部经常使用的信息：


## CGI环境变量

所有的CGI程序都接收以下的环境变量，这些变量在CGI程序中发挥了重要的作用：

以下是一个简单的CGI脚本输出CGI的环境变量：


## 实例

```java
#!/usr/bin/perl

print "Content-type: text/html\n\n";
print '<meta charset="utf-8">';
print "<font size=+1>环境变量：</font>\n";
foreach (sort keys %ENV)
{
  print "<b>$_</b>: $ENV{$_}<br>\n";
}

1;
```


## 文件下载

如果我们想通过 Perl CGI 实现文件下载，需要设置不同的头部信息，如下所示：


## 实例

```java
#!/usr/bin/perl

# HTTP Header
print "Content-Type:application/octet-stream; name=\"FileName\"\r\n";
print "Content-Disposition: attachment; filename=\"FileName\"\r\n\n";

# Actual File Content will go hear.
open( FILE, "<FileName" );
while(read(FILE, $buffer, 100) )
{
   print("$buffer");
}
```


## 使用GET方法传输数据

GET方法发送编码后的用户信息到服务端，数据信息包含在请求页面的URL上，以"?"号分割, 如下所示：

```text
http://www.test.com/cgi-bin/test.cgi?key1=value1&key2=value2
```

- GET 请求可被缓存
- GET 请求保留在浏览器历史记录中
- GET 请求可被收藏为书签
- GET 请求不应在处理敏感数据时使用
- GET 请求有长度限制
- GET 请求只应当用于取回数据


### 简单的url实例：GET方法

以下是一个简单的URL，使用GET方法向test.cgi程序发送两个参数：

```text
/cgi-bin/test.cgi?name=菜鸟教程&url=http://www.runoob.com
```

以下为test.cgi文件的代码：


## 实例

```java
#!/usr/bin/perl

local ($buffer, @pairs, $pair, $name, $value, %FORM);
# 读取文本信息
$ENV{'REQUEST_METHOD'} =~ tr/a-z/A-Z/;
if ($ENV{'REQUEST_METHOD'} eq "GET")
{
   $buffer = $ENV{'QUERY_STRING'};
}
# 读取 name/value 对信息
@pairs = split(/&/, $buffer);
foreach $pair (@pairs)
{
   ($name, $value) = split(/=/, $pair);
   $value =~ tr/+/ /;
   $value =~ s/%(..)/pack("C", hex($1))/eg;
   $FORM{$name} = $value;
}
$name = $FORM{name};
$url  = $FORM{url};

print "Content-type:text/html\r\n\r\n";
print "<html>";
print "<head>";
print '<meta charset="utf-8">';
print '<title>菜鸟教程(runoob.com)</title>';
print "</head>";
print "<body>";
print "<h2>$name网址：$url</h2>";
print "</body>";
print "</html>";

1;
```

查看浏览器，输出结果如下：


### 简单的表单实例：GET方法

以下是一个通过HTML的表单使用GET方法向服务器发送两个数据，提交的服务器脚本同样是test.cgi文件，test.html 代码如下：


## test.html 文件代码

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
<form action="/cgi-bin/test.cgi" method="get">
站点名称: <input type="text" name="name">  <br />

站点 URL: <input type="text" name="url" />
<input type="submit" value="提交" />
</form>
</body>
</html>
```

浏览器中，执行效果如下所示：


## 使用POST方法传递数据

使用POST方法向服务器传递数据是更安全可靠的，像一些敏感信息如用户密码等需要使用POST传输数据。

以下同样是 test.cgi ，它也可以处理浏览器提交的POST表单数据:


## test.cgi 代码

```java
#!/usr/bin/perl

local ($buffer, @pairs, $pair, $name, $value, %FORM);
# 读取文本信息
$ENV{'REQUEST_METHOD'} =~ tr/a-z/A-Z/;
if ($ENV{'REQUEST_METHOD'} eq "POST")
{
   read(STDIN, $buffer, $ENV{'CONTENT_LENGTH'});
}else {
   $buffer = $ENV{'QUERY_STRING'};
}
# 读取 name/value 对信息
@pairs = split(/&/, $buffer);
foreach $pair (@pairs)
{
   ($name, $value) = split(/=/, $pair);
   $value =~ tr/+/ /;
   $value =~ s/%(..)/pack("C", hex($1))/eg;
   $FORM{$name} = $value;
}
$name = $FORM{name};
$url  = $FORM{url};

print "Content-type:text/html\r\n\r\n";
print "<html>";
print "<head>";
print '<meta charset="utf-8">';
print '<title>菜鸟教程(runoob.com)</title>';
print "</head>";
print "<body>";
print "<h2>$name网址：$url</h2>";
print "</body>";
print "</html>";

1;
```

以下是一个通过HTML的表单使用GET方法向服务器发送两个数据，提交的服务器脚本同样是test.cgi文件，test.html 代码如下：


## test.html 代码

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
<form action="/cgi-bin/test.cgi" method="post">
站点名称: <input type="text" name="name">  <br />

站点 URL: <input type="text" name="url" />
<input type="submit" value="提交" />
</form>
</body>
</html>
```

浏览器中，执行效果如下所示：


### 通过CGI程序传递checkbox数据

checkbox用于提交一个或者多个选项数据，test.html 代码如下：


## test.html 代码

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
<form action="/cgi-bin/test.cgi" method="POST" target="_blank">
<input type="checkbox" name="runoob" value="on" /> 菜鸟教程
<input type="checkbox" name="google" value="on" /> Google
<input type="submit" value="选择站点" />
</form>
</body>
</html>
```

以下为 test.cgi 文件的代码：


## test.cgi 代码

```java
#!/usr/bin/perl

local ($buffer, @pairs, $pair, $name, $value, %FORM);
# 读取信息
$ENV{'REQUEST_METHOD'} =~ tr/a-z/A-Z/;
if ($ENV{'REQUEST_METHOD'} eq "POST")
{
   read(STDIN, $buffer, $ENV{'CONTENT_LENGTH'});
}else {
   $buffer = $ENV{'QUERY_STRING'};
}
# 读取 name/value 对信息
@pairs = split(/&/, $buffer);
foreach $pair (@pairs)
{
   ($name, $value) = split(/=/, $pair);
   $value =~ tr/+/ /;
   $value =~ s/%(..)/pack("C", hex($1))/eg;
   $FORM{$name} = $value;
}
if( $FORM{runoob} ){
   $runoob_flag ="ON";
}else{
   $runoob_flag ="OFF";
}
if( $FORM{google} ){
   $google_flag ="ON";
}else{
   $google_flag ="OFF";
}

print "Content-type:text/html\r\n\r\n";
print "<html>";
print "<head>";
print '<meta charset="utf-8">';
print '<title>菜鸟教程(runoob.com)</title>';
print "</head>";
print "<body>";
print "<h2> 菜鸟教程选中状态 : $runoob_flag</h2>";
print "<h2> Google 选择状态 : $google_flag</h2>";
print "</body>";
print "</html>";

1;
```

浏览器中，执行效果如下所示：


## 复习重点

- 能说明 `Perl CGI编程` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
