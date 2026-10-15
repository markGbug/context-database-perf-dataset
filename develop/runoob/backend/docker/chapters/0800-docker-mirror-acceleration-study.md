# Docker：Docker 镜像加速

- 来源：[Docker 镜像加速](https://www.runoob.com/docker/docker-mirror-acceleration.html)
- 分类：后端开发
- 技术：Docker
- 笔记类型：学习笔记
- 章节序号：0800

## 本章内容

国内从 DockerHub 拉取镜像有时会遇到困难，此时可以配置镜像加速器。

目前国内 Docker 镜像源出现了一些问题，基本不能用了，后期能用我再更新下。

Docker 官方和国内很多云服务商都提供了国内加速器服务，例如：

- 科大镜像：https://docker.mirrors.ustc.edu.cn/
- 网易：https://hub-mirror.c.163.com/
- 阿里云：https://<你的ID>.mirror.aliyuncs.com
- 七牛云加速器：https://reg-mirror.qiniu.com

当配置某一个加速器地址之后，若发现拉取不到镜像，请切换到另一个加速器地址。国内各大云服务商均提供了 Docker 镜像加速服务，建议根据运行 Docker 的云平台选择对应的镜像加速服务。

阿里云镜像获取地址：https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors，登陆后，左侧菜单选中镜像加速器就可以看到你的专属地址了：

之前还有 Docker 官方加速器 https://registry.docker-cn.com ，现在好像已经不能使用了，我们可以多添加几个国内的镜像，如果有不能使用的，会切换到可以使用的镜像来拉取。


### Ubuntu14.04、Debian7Wheezy

对于使用 upstart 的系统而言，编辑 /etc/default/docker 文件，在其中的 DOCKER_OPTS 中配置加速器地址：

```text
DOCKER_OPTS="--registry-mirror=https://registry.docker-cn.com"
```

重新启动服务:

```text
$ sudo service docker restart
```


### Ubuntu16.04+、Debian8+、CentOS7

对于使用 systemd 的系统，请在 /etc/docker/daemon.json 中写入如下内容（如果文件不存在请新建该文件）：

```text
{"registry-mirrors":["https://reg-mirror.qiniu.com/"]}
```

之后重新启动服务：


### Windows 10

对于使用 Windows 10 的系统，在系统右下角托盘 Docker 图标内右键菜单选择 Settings，打开配置窗口后左侧导航菜单选择 Daemon。在 Registrymirrors 一栏中填写加速器地址 https://docker.mirrors.ustc.edu.cn/ ，之后点击 Apply 保存后 Docker 就会重启并应用配置的镜像地址了。


### Mac OS X

对于使用 Mac OS X 的用户，在任务栏点击 Docker for mac 应用图标-> Perferences...-> Daemon-> Registrymirrors。在列表中填写加速器地址 https://reg-mirror.qiniu.com 。修改完成之后，点击 Apply&Restart 按钮，Docker 就会重启并应用配置的镜像地址了。


### 检查加速器是否生效

检查加速器是否生效配置加速器之后，如果拉取镜像仍然十分缓慢，请手动检查加速器配置是否生效，在命令行执行 docker info，如果从结果中看到了如下内容，说明配置成功。

```text
$ docker info
Registry Mirrors:
    https://reg-mirror.qiniu.com
```


## 复习重点

- 能说明 `Docker 镜像加速` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
