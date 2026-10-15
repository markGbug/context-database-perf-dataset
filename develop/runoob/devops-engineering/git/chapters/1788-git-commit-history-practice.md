# Git：Git 查看提交历史

- 来源：[Git 查看提交历史](https://www.runoob.com/git/git-commit-history.html)
- 分类：DevOps / 工程化
- 技术：Git
- 笔记类型：练习笔记
- 章节序号：1788

## 本章内容

查看 Git 提交历史可以帮助你了解代码的变更情况和开发进度。

Git 提供了多种命令和选项来查看提交历史，从简单的日志到详细的差异对比。

Git 提交历史一般常用两个命令：

- git log - 查看历史提交记录。
- git blame <file> - 以列表形式查看指定文件的历史修改记录。

## git log

在使用 Git 提交了若干更新之后，又或者克隆了某个项目，想回顾下提交历史，我们可以使用 git log 命令查看。

git log 命令用于查看 Git 仓库中提交历史记录。

git log 显示了从最新提交到最早提交的所有提交信息，包括提交的哈希值、作者、提交日期和提交消息等。

git log 命令的基本语法：

```text
git log [选项] [分支名/提交哈希]
```

常用的选项包括：

- -p：显示提交的补丁（具体更改内容）。
- --oneline：以简洁的一行格式显示提交信息。
- --graph：以图形化方式显示分支和合并历史。
- --decorate：显示分支和标签指向的提交。
- --author=<作者>：只显示特定作者的提交。
- --since=<时间>：只显示指定时间之后的提交。
- --until=<时间>：只显示指定时间之前的提交。
- --grep=<模式>：只显示包含指定模式的提交消息。
- --no-merges：不显示合并提交。
- --stat：显示简略统计信息，包括修改的文件和行数。
- --abbrev-commit：使用短提交哈希值。
- --pretty=<格式>：使用自定义的提交信息显示格式。

针对我们前一章节的操作，使用 git log 命令列出历史提交记录如下：

```php
$ git log
commit d5e9fc2c811e0ca2b2d28506ef7dc14171a207d9 (HEAD -> master)
Merge: c68142b 7774248
Author: runoob <test@runoob.com>
Date:   Fri May 3 15:55:58 2019 +0800

    Merge branch 'change_site'

commit c68142b562c260c3071754623b08e2657b4c6d5b
Author: runoob <test@runoob.com>
Date:   Fri May 3 15:52:12 2019 +0800

    修改代码

commit 777424832e714cf65d3be79b50a4717aea51ab69 (change_site)
Author: runoob <test@runoob.com>
Date:   Fri May 3 15:49:26 2019 +0800

    changed the runoob.php

commit c1501a244676ff55e7cccac1ecac0e18cbf6cb00
Author: runoob <test@runoob.com>
Date:   Fri May 3 15:35:32 2019 +0800
```

我们可以用 --oneline 选项来查看历史记录的简洁的版本。

```php
$ git log --oneline
$ git log --oneline
d5e9fc2 (HEAD -> master) Merge branch 'change_site'
c68142b 修改代码
7774248 (change_site) changed the runoob.php
c1501a2 removed test.txt、add runoob.php
3e92c19 add test.txt
3b58100 第一次版本提交
```

这告诉我们的是，此项目的开发历史。

我们还可以用 --graph 选项，查看历史中什么时候出现了分支、合并。以下为相同的命令，开启了拓扑图选项：

```text
*   d5e9fc2 (HEAD -> master) Merge branch 'change_site'
|\
| * 7774248 (change_site) changed the runoob.php
* | c68142b 修改代码
|/
* c1501a2 removed test.txt、add runoob.php
* 3e92c19 add test.txt
* 3b58100 第一次版本提交
```

现在我们可以更清楚明了地看到何时工作分叉、又何时归并。

你也可以用 --reverse 参数来逆向显示所有日志。

```php
$ git log --reverse --oneline
3b58100 第一次版本提交
3e92c19 add test.txt
c1501a2 removed test.txt、add runoob.php
7774248 (change_site) changed the runoob.php
c68142b 修改代码
d5e9fc2 (HEAD -> master) Merge branch 'change_site'
```

如果只想查找指定用户的提交日志可以使用命令：git log --author , 例如，比方说我们要找 Git 源码中 Linus 提交的部分：

```php
$ git log --author=Linus --oneline -5
81b50f3 Move 'builtin-*' into a 'builtin/' subdirectory
3bb7256 make "index-pack" a built-in
377d027 make "git pack-redundant" a built-in
b532581 make "git unpack-file" a built-in
112dd51 make "mktag" a built-in
```

如果你要指定日期，可以执行几个选项：--since 和 --before，但是你也可以用 --until 和 --after。

例如，如果我要看 Git 项目中三周前且在四月十八日之后的所有提交，我可以执行这个（我还用了 --no-merges 选项以隐藏合并提交）：

### 常用选项

限制显示的提交数:

```html
git log -n <number>
```

例如，显示最近的 5 次提交：

```text
git log -n 5
```

显示自指定日期之后的提交：

```text
git log --since="2024-01-01"
```

显示指定日期之前的提交：

```text
git log --until="2024-07-01"
```

只显示某个作者的提交：

```text
git log --author="Author Name"
```

更多 git log 命令可查看 http://git-scm.com/docs/git-log 或使用 git log --help 命令查看帮助信息。

## git blame

git blame 命令用于逐行显示指定文件的每一行代码是由谁在什么时候引入或修改的。

git blame 可以追踪文件中每一行的变更历史，包括作者、提交哈希、提交日期和提交消息等信息。

如果要查看指定文件的修改记录可以使用 git blame 命令，格式如下：

```text
git blame [选项] <文件路径>
```

常用的选项包括：

- -L <起始行号>,<结束行号>：只显示指定行号范围内的代码注释。
- -C：对于重命名或拷贝的代码行，也进行代码行溯源。
- -M：对于移动的代码行，也进行代码行溯源。
- -C -C 或 -M -M：对于较多改动的代码行，进行更进一步的溯源。
- --show-stats：显示包含每个作者的行数统计信息。

显示文件每一行的代码注释和相关信息：

```text
git blame <文件路径>
```

只显示指定行号范围内的代码注释：

```text
git blame -L <起始行号>,<结束行号> <文件路径>
```

对于重命名或拷贝的代码行进行溯源：

```text
git blame -C <文件路径>
```

对于移动的代码行进行溯源：

```text
git blame -M <文件路径>
```

显示行数统计信息：

```text
git blame --show-stats <文件路径>
```

git blame 命令是以列表形式显示修改记录，如下实例：

```php
$ git blame README
^d2097aa (tianqixin 2020-08-25 14:59:25 +0800 1) # Runoob Git 测试
db9315b0 (runoob    2020-08-25 16:00:23 +0800 2) # 菜鸟教程
```

更多内容可以使用 git blame --help 查看完整的帮助文档，了解更多选项和使用方式。

## 恢复和回退

Git 提供了多种方式来恢复和回退到之前的版本，不同的命令适用于不同的场景和需求。

以下是几种常见的方法：

- git checkout：切换分支或恢复文件到指定提交。
- git reset：重置当前分支到指定提交（软重置、混合重置、硬重置）。
- git revert：创建一个新的提交以撤销指定提交，不改变提交历史。
- git reflog：查看历史操作记录，找回丢失的提交。

### 1、git checkout：检查出特定版本的文件

git checkout 命令用于切换分支或恢复工作目录中的文件到指定的提交。

恢复工作目录中的文件到某个提交：

```html
git checkout <commit> -- <filename>
```

例如，将 file.txt 恢复到 abc123 提交时的版本：

```text
git checkout abc123 -- file.txt
```

切换到特定提交：

```html
git checkout <commit>
```

例如：

```text
git checkout abc123
```

这种方式切换到特定的提交时，处于分离头指针（detached HEAD）状态。

### 2、git reset：重置当前分支到特定提交

git reset 命令可以更改当前分支的提交历史，它有三种主要模式：--soft、--mixed 和 --hard。

--soft：只重置 HEAD 到指定的提交，暂存区和工作目录保持不变。

```html
git reset --soft <commit>
```

--mixed（默认）：重置 HEAD 到指定的提交，暂存区重置，但工作目录保持不变。

```html
git reset --mixed <commit>
```

--hard：重置 HEAD 到指定的提交，暂存区和工作目录都重置。

```html
git reset --hard <commit>
```

例如，将当前分支重置到 abc123 提交：

```text
git reset --hard abc123
```

### 3、git revert：撤销某次提交

git revert 命令创建一个新的提交，用来撤销指定的提交，它不会改变提交历史，适用于已经推送到远程仓库的提交。

```html
git revert <commit>
```

例如，撤销 abc123 提交：

```text
git revert abc123
```

### 4、git reflog：查看历史操作记录

git reflog 命令记录了所有 HEAD 的移动。即使提交被删除或重置，也可以通过 reflog 找回。

```text
git reflog
```

利用 reflog 可以找到之前的提交哈希，从而恢复到特定状态。例如：

```text
git reset --hard HEAD@{3}
```

### 实例

以下是一个综合示例，演示如何使用这些命令恢复历史版本：

查看提交历史：

```text
git log --oneline
```

假设输出如下：

```text
abc1234 Commit 1
def5678 Commit 2
ghi9012 Commit 3
```

切换到 Commit 2（处于分离头指针状态）：

```text
git checkout def5678
```

重置到 Commit 2，保留更改到暂存区：

```text
git reset --soft def5678
```

重置到 Commit 2，取消暂存区更改：

```text
git reset --mixed def5678
```

重置到 Commit 2，丢弃所有更改：

```text
git reset --hard def5678
```

撤销 Commit 2：

```text
git revert def5678
```

查看 reflog 找回丢失的提交：

```text
git reflog
```

找到之前的提交哈希并恢复：

```text
git reset --hard HEAD@{3}
```

## 动手验证

- 复现 `Git 查看提交历史` 中的关键示例或命令。
- 修改一个输入、参数或条件，观察结果变化。
- 记录报错信息、定位过程和修复方式。
