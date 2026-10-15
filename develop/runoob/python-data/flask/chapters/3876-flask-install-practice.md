# Flask：Flask 安装

- 来源：[Flask 安装](https://www.runoob.com/flask/flask-install.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
- 章节序号：3876

## 本章内容

在开始编写 Flask 应用之前，我们需要先准备好 Python 环境并安装 Flask。

Flask 安装还是比较简单的。

Flask 是 Python的一个库，所以首先需要确保你的计算机上已经安装了 Python。


## Python 版本要求

Flask 3.x 要求 Python 3.9 及以上版本。

如果你还没有安装 Python，可以从 python.org 下载安装。

安装完成后，打开终端验证：

```text
$ python3 --version
Python 3.12.3

$ pip3 --version
pip 24.0 from /usr/lib/python3.12/site-packages/pip (python 3.12)
```

macOS 和大多数 Linux 发行版已预装 Python 3。如果你用的是 Windows，安装时请勾选 Add Python to PATH 选项。


## 虚拟环境

虚拟环境（Virtual Environment）是 Python 项目的标配做法，它为每个项目创建独立的 Python 包空间。


### 为什么要用虚拟环境

假设你有两个项目：项目 A 需要 Flask 3.0，项目 B 需要 Flask 2.3。

如果全局安装，两个版本的 Flask 会互相冲突。

虚拟环境让每个项目拥有独立的依赖包，互不干扰。

Python 自带的 venv 模块就可以创建虚拟环境，无需安装额外工具。


### 创建虚拟环境

首先创建项目目录，然后在其中创建虚拟环境：

```text
$ mkdir runoob-flask-test
$ cd runoob-flask-test
$ python3 -m venv .venv
```

.venv 是虚拟环境的目录名，你可以改成自己喜欢的名称，但 .venv 是社区最常见的约定。


### 激活虚拟环境

激活成功后，终端提示符前会出现 (.venv) 标识，表示虚拟环境已生效。

```text
$ . .venv/bin/activate
(.venv) $   # <-- 提示符变了，说明虚拟环境已经激活
```


### 退出虚拟环境

完成开发后，使用 deactivate 命令退出：

```text
(.venv) $ deactivate
$
```

每次打开新终端窗口时，都需要重新激活虚拟环境才能使用 Flask。

另外也可以使用 uv 这个Python 包与环境管理工具，参考：https://www.runoob.com/python3/uv-tutorial.html

```text
# 使用指定 Python 版本创建虚拟环境
uv venv --python 3.12
激活虚拟环境：

# macOS / Linux
source .venv/bin/activate

# Windows（PowerShell）
.venv\Scripts\activate
```


## 安装 Flask

在虚拟环境已激活的状态下，使用 pip 安装 Flask：

```text
(.venv) $ pip install Flask
```

安装完成后，验证 Flask 是否安装成功：

```text
flask --version
```

输出类似如下信息：

```text
Python 3.9.6
Flask 3.0.0
Werkzeug 3.1.5
```

也可以用以下代码验证：

```text
from importlib.metadata import version

flask_version = version("flask")
print(flask_version)
```

如果按照成功会输出类似如下的版本号：

```text
3.1.3
```

此时，以下依赖包也被一并安装：Werkzeug、Jinja2、Click、itsdangerous、blinker。


### 可选：安装 python-dotenv

python-dotenv 让你可以通过 .env 和 .flaskenv 文件管理环境变量，简化 Flask 命令的使用：

```text
(.venv) $ pip install python-dotenv
```

虽然不是必须的，但在实际开发中强烈建议安装。它让你省去每次输入 --app 参数，也方便团队共享环境配置。


## 项目目录结构

在开始编码前，了解一个标准的 Flask 项目目录结构很有帮助：

```text
myflaskapp/
├── .venv/          # 虚拟环境（不要提交到 Git）
├── app.py           # 应用入口文件
├── templates/       # Jinja2 模板文件目录
├── static/          # CSS、JS、图片等静态文件目录
├── .flaskenv        # Flask 环境变量（可选）
└── .gitignore       # 忽略 .venv 等不需要提交的文件
```

虚拟环境目录 .venv 不应该提交到 Git。在 .gitignore 中添加 .venv/ 即可。


## 开发环境

开发环境推荐：

- VS Code 开发工具
- PyCharm 开发工具

国内阿里与字节也有基于 VS Code 开发的 AI IDE：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flask 安装` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
