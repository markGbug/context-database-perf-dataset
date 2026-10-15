# Docker：CentOS Docker 安装

- 来源：[CentOS Docker 安装](https://www.runoob.com/docker/centos-docker-install.html)
- 分类：后端开发
- 技术：Docker
- 笔记类型：学习笔记
- 章节序号：0797

## 本章内容

Docker 支持以下的 64 位 CentOS 版本：

- CentOS 9 (stream)
- 更高版本...

必须启用 centos-extras 仓库，该仓库默认启用，如果您禁用了它，需要重新启用。


## 使用官方安装脚本自动安装

安装命令如下：

```text
$ curl -fsSL https://get.docker.com -o install-docker.sh
$ sudo sh install-docker.sh
```


## 手动安装


### 卸载旧版本

较旧的 Docker 版本称为 docker 或 docker-engine，如果已安装这些程序，请卸载它们以及相关的依赖项。

运行以下命令卸载旧版本：


### 安装


### 使用 Docker 仓库进行安装

在新主机上首次安装 Docker 之前，需要设置 Docker 仓库。之后，您可以从仓库安装和更新 Docker。

设置仓库

安装 dnf-plugins-core 包（提供管理 DNF 仓库的命令），并设置仓库。

使用以下命令来设置稳定的仓库。


## 使用官方源地址（比较慢）

可以执行以下命令换成清华大学的镜像源：


## 清华大学镜像源

参考地址：https://mirrors.tuna.tsinghua.edu.cn/help/docker-ce/


### 安装

运行以下命令安装Docker：：

```text
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

如果提示接受 GPG 密钥，验证指纹是否与 060A 61C5 1B55 8A7F 742B 77AA C52F EB6B 621E 9F35 匹配，如果匹配则接受。

安装成功后，启动 Docker 引擎：

```text
sudo systemctl start docker
```

如果希望 Docker 在系统启动时也启动可以使用以下命令：

```text
sudo systemctl enable --now docker
```

以上命令会配置 Docker 的 systemd 服务，在系统启动时自动启动 Docker。

Docker 安装完默认未启动。并且已经创建好 docker 用户组，但该用户组下没有用户。

运行以下命令来验证安装是否成功：

```text
sudo docker run hello-world
```

此命令会下载一个测试镜像，并在容器中运行，当容器运行时，会打印确认消息并退出。


### 卸载 docker

删除安装包：

```text
yum remove docker-ce
```

删除镜像、容器、配置文件等内容：

```text
rm -rf /var/lib/docker
```


## 复习重点

- 能说明 `CentOS Docker 安装` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
