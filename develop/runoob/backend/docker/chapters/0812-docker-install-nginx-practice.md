# Docker：Docker 安装 Nginx

- 来源：[Docker 安装 Nginx](https://www.runoob.com/docker/docker-install-nginx.html)
- 分类：后端开发
- 技术：Docker
- 笔记类型：练习笔记
- 章节序号：0812

## 本章内容

Nginx 是一个高性能的 HTTP 和反向代理 web 服务器，同时也提供了 IMAP/POP3/SMTP 服务 。


### 1、查看可用的 Nginx 版本

访问 Nginx 镜像库地址： https://hub.docker.com/_/nginx?tab=tags。

可以通过 Sort by 查看其他版本的 Nginx，默认是最新版本 nginx:latest。

你也可以在下拉列表中找到其他你想要的版本：

此外，我们还可以用 docker search nginx 命令来查看可用版本：

```text
$ docker search nginx
NAME                      DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
nginx                     Official build of Nginx.                        3260      [OK]
jwilder/nginx-proxy       Automated Nginx reverse proxy for docker c...   674                  [OK]
richarvey/nginx-php-fpm   Container running Nginx + PHP-FPM capable ...   207                  [OK]
million12/nginx-php       Nginx + PHP-FPM 5.5, 5.6, 7.0 (NG), CentOS...   67                   [OK]
maxexcloo/nginx-php       Docker framework container with Nginx and ...   57                   [OK]
...
```


### 2、取最新版的 Nginx 镜像

这里我们拉取官方的最新版本的镜像：

```text
$ docker pull nginx:latest
```


### 3、查看本地镜像

使用以下命令来查看是否已安装了 nginx：

```text
$ docker images
```

在上图中可以看到我们已经安装了最新版本（latest）的 nginx 镜像。


### 4、运行容器

安装完成后，我们可以使用以下命令来运行 nginx 容器：

```text
$ docker run --name nginx-test -p 8080:80 -d nginx
```

参数说明：

- --name nginx-test：容器名称。
- -p 8080:80： 端口进行映射，将本地 8080 端口映射到容器内部的 80 端口。
- -d nginx： 设置容器在在后台一直运行。


### 5、安装成功

最后我们可以通过浏览器可以直接访问 8080 端口的 nginx 服务：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Docker 安装 Nginx` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
