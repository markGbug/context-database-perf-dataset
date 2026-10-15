# HTML：HTML URL 编码 参考手册

- 来源：[HTML URL 编码](https://www.runoob.com/tags/html-urlencode.html)
- 分类：前端开发
- 技术：HTML
- 笔记类型：学习笔记
- 章节序号：2672

## 本章内容

URL 编码会将字符转换为可通过因特网传输的格式。


## URL - 统一资源定位器

Web 浏览器通过 URL 从 web 服务器请求页面。

URL 是网页的地址，比如： https://www.runoob.com。


## URL 编码

URL 只能使用 ASCII 字符集来通过因特网进行发送。

由于 URL 常常会包含 ASCII 集合之外的字符，URL 必须转换为有效的 ASCII 格式。

URL 编码使用 "%" 其后跟随两位的十六进制数来替换非 ASCII 字符。

URL 不能包含空格。URL 编码通常使用 + 来替换空格。


## 尝试一下

如果您点击下面的"提交"按钮，浏览器会在发送输入之前对其进行 URL 编码。服务器上的页面会显示出接收到的输入。

试着输入一些其他字符，然后再次点击提交按钮。


## URL 编码函数

JavaScript、PHP、ASP 都提供了对字符串进行URL编码的函数。

JavaScript 中使用 encodeURI() 函数，PHP 中使用 rawurlencode() 函数，ASP 中使用 Server.URLEncode() 函数。

点击"URL 编码"按钮，看看 JavaScript 函数是怎么对文本进行编码的。

注释：JavaScript 函数将空格编码成 %20 。


## URL 编码参考手册

ASCII 设备控制字符最初被设计为用来控制诸如打印机和磁带驱动器之类的硬件设备。在URL中这些字符不会起任何作用。


## 复习重点

- 能说明 `HTML URL 编码` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
