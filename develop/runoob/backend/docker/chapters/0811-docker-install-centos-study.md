# Docker：Docker 安装 CentOS

- 来源：[Docker 安装 Centos](https://www.runoob.com/docker/docker-install-centos.html)
- 分类：后端开发
- 技术：Docker
- 笔记类型：学习笔记
- 章节序号：0811

## 本章内容

CentOS（Community Enterprise Operating System）是 Linux 发行版之一，它是来自于 Red Hat Enterprise Linux(RHEL) 依照开放源代码规定发布的源代码所编译而成。由于出自同样的源代码，因此有些要求高度稳定性的服务器以 CentOS 替代商业版的 Red Hat Enterprise Linux 使用。


### 1、查看可用的 CentOS 版本

访问 CentOS 镜像库地址：https://hub.docker.com/_/centos?tab=tags&page=1。

可以通过 Sort by 查看其他版本的 CentOS 。默认是最新版本 centos:latest 。

你也可以在下拉列表中找到其他你想要的版本：


### 2、拉取指定版本的 CentOS 镜像，这里我们安装指定版本为例(centos7):

```text
$ docker pull centos:centos7
```


### 3、查看本地镜像

使用以下命令来查看是否已安装了 centos7：

```text
$ docker images
```


### 4、运行容器，并且可以通过 exec 命令进入 CentOS 容器。

```text
$ docker run -itd --name centos-test centos:centos7
```


### 5、安装成功

最后我们可以通过 docker ps 命令查看容器的运行信息：


## 复习重点

- 能说明 `Docker 安装 Centos` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
