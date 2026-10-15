# SVN：SVN 提交操作

- 来源：[SVN 提交操作](https://www.runoob.com/svn/svn-commit.html)
- 分类：DevOps / 工程化
- 技术：SVN
- 笔记类型：学习笔记
- 章节序号：1889

## 本章内容

在上一章中，我们检出了版本库runoob01，对应的目录放在/home/user01/runoob01中，下面我们针对这个库进行版本控制。

我们在库本版中需要增加一个readme的说明文件。

```text
root@runoob:~/svn/runoob01/trunk# cat readme
this is SVN tutorial.
```

查看工作副本中的状态。

```text
root@runoob:~/svn/runoob01/trunk# svn status
?       readme
```

此时 readme的状态为？，说明它还未加到版本控制中。

将文件readme加到版本控制，等待提交到版本库。

```text
root@runoob:~/svn/runoob01/trunk# svn add readme
A         readme
```

查看工作副本中的状态

```text
root@runoob:~/svn/runoob01/trunk# svn status
A       readme
```

此时 readme的状态为A,它意味着这个文件已经被成功地添加到了版本控制中。


## 复习重点

- 能说明 `SVN 提交操作` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
