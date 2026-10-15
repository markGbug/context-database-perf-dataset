# MongoDB：MongoDB 删除文档

- 来源：[MongoDB 删除文档](https://www.runoob.com/mongodb/mongodb-remove.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：练习笔记
- 章节序号：1475

## 本章内容

在前面的几个章节中我们已经学习了 MongoDB 中如何为集合添加数据和更新数据，在本章节中我们将继续学习 MongoDB 集合的删除。

常用的删除文档方法包括 deleteOne()、deleteMany() 以及 findOneAndDelete()。

使用场景：

- 数据清理：删除不再需要的旧数据或无效数据。
- 数据修正：在数据修正过程中删除错误的或重复的文档。
- 自动化任务：在自动化脚本或任务中，根据特定条件删除文档。


### 1、deleteOne()

deleteOne() 方法用于删除匹配过滤器的单个文档。

语法：

```text
db.collection.deleteOne(filter, options)
```

- filter：用于查找要删除的文档的查询条件。
- options（可选）：一个可选参数对象。


## 实例

返回结果：

```text
{
    "acknowledged": true,
    "deletedCount": 1
}
```


### 2、deleteMany()

deleteMany() 方法用于删除所有匹配过滤器的文档。

语法：

```text
db.collection.deleteMany(filter, options)
```

- filter：用于查找要删除的文档的查询条件。
- options（可选）：一个可选参数对象。


## 实例

返回结果：

```text
{
    "acknowledged": true,
    "deletedCount": 1
}
```


### 3、findOneAndDelete()

findOneAndDelete() 方法用于查找并删除单个文档，并可以选择返回删除的文档。

语法：

```text
db.collection.findOneAndDelete(filter, options)
```

- filter：用于查找要删除的文档的查询条件。
- options：可选参数对象，如 projection、sort 等。


## 实例

findOneAndDelete 返回被删除的文档，如果找不到匹配的文档，则返回 null。


### 删除操作的选项

这些删除方法的 options 参数通常可以包含以下选项：

- writeConcern：指定写操作的确认级别。
- collation：指定比较字符串时使用的排序规则。
- projection（仅适用于 findOneAndDelete）：指定返回的字段。
- sort（仅适用于 findOneAndDelete）：指定排序顺序以确定要删除的文档。


### 实例

删除单个文档：

```text
db.myCollection.deleteOne({ name: "Alice" });
```

删除多个文档：

```text
db.myCollection.deleteMany({ status: "inactive" });
```

查找并删除单个文档：

```text
db.myCollection.findOneAndDelete(
    { name: "Charlie" },
    { projection: { name: 1, age: 1 } }
);
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MongoDB 删除文档` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
