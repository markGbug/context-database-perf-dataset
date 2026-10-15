# MongoDB：MongoDB $type 操作符

- 来源：[MongoDB $type 操作符](https://www.runoob.com/mongodb/mongodb-operators-type.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：学习笔记
- 章节序号：1478

## 本章内容

在 MongoDB 中，$type 操作符用于查询具有指定类型的字段的文档。

MongoDB 的 $type 操作符用于查询字段的 BSON 数据类型。

它允许您指定一个或多个类型，并返回匹配这些类型的文档。

语法：

```html
db.collection.find({ field: { $type: <type> } })
```

- field：要检查类型的字段。
- type：指定的 BSON 类型，可以是类型的数字代码或类型名称的字符串。


### BSON 类型

以下是常见的 BSON 类型及其对应的数字代码和字符串名称：


### 实例

查找字段类型为字符串的文档:

```text
db.myCollection.find({ fieldName: { $type: "string" } })
```

或使用类型代码：

```text
db.myCollection.find({ fieldName: { $type: 2 } })
```

查找字段类型为数字的文档，例如，查找 age 字段类型为整数的文档：

```text
db.myCollection.find({ age: { $type: "int" } })
```

或使用类型代码：

```text
db.myCollection.find({ age: { $type: 16 } })
```

查找字段类型为布尔值的文档：

```text
db.myCollection.find({ isActive: { $type: "bool" } })
```

或使用类型代码：

```text
db.myCollection.find({ isActive: { $type: 8 } })
```

查找字段类型为日期的文档：

```text
db.myCollection.find({ createdAt: { $type: "date" } })
```

或使用类型代码：

```text
db.myCollection.find({ createdAt: { $type: 9 } })
```

查找字段类型为多种类型的文档，例如，查找 value 字段类型为字符串或整数的文档：

```text
db.myCollection.find({ value: { $type: ["string", "int"] } })
```

或使用类型代码：

```text
db.myCollection.find({ value: { $type: [2, 16] } })
```

查找 details 字段类型为对象，并且 score 字段类型为双精度浮点数的文档：


## 实例

或使用类型代码：


## 实例

通过使用 $type 操作符，您可以精确地查询文档中特定字段的数据类型，从而进行更细粒度的数据过滤和管理。


## 更多实例

我们使用的数据库名称为"runoob" 我们的集合名称为"col"，以下为我们插入的数据。

简单的集合"col"：

```text
>db.col.insert({
    title: 'PHP 教程',
    description: 'PHP 是一种创建动态交互性站点的强有力的服务器端脚本语言。',
    by: '菜鸟教程',
    url: 'http://www.runoob.com',
    tags: ['php'],
    likes: 200
})
```

```text
>db.col.insert({title: 'Java 教程',
    description: 'Java 是由Sun Microsystems公司于1995年5月推出的高级程序设计语言。',
    by: '菜鸟教程',
    url: 'http://www.runoob.com',
    tags: ['java'],
    likes: 150
})
```

```text
>db.col.insert({title: 'MongoDB 教程',
    description: 'MongoDB 是一个 Nosql 数据库',
    by: '菜鸟教程',
    url: 'http://www.runoob.com',
    tags: ['mongodb'],
    likes: 100
})
```

使用find()命令查看数据：

```text
> db.col.find()
{ "_id" : ObjectId("56066542ade2f21f36b0313a"), "title" : "PHP 教程", "description" : "PHP 是一种创建动态交互性站点的强有力的服务器端脚本语言。", "by" : "菜鸟教程", "url" : "http://www.runoob.com", "tags" : [ "php" ], "likes" : 200 }
{ "_id" : ObjectId("56066549ade2f21f36b0313b"), "title" : "Java 教程", "description" : "Java 是由Sun Microsystems公司于1995年5月推出的高级程序设计语言。", "by" : "菜鸟教程", "url" : "http://www.runoob.com", "tags" : [ "java" ], "likes" : 150 }
{ "_id" : ObjectId("5606654fade2f21f36b0313c"), "title" : "MongoDB 教程", "description" : "MongoDB 是一个 Nosql 数据库", "by" : "菜鸟教程", "url" : "http://www.runoob.com", "tags" : [ "mongodb" ], "likes" : 100 }
```


## MongoDB 操作符 - $type 实例

如果想获取 "col" 集合中 title 为 String 的数据，你可以使用以下命令：

```text
db.col.find({"title" : {$type : 2}})
或
db.col.find({"title" : {$type : 'string'}})
```

输出结果为：

```text
{ "_id" : ObjectId("56066542ade2f21f36b0313a"), "title" : "PHP 教程", "description" : "PHP 是一种创建动态交互性站点的强有力的服务器端脚本语言。", "by" : "菜鸟教程", "url" : "http://www.runoob.com", "tags" : [ "php" ], "likes" : 200 }
{ "_id" : ObjectId("56066549ade2f21f36b0313b"), "title" : "Java 教程", "description" : "Java 是由Sun Microsystems公司于1995年5月推出的高级程序设计语言。", "by" : "菜鸟教程", "url" : "http://www.runoob.com", "tags" : [ "java" ], "likes" : 150 }
{ "_id" : ObjectId("5606654fade2f21f36b0313c"), "title" : "MongoDB 教程", "description" : "MongoDB 是一个 Nosql 数据库", "by" : "菜鸟教程", "url" : "http://www.runoob.com", "tags" : [ "mongodb" ], "likes" : 100 }
```


## 复习重点

- 能说明 `MongoDB $type 操作符` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
