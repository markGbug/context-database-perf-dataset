# MongoDB：MongoDB 更新文档

- 来源：[MongoDB 更新文档](https://www.runoob.com/mongodb/mongodb-update.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：练习笔记
- 章节序号：1474

## 本章内容

在 MongoDB 中，更新文档的操作可以使用多种方法实现，常用的方法包括 updateOne()、updateMany()、replaceOne() 和 findOneAndUpdate()。


### 1、updateOne()

updateOne() 方法用于更新匹配过滤器的单个文档。

语法：

```text
db.collection.updateOne(filter, update, options)
```

- filter：用于查找文档的查询条件。
- update：指定更新操作的文档或更新操作符。
- options：可选参数对象，如 upsert、arrayFilters 等。


## 实例


### 2、updateMany()

updateMany() 方法用于更新所有匹配过滤器的文档。

语法：

```text
db.collection.updateMany(filter, update, options)
```

- filter：用于查找文档的查询条件。
- update：指定更新操作的文档或更新操作符。
- options：可选参数对象，如 upsert、arrayFilters 等。


## 实例


### 3、replaceOne()

replaceOne() 方法用于替换匹配过滤器的单个文档，新的文档将完全替换旧的文档。

语法：

```text
db.collection.replaceOne(filter, replacement, options)
```

- filter：用于查找文档的查询条件。
- replacement：新的文档，将替换旧的文档。
- options：可选参数对象，如 upsert 等。


## 实例


### 4、findOneAndUpdate()

findOneAndUpdate() 方法用于查找并更新单个文档，可以选择返回更新前或更新后的文档。

语法：

```text
db.collection.findOneAndUpdate(filter, update, options)
```

- filter：用于查找文档的查询条件。
- update：指定更新操作的文档或更新操作符。
- options：可选参数对象，如 projection、sort、upsert、returnDocument 等。


## 实例


### 选项参数

这些更新方法的 options 参数通常可以包含以下选项：

- upsert：如果没有匹配的文档，是否插入一个新文档。
- arrayFilters：当更新嵌套数组时，指定应更新的数组元素的条件。
- collation：指定比较字符串时使用的排序规则。
- returnDocument：在 findOneAndUpdate 中使用，指定返回更新前 ("before") 或更新后 ("after") 的文档。


### 简单实例

更新单个文档：

```text
db.myCollection.updateOne(
    { name: "Alice" },
    { $set: { age: 26 } }
);
```

更新多个文档：

```text
db.myCollection.updateMany(
    { age: { $lt: 30 } },
    { $set: { status: "active" } }
);
```

替换单个文档：

```text
db.myCollection.replaceOne(
    { name: "Bob" },
    { name: "Bob", age: 31 }
);
```

查找并更新单个文档：

```text
db.myCollection.findOneAndUpdate(
    { name: "Charlie" },
    { $set: { age: 36 } },
    { returnDocument: "after" }
);
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MongoDB 更新文档` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
