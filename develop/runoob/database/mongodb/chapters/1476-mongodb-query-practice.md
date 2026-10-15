# MongoDB：MongoDB 查询文档

- 来源：[MongoDB 查询文档](https://www.runoob.com/mongodb/mongodb-query.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：练习笔记
- 章节序号：1476

## 本章内容

MongoDB 查询文档使用 find()、findOne() 方法。

find() 方法以非结构化的方式来显示所有文档。


### 语法

MongoDB 查询数据的语法格式如下：

```text
db.collection.find(query, projection)
```

- query：用于查找文档的查询条件。默认为 {}，即匹配所有文档。
- projection（可选）：指定返回结果中包含或排除的字段。

查找所有文档：


## 实例

按条件查找文档：


## 实例

按条件查找文档，并只返回指定字段：


## 实例

如果你需要以易读的方式来读取数据，可以使用 pretty() 方法，语法格式如下：

```text
>db.col.find().pretty()
```

pretty() 方法以格式化的方式来显示所有文档。


## 实例


### 2、findOne()

findOne() 方法用于查找集合中的单个文档。如果找到多个匹配的文档，它只返回第一个。

语法：

```text
db.collection.findOne(query, projection)
```

- query：用于查找文档的查询条件。默认为 {}，即匹配所有文档。
- projection（可选）：指定返回结果中包含或排除的字段。

查找单个文档：

```text
db.myCollection.findOne({ name: "Alice" });
```

```text
db.myCollection.findOne(
    { name: "Alice" },
    { name: 1, age: 1, _id: 0 }
);
```


## 高级查询方法


### 1、使用比较操作符

MongoDB 支持多种比较操作符，如 $gt、$lt、$gte、$lte、$eq、$ne 等。

查找年龄大于 25 的文档:

```text
db.myCollection.find({ age: { $gt: 25 } });
```


### 2、使用逻辑操作符

MongoDB 支持多种逻辑操作符，如 $and、$or、$not、$nor 等。

查找年龄大于 25 且城市为 "New York" 的文档:


## 实例


### 3、使用正则表达式

可以使用正则表达式进行模式匹配查询。

查找名字以 "A" 开头的文档：

```text
db.myCollection.find({ name: /^A/ });
```


### 4、投影

投影用于控制查询结果中返回的字段。可以使用包含字段和排除字段两种方式。

只返回名字和年龄字段：


## 实例


### 5、排序

可以对查询结果进行排序。

按年龄降序排序：

```text
db.myCollection.find().sort({ age: -1 });
```


### 6、限制与跳过

可以对查询结果进行限制和跳过指定数量的文档。

返回前 10 个文档：

```text
db.myCollection.find().limit(10);
```

跳过前 5 个文档，返回接下来的 10 个文档：

```text
db.myCollection.find().skip(5).limit(10);
```


### 实例

查找年龄大于 25 且城市为 "New York" 的文档，只返回名字和年龄字段，按年龄降序排序，并返回前 10 个文档。


## 实例


## MongoDB 与 RDBMS Where 语句比较

如果你熟悉常规的 SQL 数据，通过下表可以更好的理解 MongoDB 的条件语句查询：


## MongoDB AND 条件

MongoDB 的 find() 方法可以传入多个键(key)，每个键(key)以逗号隔开，即常规 SQL 的 AND 条件。

语法格式如下：

```text
>db.col.find({key1:value1, key2:value2}).pretty()
```


### 实例

以下实例通过 by 和 title 键来查询 菜鸟教程 中 MongoDB 教程 的数据

```text
> db.col.find({"by":"菜鸟教程", "title":"MongoDB 教程"}).pretty()
{
        "_id" : ObjectId("56063f17ade2f21f36b03133"),
        "title" : "MongoDB 教程",
        "description" : "MongoDB 是一个 Nosql 数据库",
        "by" : "菜鸟教程",
        "url" : "http://www.runoob.com",
        "tags" : [
                "mongodb",
                "database",
                "NoSQL"
        ],
        "likes" : 100
}
```

以上实例中类似于 WHERE 语句：WHERE by='菜鸟教程' AND title='MongoDB 教程'


## MongoDB OR 条件

MongoDB OR 条件语句使用了关键字 $or,语法格式如下：

```text
>db.col.find(
   {
      $or: [
         {key1: value1}, {key2:value2}
      ]
   }
).pretty()
```


### 实例

以下实例中，我们演示了查询键 by 值为 菜鸟教程 或键 title 值为 MongoDB 教程 的文档。

```text
>db.col.find({$or:[{"by":"菜鸟教程"},{"title": "MongoDB 教程"}]}).pretty()
{
        "_id" : ObjectId("56063f17ade2f21f36b03133"),
        "title" : "MongoDB 教程",
        "description" : "MongoDB 是一个 Nosql 数据库",
        "by" : "菜鸟教程",
        "url" : "http://www.runoob.com",
        "tags" : [
                "mongodb",
                "database",
                "NoSQL"
        ],
        "likes" : 100
}
>
```


## AND 和 OR 联合使用

以下实例演示了 AND 和 OR 联合使用，类似常规 SQL 语句为： 'where likes>50 AND (by = '菜鸟教程' OR title = 'MongoDB 教程')'

```text
>db.col.find({"likes": {$gt:50}, $or: [{"by": "菜鸟教程"},{"title": "MongoDB 教程"}]}).pretty()
{
        "_id" : ObjectId("56063f17ade2f21f36b03133"),
        "title" : "MongoDB 教程",
        "description" : "MongoDB 是一个 Nosql 数据库",
        "by" : "菜鸟教程",
        "url" : "http://www.runoob.com",
        "tags" : [
                "mongodb",
                "database",
                "NoSQL"
        ],
        "likes" : 100
}
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MongoDB 查询文档` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
