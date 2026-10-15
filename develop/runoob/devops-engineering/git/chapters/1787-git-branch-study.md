# Git：Git 分支管理

- 来源：[Git 分支管理](https://www.runoob.com/git/git-branch.html)
- 分类：DevOps / 工程化
- 技术：Git
- 笔记类型：学习笔记
- 章节序号：1787

## 本章内容

Git 分支管理是 Git 强大功能之一，能够让多个开发人员并行工作，开发新功能、修复 bug 或进行实验，而不会影响主代码库。

几乎每一种版本控制系统都以某种形式支持分支，一个分支代表一条独立的开发线。

使用分支意味着你可以从开发主线上分离开来，然后在不影响主线的同时继续工作。

Git 分支实际上是指向更改快照的指针。

有人把 Git 的分支模型称为必杀技特性，而正是因为它，将 Git 从版本控制系统家族里区分出来。


### 创建分支

创建新分支并切换到该分支：

```html
git checkout -b <branchname>
```

例如：

```text
git checkout -b feature-xyz
```

切换分支命令:

```text
git checkout (branchname)
```

例如：

```text
git checkout main
```

当你切换分支的时候，Git 会用该分支的最后提交的快照替换你的工作目录的内容， 所以多个分支不需要多个目录。


### 查看分支

查看所有分支：

```text
git branch
```

查看远程分支：

```text
git branch -r
```

查看所有本地和远程分支：

```text
git branch -a
```


### 合并分支

将其他分支合并到当前分支：

```html
git merge <branchname>
```

例如，切换到 main 分支并合并 feature-xyz 分支：

```text
git checkout main
git merge feature-xyz
```


### 解决合并冲突

当合并过程中出现冲突时，Git 会标记冲突文件，你需要手动解决冲突。

打开冲突文件，按照标记解决冲突。

标记冲突解决完成：

```html
git add <conflict-file>
```

提交合并结果：

```text
git commit
```


### 删除分支

删除本地分支：

```html
git branch -d <branchname>
```

强制删除未合并的分支：

```html
git branch -D <branchname>
```

删除远程分支：

```html
git push origin --delete <branchname>
```


## 实例

开始前我们先创建一个测试目录：

```text
$ mkdir gitdemo
$ cd gitdemo/
$ git init
Initialized empty Git repository...
$ touch README
$ git add README
$ git commit -m '第一次版本提交'
[master (root-commit) 3b58100] 第一次版本提交
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README
```


## Git 分支管理


### 列出分支

列出分支基本命令：

```text
git branch
```

没有参数时，git branch 会列出你在本地的分支。

```text
$ git branch
* master
```

此例的意思就是，我们有一个叫做 master 的分支，并且该分支是当前分支。

当你执行 git init 的时候，默认情况下 Git 就会为你创建 master 分支。


## 复习重点

- 能说明 `Git 分支管理` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
