# PyCharm：PyCharm 包管理与虚拟环境

- 来源：[PyCharm 包管理](https://www.runoob.com/pycharm/pycharm-packages.html)
- 分类：DevOps / 工程化
- 技术：PyCharm
- 笔记类型：学习笔记
- 章节序号：1877

## 本章内容

Python 生态的强大之处在于丰富的第三方包，而管理这些包及其依赖是每个项目的必修课。

PyCharm 提供了图形化的包管理界面和集成的终端工具，让包的安装、升级和卸载变得直观高效。

同时，PyCharm 对虚拟环境的支持可以有效隔离不同项目之间的依赖冲突。


## 通过图形界面查看和安装包

PyCharm 提供了一个直观的包管理面板，无需记忆命令行即可完成包的日常操作。

在右侧面板中，你可以看到当前解释器下已安装的所有包及其版本。

在搜索框中输入包名（如 requests），找到目标包后点击 Install Package 按钮。

安装完成后，新包会出现在已安装列表中，并且立即可用。

搜索包时，PyCharm 会从 PyPI 仓库获取最新信息，包括包的描述、版本和依赖关系，帮助你做出选择。


## 使用内置终端（Terminal）安装包

如果你更习惯命令行操作，PyCharm 内置的 终端（Terminal） 工具窗口是一个绝佳选择。


### 打开终端

点击底部工具栏的 Terminal 标签，或使用快捷键 Alt + F12 打开内置终端。

终端会自动激活当前项目的虚拟环境，命令提示符前面会显示环境名称。


### 常用 pip 命令

```text
# 安装单个包
pip install requests

# 安装指定版本的包
pip install requests==2.28.0

# 同时安装多个包
pip install requests flask numpy

# 升级已安装的包到最新版本
pip install --upgrade requests

# 卸载包
pip uninstall requests

# 查看已安装的所有包
pip list

# 查看某个包的详细信息
pip show requests
```

PyCharm 的内置终端与外部终端完全一致，支持所有 pip 命令和系统命令，且与虚拟环境无缝集成。


## 管理虚拟环境

虚拟环境是 Python 开发的核心实践，它确保每个项目拥有独立的依赖空间，互不干扰。


### 新建虚拟环境

在创建新项目时，PyCharm 默认会提示你创建一个新的虚拟环境。

你也可以在已有项目中手动创建：

- 打开 设置。
- 查看已经有的虚拟环境。
- 选择 添加解释器，指定环境存放位置和基础 Python 解释器。
- 点击 确认 完成创建。


### 切换到 Conda 环境

如果你使用 Anaconda 或 Miniconda 管理 Python 环境，PyCharm 也提供原生支持。

- 在 Python Interpreter 设置页面点击齿轮图标，选择 Add...。
- 左侧选择 Conda Environment。
- 选择 Existing environment，PyCharm 会自动检测系统中已安装的 Conda 环境。
- 从下拉列表中选择目标环境，点击 OK 完成切换。

切换虚拟环境后，PyCharm 会自动重新索引包列表。请耐心等待索引完成，否则代码补全和类型检查可能不准确。


## requirements.txt 自动检测

requirements.txt 是 Python 项目中最常见的依赖声明文件，PyCharm 对其有智能的支持。


### 自动检测与提示

当你打开一个包含 requirements.txt 文件的项目时，如果 PyCharm 检测到文件中的某些包尚未安装，编辑器顶部会出现一个醒目的提示栏。

提示内容类似于："Package requirements 'requests', 'flask' are not satisfied"。

点击提示栏中的 Install requirements 链接，PyCharm 会自动调用 pip 安装所有缺失的包。


### 自动生成 requirements.txt

你也可以让 PyCharm 帮你生成 requirements.txt 文件。

在终端中执行以下命令：

```text
# 将当前虚拟环境中所有已安装的包导出到 requirements.txt
pip freeze > requirements.txt
```

之后其他开发者拿到项目时，只需执行 pip install -r requirements.txt 即可一键安装全部依赖。

建议将 requirements.txt 纳入 Git 版本控制，这样团队成员和 CI/CD 流水线都能基于相同的依赖环境进行开发和构建。


## 复习重点

- 能说明 `PyCharm 包管理` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
