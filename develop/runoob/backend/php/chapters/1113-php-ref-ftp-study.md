# PHP：PHP FTP 函数

- 来源：[PHP FTP](https://www.runoob.com/php/php-ref-ftp.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：学习笔记
- 章节序号：1113

## 本章内容

## PHP FTP 简介

FTP 函数通过文件传输协议 (FTP) 提供对文件服务器的客户端访问。

FTP 函数用于打开、登录以及关闭连接，同时用于上传、下载、重命名、删除及获取文件服务器上的文件信息。不是所有的 FTP 函数对每个服务器都起作用或返回相同的结果。自 PHP 3 起，FTP 函数可用。

这些函数用于对 FTP 服务器进行细致的访问。如果您仅仅需要对 FTP 服务器进行读写操作，建议使用 Filesystem 函数中的 ftp:// wrapper。


## 安装

PHP 的 Windows 版本内置了对 FTP 扩展的支持。无需加载任何附加扩展库即可使用 FTP 函数。

然而，如果您运行的是 PHP 的 Linux 版本，在编译 PHP 的时候请添加 --enable-ftp 选项（PHP4 或以上版本）或者 --with-ftp 选项（PHP3 版本）。


## PHP FTP 函数

PHP：指示支持该函数的最早的 PHP 版本。


## PHP FTP 常量

PHP：指示支持该常量的最早的 PHP 版本。


## 复习重点

- 能说明 `PHP FTP` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
