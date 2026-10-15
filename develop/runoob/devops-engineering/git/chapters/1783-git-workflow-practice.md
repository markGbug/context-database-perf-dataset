# Git：Git 工作流程

- 来源：[Git 工作流程](https://www.runoob.com/git/git-workflow.html)
- 分类：DevOps / 工程化
- 技术：Git
- 笔记类型：练习笔记
- 章节序号：1783

## 本章内容

本章节我们将为大家介绍 Git 的工作流程。

下图展示了 Git 的工作流程：

我们可以把 Git 的工作流程想象成一个写作业并交给老师的过程。结合上面的图，我们可以把这个流程分为四个主要部分：


### 1. 工作区 (Working Directory) —— 你的书桌

这是你实际修改文件的地方。你在这里写代码、删删改改。

- 动作：你在这里编写了新功能或修复了 Bug。


### 2. 暂存区 (Staging Area) —— 你的待邮寄篮子

当你觉得作业写得差不多了，你会把它放进一个篮子里，准备打包。

- 关键指令：git add
- 意义：告诉 Git，这些改动我确认要提交了，先帮我记着。


### 3. 本地仓库 (Local Repository) —— 你的个人保险箱

你把篮子里的东西打包好，贴上标签（提交信息），锁进自己的保险箱。

- 关键指令：git commit
- 意义：改动正式成为了项目历史的一部分。即便你之后改乱了，也可以随时从这里找回。


### 4. 远程仓库 (Remote) —— 老师的收件箱（如 GitHub/GitLab）

最后，你把保险箱里的代码通过网络发送给远程服务器，方便其他人查看或合作。

- 关键指令：git push
- 意义：备份代码，并与团队共享进度。


### 知识点说明

- git stash (贮藏区)：作业写了一半，突然要改另一个急活，但又不想把没写完的作业提交。这时可以先用 stash 把代码藏进抽屉，等忙完再拿出来继续写（pop）。
- git pull (拉取)：看看老师（远程仓库）那里有没有别人交的新作业，直接同步到你的书桌上。
- git fetch & merge：先看看远程有什么更新（fetch），确认没问题后再合并（merge）到自己的代码里。

简单总结： 修改代码 → add (放进篮子) → commit (存入箱子) → push (寄给远方)。


## 命令说明


### 1、克隆仓库

如果你要参与一个已有的项目，首先需要将远程仓库克隆到本地：

```text
git clone https://github.com/username/repo.git
cd repo
```


### 2、创建新分支

为了避免直接在 main 或 master 分支上进行开发，通常会创建一个新的分支：

```text
git checkout -b new-feature
```


### 3、工作目录

在工作目录中进行代码编辑、添加新文件或删除不需要的文件。


### 4、暂存文件

将修改过的文件添加到暂存区，以便进行下一步的提交操作：

```text
git add filename
# 或者添加所有修改的文件
git add .
```


### 5、提交更改

将暂存区的更改提交到本地仓库，并添加提交信息：

```text
git commit -m "Add new feature"
```


### 6、拉取最新更改

在推送本地更改之前，最好从远程仓库拉取最新的更改，以避免冲突：

```text
git pull origin main
# 或者如果在新的分支上工作
git pull origin new-feature
```


### 7、推送更改

将本地的提交推送到远程仓库：

```text
git push origin new-feature
```


### 8、创建 Pull Request（PR）

在 GitHub 或其他托管平台上创建 Pull Request，邀请团队成员进行代码审查。PR 合并后，你的更改就会合并到主分支。


### 9、合并更改

在 PR 审核通过并合并后，可以将远程仓库的主分支合并到本地分支：

```text
git checkout main
git pull origin main
git merge new-feature
```


### 10、删除分支

如果不再需要新功能分支，可以将其删除：

```text
git branch -d new-feature
```

或者从远程仓库删除分支：

```text
git push origin --delete new-feature
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Git 工作流程` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
