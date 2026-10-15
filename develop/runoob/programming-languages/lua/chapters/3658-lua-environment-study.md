# Lua：Lua 环境安装

- 来源：[Lua 环境安装](https://www.runoob.com/lua/lua-environment.html)
- 分类：编程语言
- 技术：Lua
- 笔记类型：学习笔记
- 章节序号：3658

## 本章内容

## Linux 系统上安装

Linux & Mac 上安装 Lua 安装非常简单，只需要下载源码包并在终端解压编译即可，本文使用了 5.4.7 版本进行安装：


### 源码安装

下载源码安装：

```text
curl -L -R -O https://www.lua.org/ftp/lua-5.4.7.tar.gz
tar zxf lua-5.4.7.tar.gz
cd lua-5.4.7
make all test
make install
```


### 使用包管理器安装

Debian/Ubuntu 系统:

```text
sudo apt update
sudo apt install lua5.3
```

CentOS/RHEL 系统:

```text
sudo yum install epel-release
sudo yum install lua
```


## 复习重点

- 能说明 `Lua 环境安装` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
