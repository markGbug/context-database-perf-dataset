# PHP：PHP 安装

- 来源：[PHP 安装](https://www.runoob.com/php/php-install.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：练习笔记
- 章节序号：1038

## 本章内容

## 您需要做什么？

为了开始使用 PHP，您可以：

- 找一个支持 PHP 和 MySQL 的 Web 主机
- 在您自己的 PC 机上安装 Web 服务器，然后安装 PHP 和 MySQL


## 使用支持 PHP 的 Web 主机

如果您的服务器支持 PHP，那么您不需要做任何事情。

只要在您的 web 目录中创建 .php 文件即可，服务器将自动为您解析这些文件。

您不需要编译任何软件，或安装额外的工具。

由于 PHP 是免费的，大多数的 Web 主机都提供对 PHP 的支持。


## 在您自己的 PC 机上建立 PHP

然而，如果您的服务器不支持 PHP，您必须：

- 安装 Web 服务器
- 安装 PHP
- 安装数据库，比如 MySQL

官方 PHP 网站（PHP.net）有 PHP 的安装说明： https://www.php.net/manual/zh/install.php


## PHP 服务器组件

对于初学者建议使用集成的服务器组件，它已经包含了 PHP、Apache、Mysql 等服务,免去了开发人员将时间花费在繁琐的配置环境过程。


### WampServer

Windows 系统可以使用 WampServer，下载地址：https://www.wampserver.com/en/，支持32位和64位系统，根据自己的系统选择版本。

WampServer 安装也简单，你只需要一直点击 "Next" 就可以完成安装了。


### XAMPP

XAMPP 支持 Mac OS 和 Windows 系统，下载地址：https://www.apachefriends.org/zh_cn/index.html。


## IDE (Integrated Development Environment,集成开发环境)


### VS Code

VS Code（全称 Visual Studio Code）是一款由微软推出的免费、开源、跨平台的代码编辑器。

VS Code 支持 Windows、macOS 和 Linux，拥有强大的功能和灵活的扩展性。

VS Code 教程：https://www.runoob.com/vscode/vscode-tutorial.html

另外国内阿里与字节也有基于 VS Code 开发的 AI IDE：

- 字节 Trae：https://www.trae.cn/
- 阿里 Qoder：https://qoder.com/


### Eclipse for PHP（免费）

Eclipse 是一个开放源代码的、基于Java的可扩展开发平台(如果未安装JDK，则需要先 下载 JDK 安装)。就其本身而言，它只是一个框架和一组服务，用于通过插件组件构建开发环境。幸运的是，Eclipse 附带了一个标准的插件集，包括Java开发工具（Java Development Kit，JDK）。

支持 Windows、Linux 和 Mac OS 平台。

Eclipse for PHP 官方下载地址：https://www.eclipse.org/downloads/packages/


### PhpStorm（收费）

PhpStorm是一个轻量级且便捷的PHP IDE，其旨在提供用户效率，可深刻理解用户的编码，提供智能代码补全，快速导航以及即时错误检查。

PhpStorm 非常适合于PHP开发人员及前端工程师。提供诸于：智能HTML/CSS/JavaScript/PHP编辑、代码质量分析、版本控制集成（SVN、GIT）、调试和测试等功能。

支持 Windows、Linux 和 Mac OS 平台。

PhpStorm 官方下载地址：http://www.jetbrains.com/phpstorm/download/


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PHP 安装` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
