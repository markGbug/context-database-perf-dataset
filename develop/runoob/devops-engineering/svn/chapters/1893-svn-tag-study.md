# SVN：SVN 标签（tag）

- 来源：[SVN 标签](https://www.runoob.com/svn/svn-tag.html)
- 分类：DevOps / 工程化
- 技术：SVN
- 笔记类型：学习笔记
- 章节序号：1893

## 本章内容

版本管理系统支持 tag 选项，通过使用 tag 的概念，我们可以给某一个具体版本的代码一个更加有意义的名字。

Tags 即标签主要用于项目开发中的里程碑，比如开发到一定阶段可以单独一个版本作为发布等，它往往代表一个可以固定的完整的版本，这跟 VSS 中的 Tag 大致相同。

我们在本地工作副本创建一个 tag。

```text
root@runoob:~/svn/runoob01# svn copy trunk/ tags/v1.0
A         tags/v1.0
```

上面的代码成功完成，新的目录将会被创建在 tags 目录下。

```text
root@runoob:~/svn/runoob01# ls tags/
v1.0
root@runoob:~/svn/runoob01# ls tags/v1.0/
HelloWorld.html  readme
```

查看状态。

```text
root@runoob:~/svn/runoob01# svn status
A  +    tags/v1.0
```

提交tag内容。

```text
root@runoob:~/svn/runoob01# svn commit -m "tags v1.0"
Adding         tags/v1.0
Transmitting file data ..
Committed revision 14.
```


## 复习重点

- 能说明 `SVN 标签` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
