# SVN：SVN 安装

- 来源：[SVN 安装](https://www.runoob.com/svn/svn-install.html)
- 分类：DevOps / 工程化
- 技术：SVN
- 笔记类型：练习笔记
- 章节序号：1883

## 本章内容

## 在windows下安装 SVN

1、准备svn的安装文件

下载地址：https://sourceforge.net/projects/win32svn/

2、下载完成后，在相应的盘符中会有一个Setup-Subversion-1.8.16.msi的文件，目前最新的版本是1.8.16， 这里就使用这个版本。然后双击安装文件进行安装。我们指定安装在D:\Program Files (x86)\Subversion目录里。

3、查看目录结构

把svn安装目录里的bin目录添加到path路径中，在命令行窗口中输入 svnserve --help ,查看安装正常与否。

至此，windows下的SVN安装完成


## 在CentOS下安装 SVN

大多数 GNU/Linux 发行版系统自带了Subversion ，所以它很有可能已经安装在你的系统上了。可以使用下面命令检查是否安装了。

```text
svn --version
```

如果 Subversion 客户端没有安装，命令将报告svn命令找不到的错误。

```text
[runoob@centos6 ~]$ svn --version
bash: svn: command not found
```

我们可以使用 yum install subversion 命令进行安装。

```text
[runoob@centos6 root]$ su -
密码：
[root@centos6 ~]# yum install subversion
已加载插件：fastestmirror, security
设置安装进程
Loading mirror speeds from cached hostfile
 * base: mirrors.aliyun.com
 * epel: mirrors.neusoft.edu.cn
 * extras: mirrors.zju.edu.cn
 * updates: mirrors.aliyun.com
解决依赖关系
--> 执行事务检查
...
```

安装成功之后，执行 svn --version 命令。

```text
[root@centos6 ~]# svn --version
svn，版本 1.6.11 (r934486)
   编译于 Aug 17 2015，08:37:43
```

至此，centos下的SVN安装完成。


## 在Ubuntu下安装 SVN

如果 Subversion 客户端没有安装，命令将报告svn命令找不到的错误。

```text
root@runoob:~# svn --version
The program 'svn' is currently not installed. You can install it by typing:
apt-get install subversion
```

我们可以使用 apt-get 命令进行安装

```text
root@runoob:~# apt-get install subversion
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  augeas-lenses hiera libaugeas0 libxslt1.1 ruby-augeas ruby-deep-merge ruby-json ruby-nokogiri ruby-rgen ruby-safe-yaml ruby-selinux ruby-shadow
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libserf-1-1 libsvn1
...
```

安装成功之后，执行 svn --version 命令。

```text
root@runoob:~# svn --version
svn, version 1.8.13 (r1667537)
   compiled Sep  8 2015, 14:59:01 on x86_64-pc-linux-gnu
```

至此，Ubuntu下的SVN安装完成。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SVN 安装` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
