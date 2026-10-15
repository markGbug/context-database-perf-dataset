# MongoDB：MongoDB 插入文档

- 来源：[MongoDB 插入文档](https://www.runoob.com/mongodb/mongodb-insert.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：学习笔记
- 章节序号：1473

## 本章内容

本章节中我们将向大家介绍如何将数据插入到 MongoDB 的集合中。

文档的数据结构和 JSON 基本一样。

所有存储在集合中的数据都是 BSON 格式。

BSON 是一种类似 JSON 的二进制形式的存储格式，是 Binary JSON 的简称。

常用的插入文档方法包括：


### 1、insertOne()

insertOne() 方法用于在集合中插入单个文档。

```text
db.collection.insertOne(document, options)
```

- document：要插入的单个文档。
- options（可选）：一个可选参数对象，可以包含 writeConcern 和 bypassDocumentValidation 等。


## 实例

返回结果：

```text
{
    "acknowledged": true,
    "insertedId": ObjectId("60c72b2f9b1d8b5a5f8e2b2d")
}
```


### 2、insertMany()

insertMany() 方法用于在集合中插入多个文档。

```text
db.collection.insertMany(documents, options)
```

- documents：要插入的文档数组。
- options（可选）：一个可选参数对象，可以包含 ordered、writeConcern 和 bypassDocumentValidation 等。

```text
db.myCollection.insertMany([
    { name: "Bob", age: 30, city: "Los Angeles" },
    { name: "Charlie", age: 35, city: "Chicago" }
]);
```

返回结果：

```text
{
    "acknowledged": true,
    "insertedIds": [
        ObjectId("60c72b2f9b1d8b5a5f8e2b2e"),
        ObjectId("60c72b2f9b1d8b5a5f8e2b2f")
    ]
}
```


### 3、db.collection.save()

save() 方法在插入文档时表现得类似于 insertOne()。

如果文档包含 _id 字段且已存在，则该文档会被更新；如果文档不包含 _id 字段或 _id 不存在，则会插入一个新文档。

从 MongoDB 4.2 开始，db.collection.save() 已被标记为弃用（deprecated），官方推荐使用 db.collection.insertOne() 或 db.collection.replaceOne() 替代。

```text
db.collection.save(document, options)
```

- document：要保存的文档。
- options（可选）：一个可选参数对象，可以包含 writeConcern 等。

```text
db.myCollection.save({
    _id: ObjectId("60c72b2f9b1d8b5a5f8e2b2d"),
    name: "David",
    age: 40,
    city: "San Francisco"
});
```


### 插入单个或多个文档（旧方法）

使用 db.collection.insert() 方法插入单个或多个文档。

insert() 方法在 MongoDB 4.2 及更高版本中已被标记为弃用（deprecated），推荐使用 insertOne() 和 insertMany()。

语法：

```text
db.collection.insert(document_or_array)
```

参数：

- 可以是一个文档，也可以是一个文档数组。

1、插入单个文档：

```text
db.users.insert({ name: "David", age: 40, email: "david@example.com" });
```

2、插入多个文档：

```text
db.users.insert([
  { name: "Eve", age: 45, email: "eve@example.com" },
  { name: "Frank", age: 50, email: "frank@example.com" }
]);
```


### 批量插入的性能优化

如果需要插入大量文档，可以使用 insertMany() 并启用 ordered: false 选项，以提高插入性能。

语法：

```text
db.collection.insertMany([document1, document2, ...], { ordered: false })
```

参数：

- ordered: false：表示无序插入，即使某个文档插入失败，也不会影响其他文档的插入。


## 实例


### 插入时的验证

MongoDB 会根据集合的 schema 验证规则（如果定义了）对插入的文档进行验证。如果文档不符合规则，插入操作会失败。

假设集合 users 有一个验证规则，要求 age 字段必须大于 0：

```text
db.createCollection("users", {
  validator: {
    age: { $gt: 0 }
  }
});
```

如果插入以下文档会失败：

```text
db.users.insertOne({ name: "John", age: -5 }); // 验证失败
```


## 复习重点

- 能说明 `MongoDB 插入文档` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
