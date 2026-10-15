# MongoDB：MongoDB 原子操作

- 来源：[MongoDB 原子操作](https://www.runoob.com/mongodb/mongodb-atomic-operations.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：学习笔记
- 章节序号：1496

## 本章内容

mongodb不支持事务，所以，在你的项目中应用时，要注意这点。无论什么设计，都不要要求mongodb保证数据的完整性。

但是mongodb提供了许多原子操作，比如文档的保存，修改，删除等，都是原子操作。

所谓原子操作就是要么这个文档保存到Mongodb，要么没有保存到Mongodb，不会出现查询到的文档没有保存完整的情况。


## 原子操作数据模型

考虑下面的例子，图书馆的书籍及结账信息。

实例说明了在一个相同的文档中如何确保嵌入字段关联原子操作（update：更新）的字段是同步的。

```text
book = {
          _id: 123456789,
          title: "MongoDB: The Definitive Guide",
          author: [ "Kristina Chodorow", "Mike Dirolf" ],
          published_date: ISODate("2010-09-24"),
          pages: 216,
          language: "English",
          publisher_id: "oreilly",
          available: 3,
          checkout: [ { by: "joe", date: ISODate("2012-10-15") } ]
        }
```

你可以使用 db.collection.findAndModify() 方法来判断书籍是否可结算并更新新的结算信息。

在同一个文档中嵌入的 available 和 checkout 字段来确保这些字段是同步更新的:

```text
db.books.findAndModify ( {
   query: {
            _id: 123456789,
            available: { $gt: 0 }
          },
   update: {
             $inc: { available: -1 },
             $push: { checkout: { by: "abc", date: new Date() } }
           }
} )
```


## 原子操作常用命令

用来指定一个键并更新键值，若键不存在并创建。

```text
{ $set : { field : value } }
```

用来删除一个键。

```text
{ $unset : { field : 1} }
```

$inc可以对文档的某个值为数字型（只能为满足要求的数字）的键进行增减的操作。

```text
{ $inc : { field : value } }
```

用法：

```text
{ $push : { field : value } }
```

把value追加到field里面去，field一定要是数组类型才行，如果field不存在，会新增一个数组类型加进去。

同$push,只是一次可以追加多个值到一个数组字段内。

```text
{ $pushAll : { field : value_array } }
```

从数组field内删除一个等于value值。

```text
{ $pull : { field : _value } }
```

增加一个值到数组内，而且只有当这个值不在数组内才增加。


## 复习重点

- 能说明 `MongoDB 原子操作` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
