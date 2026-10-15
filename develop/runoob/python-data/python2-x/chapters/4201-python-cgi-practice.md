# Python2.x：Python CGI 编程

- 来源：[Python CGI 编程](https://www.runoob.com/python/python-cgi.html)
- 分类：Python / 数据科学
- 技术：Python2.x
- 笔记类型：练习笔记
- 章节序号：4201

## 本章内容

## 什么是 CGI

CGI 目前由 NCSA 维护，NCSA 定义 CGI 如下：

CGI(Common Gateway Interface)，通用网关接口，它是一段程序，运行在服务器上如：HTTP 服务器，提供同客户端 HTML 页面的接口。

注意：

自 Python 3.11 起，cgi 模块被官方标记为"弃用"（Deprecated），从 Python 3.13 开始被移除。

推荐迁移到 Flask、Django 或 FastAPI 等现代 Web 框架。


## 网页浏览

为了更好的了解 CGI 是如何工作的，我们可以从在网页上点击一个链接或 URL 的流程：

- 1、使用你的浏览器访问 URL 并连接到 HTTP web 服务器。
- 2、Web 服务器接收到请求信息后会解析 URL，并查找访问的文件在服务器上是否存在，如果存在返回文件的内容，否则返回错误信息。
- 3、浏览器从服务器上接收信息，并显示接收的文件或者错误信息。

CGI 程序可以是 Python 脚本，PERL 脚本，SHELL 脚本，C 或者 C++ 程序等。


## CGI架构图


## Web 服务器支持及配置

在你进行 CGI 编程前，确保您的 Web 服务器支持 CGI 及已经配置了 CGI 的处理程序。

Apache 支持 CGI 配置：

设置好CGI目录：

```text
ScriptAlias /cgi-bin/ /var/www/cgi-bin/
```

所有的HTTP服务器执行 CGI 程序都保存在一个预先配置的目录。这个目录被称为 CGI 目录，并按照惯例，它被命名为 /var/www/cgi-bin 目录。

CGI 文件的扩展名为 .cgi，python 也可以使用 .py 扩展名。

默认情况下，Linux 服务器配置运行的 cgi-bin 目录中为 /var/www。

如果你想指定其他运行 CGI 脚本的目录，可以修改 httpd.conf 配置文件，如下所示：

```html
<Directory "/var/www/cgi-bin">
   AllowOverride None
   Options +ExecCGI
   Order allow,deny
   Allow from all
</Directory>
```

在 AddHandler 中添加 .py 后缀，这样我们就可以访问 .py 结尾的 python 脚本文件：

```text
AddHandler cgi-script .cgi .pl .py
```


## 第一个CGI程序

我们使用 Python 创建第一个 CGI 程序，文件名为 hello.py，文件位于 /var/www/cgi-bin 目录中，内容如下：

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-

print "Content-type:text/html"
print                               # 空行，告诉服务器结束头部
print '<html>'
print '<head>'
print '<meta charset="utf-8">'
print '<title>Hello World - 我的第一个 CGI 程序！</title>'
print '</head>'
print '<body>'
print '<h2>Hello World! 我是来自菜鸟教程的第一CGI程序</h2>'
print '</body>'
print '</html>'
```

文件保存后修改 hello.py，修改文件权限为 755：

```text
chmod 755 hello.py
```

以上程序在浏览器访问 http://localhost/cgi-bin/hello.py 显示结果如下：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python CGI 编程` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
