# MongoDB：MongoDB 创建集合

- 来源：[MongoDB 创建集合](https://www.runoob.com/mongodb/mongodb-create-collection.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：学习笔记
- 章节序号：1470

## 本章内容

本章节我们为大家介绍如何使用 MongoDB 来创建集合。

MongoDB 中使用 createCollection() 方法来创建集合。

语法格式：

```text
db.createCollection(name, options)
```

参数说明：

- name: 要创建的集合名称。
- options: 可选参数, 指定有关内存大小及索引的选项。

options 可以是如下参数：

在插入文档时，MongoDB 首先检查固定集合的 size 字段，然后检查 max 字段。

使用这些选项创建一个集合的实例：


## 实例

这个例子创建了一个集合，具有以下特性：

- 固定大小，最大 10MB，最多存储 5000 个文档。
- 文档必须包含 name 和 email 字段，其中 name 必须是字符串，email 必须是有效的电子邮件格式。
- 验证级别为严格，验证失败将阻止插入或更新。
- 使用 WiredTiger 存储引擎，指定块压缩器为 zstd。
- 默认使用英语排序规则。


### 实例

在 test 数据库中创建 runoob 集合：

```text
> use test
switched to db test
> db.createCollection("runoob")
{ "ok" : 1 }
>
```

如果要查看已有集合，可以使用 show collections 或 show tables 命令：

```text
> show collections
runoob
system.indexes
```

下面是带有几个关键参数的 createCollection() 的用法：

创建了一个固定大小的集合，最大大小为 5MB（5242880 字节），最多存储 5000 个文档。

```text
db.createCollection("myCappedCollection", { capped: true, size: 5242880, max: 5000 });
```

在 MongoDB 中，你不需要创建集合，当你插入一些文档时，MongoDB 会自动创建集合。

```text
> db.mycol2.insert({"name" : "菜鸟教程"})
> show collections
mycol2
...
```

创建了一个最大大小为 1MB（1048576 字节）的固定大小集合：

```text
db.createCollection("myCappedCollection", { capped: true, size: 1048576 });
```

以下例子为 myCollection 集合创建了一个验证器，要求文档中必须有 name 和 age 字段，且 name 必须是字符串，age 必须是非负整数。


## 实例


## 复习重点

- 能说明 `MongoDB 创建集合` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
