# MongoDB：MongoDB 覆盖索引查询

- 来源：[MongoDB 覆盖索引查询](https://www.runoob.com/mongodb/mongodb-covered-queries.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：学习笔记
- 章节序号：1494

## 本章内容

官方的MongoDB的文档中说明，覆盖查询是以下的查询：

- 所有的查询字段是索引的一部分
- 所有的查询返回字段在同一个索引中

由于所有出现在查询中的字段是索引的一部分， MongoDB 无需在整个数据文档中检索匹配查询条件和返回使用相同索引的查询结果。

因为索引存在于RAM中，从索引中获取数据比通过扫描文档读取数据要快得多。


## 使用覆盖索引查询

为了测试覆盖索引查询，使用以下 users 集合:

```text
{
   "_id": ObjectId("53402597d852426020000002"),
   "contact": "987654321",
   "dob": "01-01-1991",
   "gender": "M",
   "name": "Tom Benzamin",
   "user_name": "tombenzamin"
}
```

我们在 users 集合中创建联合索引，字段为 gender 和 user_name :

```text
>db.users.createIndex({gender:1,user_name:1})
```

注：5.0 之前版本可以使用 db.collection.ensureIndex() ，但 ensureIndex() 在 5.0 版本后已被移除，使用 createIndex() 代替。

现在，该索引会覆盖以下查询：

```text
>db.users.find({gender:"M"},{user_name:1,_id:0})
```

也就是说，对于上述查询，MongoDB的不会去数据库文件中查找。相反，它会从索引中提取数据，这是非常快速的数据查询。

由于我们的索引中不包括 _id 字段，_id在查询中会默认返回，我们可以在MongoDB的查询结果集中排除它。

下面的实例没有排除_id，查询就不会被覆盖：

```text
>db.users.find({gender:"M"},{user_name:1})
```

最后，如果是以下的查询，不能使用覆盖索引查询：

- 所有索引字段是一个数组
- 所有索引字段是一个子文档


## 复习重点

- 能说明 `MongoDB 覆盖索引查询` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
