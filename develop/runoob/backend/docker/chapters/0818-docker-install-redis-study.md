# Docker：Docker 安装 Redis

- 来源：[Docker 安装 Redis](https://www.runoob.com/docker/docker-install-redis.html)
- 分类：后端开发
- 技术：Docker
- 笔记类型：学习笔记
- 章节序号：0818

## 本章内容

Redis 是一个开源的使用 ANSI C 语言编写、支持网络、可基于内存亦可持久化的日志型、Key-Value 的 NoSQL 数据库，并提供多种语言的 API。


### 1、查看可用的 Redis 版本

访问 Redis 镜像库地址： https://hub.docker.com/_/redis?tab=tags。

可以通过 Sort by 查看其他版本的 Redis，默认是最新版本 redis:latest。

你也可以在下拉列表中找到其他你想要的版本：

此外，我们还可以用 docker search redis 命令来查看可用版本：

```text
$ docker search  redis
NAME                      DESCRIPTION                   STARS  OFFICIAL  AUTOMATED
redis                     Redis is an open source ...   2321   [OK]
sameersbn/redis                                         32                   [OK]
torusware/speedus-redis   Always updated official ...   29             [OK]
bitnami/redis             Bitnami Redis Docker Image    22                   [OK]
anapsix/redis             11MB Redis server image ...   6                    [OK]
webhippie/redis           Docker images for redis       4                    [OK]
clue/redis-benchmark      A minimal docker image t...   3                    [OK]
williamyeh/redis          Redis image for Docker        3                    [OK]
unblibraries/redis        Leverages phusion/baseim...   2                    [OK]
greytip/redis             redis 3.0.3                   1                    [OK]
servivum/redis            Redis Docker Image            1                    [OK]
...
```


### 2、取最新版的 Redis 镜像

这里我们拉取官方的最新版本的镜像：

```text
$ docker pull redis:latest
```


### 3、查看本地镜像

使用以下命令来查看是否已安装了 redis：

```text
$ docker images
```

在上图中可以看到我们已经安装了最新版本（latest）的 redis 镜像。


### 4、运行容器

安装完成后，我们可以使用以下命令来运行 redis 容器：

```text
$ docker run -itd --name redis-test -p 6379:6379 redis
```

参数说明：

- -p 6379:6379：映射容器服务的 6379 端口到宿主机的 6379 端口。外部可以直接通过宿主机ip:6379 访问到 Redis 的服务。


### 5、安装成功

最后我们可以通过 docker ps 命令查看容器的运行信息：

接着我们通过 redis-cli 连接测试使用 redis 服务。

```text
$ docker exec -it redis-test /bin/bash
```


## 复习重点

- 能说明 `Docker 安装 Redis` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
