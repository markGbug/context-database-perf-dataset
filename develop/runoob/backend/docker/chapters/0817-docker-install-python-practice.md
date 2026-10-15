# Docker：Docker 安装 Python

- 来源：[Docker 安装 Python](https://www.runoob.com/docker/docker-install-python.html)
- 分类：后端开发
- 技术：Docker
- 笔记类型：练习笔记
- 章节序号：0817

## 本章内容

### 方法一、docker pull python:3.5

查找 Docker Hub 上的 Python 镜像:

可以通过 Sort by 查看其他版本的 python，默认是最新版本 python:latest。

此外，我们还可以用 docker search python 命令来查看可用版本：

```text
runoob@runoob:~/python$ docker search python
NAME                           DESCRIPTION                        STARS     OFFICIAL   AUTOMATED
python                         Python is an interpreted,...       982       [OK]
kaggle/python                  Docker image for Python...         33                   [OK]
azukiapp/python                Docker image to run Python ...     3                    [OK]
vimagick/python                mini python                                  2          [OK]
tsuru/python                   Image for the Python ...           2                    [OK]
pandada8/alpine-python         An alpine based python image                 1          [OK]
1science/python                Python Docker images based on ...  1                    [OK]
lucidfrontier45/python-uwsgi   Python with uWSGI                  1                    [OK]
orbweb/python                  Python image                       1                    [OK]
pathwar/python                 Python template for Pathwar levels 1                    [OK]
rounds/10m-python              Python, setuptools and pip.        0                    [OK]
ruimashita/python              ubuntu 14.04 python                0                    [OK]
tnanba/python                  Python on CentOS-7 image.          0                    [OK]
```

这里我们拉取官方的镜像,标签为3.5

```text
runoob@runoob:~/python$ docker pull python:3.5
```

等待下载完成后，我们就可以在本地镜像列表里查到 REPOSITORY 为python, 标签为 3.5 的镜像。

```text
runoob@runoob:~/python$ docker images python:3.5
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
python              3.5              045767ddf24a        9 days ago          684.1 MB
```


### 方法二、通过 Dockerfile 构建


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Docker 安装 Python` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
