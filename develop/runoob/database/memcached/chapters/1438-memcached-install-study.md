# Memcached：Linux Memcached 安装

- 来源：[Linux Memcached 安装](https://www.runoob.com/memcached/memcached-install.html)
- 分类：数据库
- 技术：Memcached
- 笔记类型：学习笔记
- 章节序号：1438

## 本章内容

Memcached 支持许多平台：Linux、FreeBSD、Solaris、Mac OS，也可以安装在Windows上。

Linux系统安装memcached，首先要先安装libevent库。

```text
sudo apt-get install libevent ibevent-dev         自动下载安装（Ubuntu/Debian）

yum install libevent libevent-devel                    自动下载安装（Redhat/Fedora/Centos）
```


## 安装 Memcached


### 自动安装

Ubuntu/Debian

```text
sudo apt-get install memcached
```

Redhat/Fedora/Centos

```text
yum install memcached
```

FreeBSD

```text
portmaster databases/memcached
```

安装完后可以使用 whereis 查看命令的路径：

```text
whereis memcached
```

发现安装位置在 /usr/bin/memcached。


### 源代码安装

从其官方网站（http://memcached.org）下载memcached最新版本。

```text
wget http://memcached.org/latest                    下载最新版本

tar -zxvf memcached-1.x.x.tar.gz                    解压源码

cd memcached-1.x.x                                  进入目录

./configure --prefix=/usr/local/memcached           配置

make && make test                                   编译

sudo make install                                   安装
```


## Memcached 运行

Memcached命令的运行：

```text
$ /usr/local/memcached/bin/memcached -h                           命令帮助
```


## 复习重点

- 能说明 `Linux Memcached 安装` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
