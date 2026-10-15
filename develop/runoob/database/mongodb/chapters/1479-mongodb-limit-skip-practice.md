# MongoDB：MongoDB Limit 与 Skip 方法

- 来源：[MongoDB Limit 与 Skip 方法](https://www.runoob.com/mongodb/mongodb-limit-skip.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：练习笔记
- 章节序号：1479

## 本章内容

## MongoDB Limit() 方法

如果你需要在 MongoDB 中读取指定数量的数据记录，可以使用 MongoDB 的 limit() 方法，如果想跳过指定数量的文档读取数据可以使用 skip() 方法。

limit() 方法用于限制查询结果返回的文档数量，而 skip() 方法用于跳过指定数量的文档。这两个方法通常一起使用，可以用来实现分页查询或在大型数据集上进行分批处理。


## limit() 方法

limit() 方法用于限制查询结果返回的文档数量。


### 语法

limit() 方法基本语法如下所示：

```html
db.collection.find().limit(<limit>)
```

- <limit>：返回的文档数量。


## 实例


### 实例

集合 col 中的数据如下：

```text
{ "_id" : ObjectId("56066542ade2f21f36b0313a"), "title" : "PHP 教程", "description" : "PHP 是一种创建动态交互性站点的强有力的服务器端脚本语言。", "by" : "菜鸟教程", "url" : "http://www.runoob.com", "tags" : [ "php" ], "likes" : 200 }
{ "_id" : ObjectId("56066549ade2f21f36b0313b"), "title" : "Java 教程", "description" : "Java 是由Sun Microsystems公司于1995年5月推出的高级程序设计语言。", "by" : "菜鸟教程", "url" : "http://www.runoob.com", "tags" : [ "java" ], "likes" : 150 }
{ "_id" : ObjectId("5606654fade2f21f36b0313c"), "title" : "MongoDB 教程", "description" : "MongoDB 是一个 Nosql 数据库", "by" : "菜鸟教程", "url" : "http://www.runoob.com", "tags" : [ "mongodb" ], "likes" : 100 }
```

以下实例为显示查询文档中的两条记录：

```text
> db.col.find({},{"title":1,_id:0}).limit(2)
{ "title" : "PHP 教程" }
{ "title" : "Java 教程" }
>
```

注：如果你们没有指定 limit() 方法中的参数则显示集合中的所有数据。


## skip() 方法

我们除了可以使用 limit() 方法来读取指定数量的数据外，还可以使用 skip() 方法来跳过指定数量的数据，skip() 方法同样接受一个数字参数作为跳过的记录条数。

skip() 方法用于跳过指定数量的文档，从而实现分页或分批查询。


### 语法

skip() 方法语法格式如下：

```html
db.collection.find().skip(<skip>)
```

- <skip>：要跳过的文档数量。


## 实例


### 实例

以下实例只会显示第二条文档数据

```text
>db.col.find({},{"title":1,_id:0}).limit(1).skip(1)
{ "title" : "Java 教程" }
>
```

分页查询：


## 实例

注:skip()方法默认参数为 0 。


### 注意事项

- skip() 和 limit() 方法通常用于配合使用，以实现分页查询。但是在大型数据集上使用 skip() 可能会导致性能问题，因为 MongoDB 在执行查询时需要扫描并跳过指定数量的文档，因此建议仅在需要时才使用 skip() 方法，尽量避免在大型数据集上连续使用。
- 当结合 skip() 和 limit() 时，skip() 应该在 limit() 之前使用，以避免意外行为。

通过使用 limit() 和 skip() 方法，您可以实现在 MongoDB 中对查询结果进行分页处理，提高查询的灵活性和性能。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MongoDB Limit 与 Skip 方法` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
