# PHP：PHP cURL 函数

- 来源：[PHP cURL](https://www.runoob.com/php/php-ref-curl.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：练习笔记
- 章节序号：1107

## 本章内容

## 概述

PHP支持的由Daniel Stenberg创建的libcurl库允许你与各种的服务器使用各种类型的协议进行连接和通讯。

libcurl目前支持http、https、ftp、gopher、telnet、dict、file和ldap协议。libcurl同时也支持HTTPS认证、HTTP POST、HTTP PUT、 FTP 上传(这个也能通过PHP的FTP扩展完成)、HTTP 基于表单的上传、代理、cookies和用户名+密码的认证。

PHP中使用cURL实现Get和Post请求的方法

这些函数在PHP 4.0.2中被引入。


## 需求

为了使用 PHP 的 cURL函数，你需要安装 libcurl 包。

PHP需要使用libcurl 7.0.2-beta 或者更高版本。在PHP 4.2.3 里使用cURL，你需要安装7.9.0或更高版本的libcurl。从PHP 4.3.0开始你需要安装7.9.0或更高版本的libcurl。从PHP 5.0.0开始你需要安装7.10.5或更高版本的libcurl。


## 安装

要使用PHP的cURL支持你必须在编译PHP时加上--with-curl[=DIR] 选项，DIR为包含lib和include的目录路径。在include目录中必须有一个名为curl，包含了easy.h和curl.h的文件夹。lib文件夹里应该有一个名为libcurl.a的文件。对于PHP 4.3.0你可以配置--with-curlwrappers 使cURL使用URL流。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PHP cURL` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
