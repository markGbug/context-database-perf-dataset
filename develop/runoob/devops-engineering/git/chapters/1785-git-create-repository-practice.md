# Git：Git 创建仓库

- 来源：[Git 创建仓库](https://www.runoob.com/git/git-create-repository.html)
- 分类：DevOps / 工程化
- 技术：Git
- 笔记类型：练习笔记
- 章节序号：1785

## 本章内容

本章节我们将为大家介绍如何创建一个 Git 仓库。

你可以使用一个已经存在的目录作为 Git 仓库。


## git init

Git 使用 git init 命令来初始化一个 Git 仓库，Git 的很多命令都需要在 Git 的仓库中运行，所以 git init 是使用 Git 的第一个命令。

在执行完成 git init 命令后，Git 仓库会生成一个 .git 目录，该目录包含了资源的所有元数据，其他的项目目录保持不变。


### 使用方法

进入你想要创建仓库的目录，或者先创建一个新的目录：

```text
mkdir my-project
cd my-project
```

使用当前目录作为 Git 仓库，我们只需使它初始化。

```text
git init
```

该命令执行完后会在当前目录生成一个 .git 目录。

使用我们指定目录作为Git仓库。

```text
git init newrepo
```

初始化后，会在 newrepo 目录下会出现一个名为 .git 的目录，所有 Git 需要的数据和资源都存放在这个目录中。

如果当前目录下有几个文件想要纳入版本控制，需要先用 git add 命令告诉 Git 开始对这些文件进行跟踪，然后提交：

```text
$ git add *.c
$ git add README
$ git commit -m '初始化项目版本'
```

以上命令将目录下以 .c 结尾及 README 文件提交到仓库中。

注： 在 Linux 系统中，commit 信息使用单引号 '，Windows 系统，commit 信息使用双引号 "。

所以在 git bash 中 git commit -m '提交说明' 这样是可以的，在 Windows 命令行中就要使用双引号 git commit -m "提交说明"。


## git clone

我们使用 git clone 从现有 Git 仓库中拷贝项目（类似 svn checkout）。 克隆仓库的命令格式为： git clone <repo> 如果我们需要克隆到指定的目录，可以使用以下命令格式： git clone <repo> <directory> 参数说明： repo:Git 仓库。 directory:本地目录。 比如，要克隆 Ruby 语言的 Git 代码仓库 Grit，可以用下面的命令： $ git clone git://github.com/schacon/grit.git 执行该命令后，会在当前目录下创建一个名为grit的目录，其中包含一个 .git 的目录，用于保存下载下来的所有版本记录。 如果要自己定义要新建的项目目录名称，可以在上面的命令末尾指定新的名字：

```text
$ git clone git://github.com/schacon/grit.git mygrit
```


## 配置

git 的设置使用 git config 命令。

```text
$ git config --list
credential.helper=osxkeychain
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
core.ignorecase=true
core.precomposeunicode=true
```

```text
$ git config -e    # 针对当前仓库
```

或者：

```text
$ git config -e --global   # 针对系统上所有仓库
```

设置提交代码时的用户信息：

```text
$ git config --global user.name "runoob"
$ git config --global user.email test@runoob.com
```

如果去掉 --global 参数只对当前仓库有效。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Git 创建仓库` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
