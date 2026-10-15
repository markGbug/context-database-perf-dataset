# Docker：Docker 安装 Ubuntu

- 来源：[Docker 安装 Ubuntu](https://www.runoob.com/docker/docker-install-ubuntu.html)
- 分类：后端开发
- 技术：Docker
- 笔记类型：练习笔记
- 章节序号：0810

## 本章内容

Ubuntu 是基于 Debian 的 Linux 操作系统。


### 1、查看可用的 Ubuntu 版本

访问 Ubuntu 镜像库地址： https://hub.docker.com/_/ubuntu?tab=tags&page=1。

可以通过 Sort by 查看其他版本的 Ubuntu。默认是最新版本 ubuntu:latest 。

你也可以在下拉列表中找到其他你想要的版本：


### 2、拉取最新版的 Ubuntu 镜像

```text
$ docker pull ubuntu
```

或者：

```text
$ docker pull ubuntu:latest
```


### 3、查看本地镜像

```text
$ docker images
```

在上图中可以看到我们已经安装了最新版本的 ubuntu。


### 4、运行容器，并且可以通过 exec 命令进入 ubuntu 容器

```text
$ docker run -itd --name ubuntu-test ubuntu
```


### 5、安装成功

最后我们可以通过 docker ps 命令查看容器的运行信息：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Docker 安装 Ubuntu` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
