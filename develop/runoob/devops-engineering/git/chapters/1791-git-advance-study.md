# Git：Git 进阶操作

- 来源：[Git 进阶操作](https://www.runoob.com/git/git-advance.html)
- 分类：DevOps / 工程化
- 技术：Git
- 笔记类型：学习笔记
- 章节序号：1791

## 本章内容

在掌握了 Git 的基础操作之后，进阶操作可以帮助你更高效地管理和优化你的代码库。

以下是一些常见的进阶操作及其详细说明：

- 交互式暂存：逐块选择要暂存的更改，精细控制提交内容。
- Git Stash：临时保存工作进度，方便切换任务。
- Git Rebase：将一个分支上的更改移到另一个分支之上，保持提交历史线性。
- Git Cherry-Pick：选择特定提交并应用到当前分支。


### 1、交互式暂存（Interactive Staging）

git add 命令可以选择性地将文件或文件的一部分添加到暂存区，这在处理复杂更改时非常有用。

- 使用 git add -p：逐块选择要暂存的更改。

```text
git add -p
```

执行此命令后，Git 会逐块显示文件的更改，你可以选择是否暂存每个块。常用选项包括：

- y：暂存当前块
- n：跳过当前块
- s：拆分当前块
- e：手动编辑当前块
- q：退出暂存


### 2、Git Stash：临时保存工作进度

git stash 命令允许你临时保存当前工作目录的更改，以便你可以切换到其他分支或处理其他任务。

保存当前工作进度：

```text
git stash
```

查看存储的进度：

```text
git stash list
```

应用最近一次存储的进度：

```text
git stash apply
```

应用并删除最近一次存储的进度：

```text
git stash pop
```

删除特定存储：

```text
git stash drop stash@{n}
```

清空所有存储：

```text
git stash clear
```


### 3、Git Rebase：变基

git rebase 命令用于将一个分支上的更改移到另一个分支之上。它可以帮助保持提交历史的线性，减少合并时的冲突。

变基当前分支到指定分支：

```html
git rebase <branchname>
```

例如，将当前分支变基到 main 分支：

```text
git rebase main
```

- 交互式变基：

```html
git rebase -i <commit>
```

交互式变基允许你在变基过程中编辑、删除或合并提交。常用选项包括：

- pick：保留提交
- reword：修改提交信息
- edit：编辑提交
- squash：将当前提交与前一个提交合并
- fixup：将当前提交与前一个提交合并，不保留提交信息
- drop：删除提交


### 4、Git Cherry-Pick：拣选提交

git cherry-pick 命令允许你选择特定的提交并将其应用到当前分支。它在需要从一个分支移植特定更改到另一个分支时非常有用。

拣选提交：

```html
git cherry-pick <commit>
```

例如，将 abc123 提交应用到当前分支：

```text
git cherry-pick abc123
```

处理拣选冲突：如果拣选过程中出现冲突，解决冲突后使用 git cherry-pick --continue 继续拣选。


### 示例操作

以下是一个综合示例，展示了如何使用这些进阶操作：

交互式暂存：

```text
git add -p
```

保存工作进度：

```text
git stash
```

查看存储的进度：

```text
git stash list
```

应用存储的进度：

```text
git stash apply
```

变基当前分支到 main 分支：

```text
git rebase main
```

交互式变基，编辑提交历史：

```text
git rebase -i HEAD~3
```

编辑提交历史，如合并和重命名提交。

拣选 feature 分支上的特定提交到 main 分支：

```text
git checkout main
git cherry-pick abc123
```


## 复习重点

- 能说明 `Git 进阶操作` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
