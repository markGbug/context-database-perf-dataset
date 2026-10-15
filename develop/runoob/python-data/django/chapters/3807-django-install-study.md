# Django：Django 安装

- 来源：[Django 安装](https://www.runoob.com/django/django-install.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：学习笔记
- 章节序号：3807

## 本章内容

在安装 Django 前，系统需要已经安装了 Python 的开发环境。

如果你还没有安装 Python，请先从 Python 官网 https://www.python.org/ 下载并安装最新版本的 Python。

Django 安装也很简单使包管理工具 pip 就可以了：

```text
pip install Django
```

安装完成后，你可以通过运行以下命令验证 Django 是否成功安装：

```text
python3 -m django --version
```

如果一切顺利，你将看到安装的 Django 版本号，如：4.2.7。

开发环境推荐：

- 1、VS Code 开发工具
- 2、PyCharm 开发工具
- 3、阿里 Qoder
- 4、Trae 开发工具


## Windows 下安装 Django

接下来我们来具体看下不同系统下 Django 的安装。

如果你还未安装Python环境需要先下载Python安装包。

1、Python 下载地址：https://www.python.org/downloads/

2、Django 下载地址：https://www.djangoproject.com/download/

注意：目前 Django 1.6.x 以上版本已经完全兼容 Python 3.x。


### Python 安装(已安装的可跳过)

安装 Python 你只需要下载 python-x.x.x.msi 文件，然后一直点击 "Next" 按钮即可。

安装完成后你需要设置 Python 环境变量。 右击计算机->属性->高级->环境变量->修改系统变量 path，添加 Python 安装地址，本文实例使用的是 C:\Python33，你需要根据你实际情况来安装。


### Django 安装

下载 Django 压缩包，解压并和 Python安装目录放在同一个根目录，进入 Django 目录，执行 python setup.py install，然后开始安装，Django 将要被安装到 Python 的 Lib下site-packages。

然后是配置环境变量，将这几个目录添加到系统环境变量中： C:\Python33\Lib\site-packages\django;C:\Python33\Scripts。 添加完成后就可以使用Django的django-admin.py命令新建工程了。


## 检查是否安装成功

输入以下命令进行检查:

```text
>>> import django
>>> django.get_version()
```

如果输出了Django的版本号说明安装正确。


## Linux 上安装 Django


### yum 安装方法

以下安装位于 Centos Linux 环境下安装，如果是你的 Linux 系统是 ubuntu 请使用 apt-get 命令。

默认情况下 Linux 环境已经支持了Python。你可以在终端输入Python命令来查看是否已经安装。

```text
Python 3.7.4 (default, Aug  1 2012, 05:14:39)
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>
```


### 安装 setuptools

命令：

```text
# Python3 安装
yum install python3-setuptools
# Python2 安装
yum install python2-setuptools
```

完成之后，就可以使用 easy_install 命令安装 django


## 复习重点

- 能说明 `Django 安装` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
