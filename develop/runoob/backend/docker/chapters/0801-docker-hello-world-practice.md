# Docker：Docker Hello World

- 来源：[Docker Hello World](https://www.runoob.com/docker/docker-hello-world.html)
- 分类：后端开发
- 技术：Docker
- 笔记类型：练习笔记
- 章节序号：0801

## 本章内容

Docker 允许你在容器内运行应用程序， 使用 docker run 命令来在容器内运行一个应用程序。

输出Hello world

```text
runoob@runoob:~$ docker run ubuntu:15.10 /bin/echo "Hello world"
Hello world
```

各个参数解析：

- docker: Docker 的二进制执行文件。
- run: 与前面的 docker 组合来运行一个容器。
- ubuntu:15.10 指定要运行的镜像，Docker 首先从本地主机上查找镜像是否存在，如果不存在，Docker 就会从镜像仓库 Docker Hub 下载公共镜像。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Docker Hello World` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
