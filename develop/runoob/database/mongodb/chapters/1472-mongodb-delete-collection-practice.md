# MongoDB：MongoDB 删除集合

- 来源：[MongoDB 删除集合](https://www.runoob.com/mongodb/mongodb-delete-collection.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：练习笔记
- 章节序号：1472

## 本章内容

本章节我们为大家介绍如何使用 MongoDB 来删除集合。

MongoDB 中使用 drop() 方法来删除集合。

drop() 方法可以永久地从数据库中删除指定的集合及其所有文档，这是一个不可逆的操作，因此需要谨慎使用。

语法格式：

```text
db.collection.drop()
```

参数说明：

- 无

返回值

如果成功删除选定集合，则 drop() 方法返回 true，否则返回 false。


### 实例

在数据库 mydb 中，我们可以先通过 show collections 命令查看已存在的集合：

```text
>use mydb
switched to db mydb
>show collections
mycol
mycol2
system.indexes
runoob
>
```

接着删除集合 mycol2 :

```text
>db.mycol2.drop()
true
>
```

通过 show collections 再次查看数据库 mydb 中的集合：

```text
>show collections
mycol
system.indexes
runoob
>
```

从结果中可以看出 mycol2 集合已被删除。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MongoDB 删除集合` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
