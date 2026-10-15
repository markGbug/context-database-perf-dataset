# Node.js：Node.js JXcore 打包

- 来源：[Node.js JXcore 打包](https://www.runoob.com/nodejs/nodejs-jxcore-packaging.html)
- 分类：后端开发
- 技术：Node.js
- 笔记类型：学习笔记
- 章节序号：1032

## 本章内容

Node.js 是一个开放源代码、跨平台的、用于服务器端和网络应用的运行环境。

JXcore 是一个支持多线程的 Node.js 发行版本，基本不需要对你现有的代码做任何改动就可以直接线程安全地以多线程运行。

这篇文章主要是要向大家介绍 JXcore 的打包功能。


## JXcore 安装

下载 JXcore 安装包，并解压，在解压的的目录下提供了 jx 二进制文件命令，接下来我们主要使用这个命令。


### 步骤1、下载

下载 JXcore 安装包 https://github.com/jxcore/jxcore-release，你需要根据你自己的系统环境来下载安装包。

1、Window 平台下载：Download(Windows x64 (V8))。

2、Linux/OSX 安装命令：

```text
$ curl https://raw.githubusercontent.com/jxcore/jxcore/master/tools/jx_install.sh | bash
```

如果权限不足，可以使用以下命令：

```text
$ curl https://raw.githubusercontent.com/jxcore/jxcore/master/tools/jx_install.sh | sudo bash
```

以上步骤如果操作正确，使用以下命令，会输出版本号信息：

```text
$ jx --version
v0.10.32
```


## 包代码

例如，我们的 Node.js 项目包含以下几个文件，其中 index.js 是主文件：

```text
drwxr-xr-x  2 root root  4096 Nov 13 12:42 images
-rwxr-xr-x  1 root root 30457 Mar  6 12:19 index.htm
-rwxr-xr-x  1 root root 30452 Mar  1 12:54 index.js
drwxr-xr-x 23 root root  4096 Jan 15 03:48 node_modules
drwxr-xr-x  2 root root  4096 Mar 21 06:10 scripts
drwxr-xr-x  2 root root  4096 Feb 15 11:56 style
```

接下来我们使用 jx 命令打包以上项目，并指定 index.js 为 Node.js 项目的主文件：

```text
$ jx package index.js index
```


## 复习重点

- 能说明 `Node.js JXcore 打包` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
