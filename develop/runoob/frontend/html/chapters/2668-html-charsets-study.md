# HTML：HTML 字符集

- 来源：[HTML 字符集](https://www.runoob.com/charsets/html-charsets.html)
- 分类：前端开发
- 技术：HTML
- 笔记类型：学习笔记
- 章节序号：2668

## 本章内容

要正确显示一个 HTML 页面，浏览器必须知道要使用的字符集（字符编码）。


## HTML 字符集

在 HTML 中，正确的字符编码是什么？

HTML5 中默认的字符编码是 UTF-8。

这并非总是如此。早期网络的字符编码是 ASCII 码。

后来，从 HTML 2.0 到 HTML 4.01，ISO-8859-1 被认定为标准。

随着 XML 和 HTML5 的出现，UTF-8 也终于到来了，解决了大量的字符编码问题。

下面是关于字符编码标准的简短概述。


## 在开始的时候：ASCII

计算机信息（数字、文字、图片）在电子中是以二进制 1 和 0（01000101）进行存储的。

为了规范字母数字字符的存储，创建了 ASCII（全称 American Standard Code for Information Interchange）。它为每个存储字符定义了一个独特的二元 7 位数字，支持 0-9 数字，大/小写英文字母（a-z、A-Z）和一些特殊的字符，比如 ! $ + - ( ) @ < > 。

由于 ASCII 使用一个字节（7 位表示字符，1 位表示传输奇偶控制），所以它只能表示 128 个不同的字符。这些字符中有 32 个被保留作为其他控制目的使用。

ASCII 的最大的缺点是，它排除了非英文字母。

ASCII 今天仍然在广泛使用，尤其是在大型计算机系统中。

如需深入了解 ASCII，请查看完整的 ASCII 参考手册。


## 在 Windows 中：ANSI

ANSI（也称为 Windows-1252），是 Windows 95 及其之前的 Windows 系统中默认的字符集。

ANSI 是 ASCII 的扩展，它加入了国际字符。它使用一个完整的字节（8 位）来表示 256 个不同字符。

自从 ANSI 成为 Windows 中默认的字符集，所有的浏览器都支持 ANSI。

如需深入了解 ANSI，请查看完整的 ANSI 参考手册。


## 在 HTML 4 中：ISO-8859-1

由于大多数国家使用 ASCII 以外的字符，在 HTML 2.0 标准中，默认的字符编码更改为 ISO-8859-1。

ISO-8859-1 是 ASCII 的扩展，它加入了国际字符。与 ANSI 一样，它使用一个完整的字节（8 位）来表示 256 个不同字符。

如果 HTML 4 网页使用了不同于 ISO-8859-1 的字符集，则需要在 <meta> 标签中指定，如下所示：


## 实例

```html
<meta http-equiv="Content-Type" content="text/html;charset=ISO-8859-8">
```

HTML5 中默认的字符集是 UTF-8。 所有的 HTML 4 处理器都支持 UTF-8，所有的 HTML5 和 XML 处理器都支持 UTF-8 和 UTF-16。

如需深入了解 ISO-8859-1，请查看完整的 ISO-8859-1 参考手册。


## 在 HTML5 中：Unicode（UTF-8）

由于以上所列的字符集是有限的，在多语言环境中是不兼容的，所以 Unicode 联盟（Unicode Consortium）开发了 Unicode 标准（Unicode Standard）。

Unicode 标准覆盖了（几乎）所有的字符、标点符号和符号。

Unicode 使文本的处理、存储和运输，独立于平台和语言。

HTML5 中默认的字符编码是 UTF-8。

如需深入了解 Unicode（UTF-8），请查看完整的 Unicode 参考手册。


## 复习重点

- 能说明 `HTML 字符集` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
