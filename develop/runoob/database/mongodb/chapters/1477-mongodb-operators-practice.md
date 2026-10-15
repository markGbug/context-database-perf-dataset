# MongoDB：MongoDB 条件操作符

- 来源：[MongoDB 条件操作符](https://www.runoob.com/mongodb/mongodb-operators.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：练习笔记
- 章节序号：1477

## 本章内容

在本章节中，我们将讨论如何在 MongoDB 中使用条件操作符。

在 MongoDB 中，条件操作符用于在查询文档时进行过滤、比较和逻辑操作。

这些操作符可以分为以下几类：比较操作符、逻辑操作符、元素操作符、数组操作符、以及其他常用操作符。


## 比较操作符

比较操作符有：


### $eq (等于)

语法格式：

```text
{ field: { $eq: value } }
```

查找年龄等于 25 的人：

```text
db.collection.find({ age: { $eq: 25 } })
```


### $ne (不等于)

语法格式：

```text
{ field: { $ne: value } }
```

查找年龄不等于 25 的人：

```text
db.collection.find({ age: { $ne: 25 } })
```


### $gt (大于)

语法格式：

```text
{ field: { $gt: value } }
```

查找年龄大于 25 的人：

```text
db.collection.find({ age: { $gt: 25 } })
```


### $gte (大于等于)

语法格式：

```text
{ field: { $gte: value } }
```

查找年龄大于或等于 25 的人：

```text
db.collection.find({ age: { $gte: 25 } })
```


### $lt (小于)

查找年龄小于 25 的人：

```text
db.collection.find({ age: { $lt: 25 } })
```


### $lte (小于等于)

语法格式：

```text
{ field: { $lte: value } }
```

查找年龄小于或等于25的人：

```text
db.collection.find({ age: { $lte: 25 } })
```


### $in (值在数组中)

语法格式：

```text
{ field: { $in: [value1, value2, ...] } }
```

查找年龄在 20、25 和 30 岁之间的人：

```text
db.collection.find({ age: { $in: [20, 25, 30] } })
```


### $nin (值不在数组中)

语法格式：

```text
{ field: { $nin: [value1, value2, ...] } }
```

查找年龄不在 20、25 和 30 岁之间的人：

```text
db.collection.find({ age: { $nin: [20, 25, 30] } })
```


## 逻辑操作符

逻辑操作符有：


### $and (多个条件都成立)

语法格式：

```text
{ $and: [ { condition1 }, { condition2 } ] }
```

查找年龄大于 25 且小于 35 的人:

```text
db.collection.find({ $and: [{ age: { $gt: 25 } }, { age: { $lt: 35 } }] })
```


### $or (至少一个条件成立)

语法格式：

```text
{ $or: [ { condition1 }, { condition2 } ] }
```

查找年龄大于 25 或小于 18 的人:

```text
db.collection.find({ $or: [{ age: { $gt: 25 } }, { age: { $lt: 18 } }] })
```


### $not (取反条件)

语法格式：

```text
{ field: { $not: { condition } } }
```

查找年龄不大于 25 的人:

```text
db.collection.find({ age: { $not: { $gt: 25 } } })
```


### $nor (没有任何条件成立)

语法格式：

```text
{ $nor: [ { condition1 }, { condition2 } ] }
```

查找年龄不大于 25 且不小于 18 的人:

```text
db.collection.find({ $nor: [{ age: { $gt: 25 } }, { age: { $lt: 18 } }] })
```


## 元素操作符

元素操作符有：


### $exists (字段是否存在)

语法格式：

```java
{ field: { $exists: boolean } }
```

查找包含 age 字段的文档:

```text
db.collection.find({ age: { $exists: true } })
```


### $type (字段类型)

语法格式：

```text
{ field: { $type: "type" } }
```

查找 age 字段为整数类型的文档:

```text
db.collection.find({ age: { $type: "int" } })
```


## 数组操作符

数组操作符有：

查找数组 tags 中包含 "red" 和 "blue" 的文档：

```text
db.myCollection.find({ tags: { $all: ["red", "blue"] } });
```


### $all (数组包含指定的所有元素)

语法格式：

```text
{ field: { $all: [value1, value2, ...] } }
```

查找 tags 数组中包含 "mongodb" 和 "database" 的文档:

```text
db.collection.find({ tags: { $all: ["mongodb", "database"] } })
```


### $elemMatch (数组中至少有一个元素符合条件)

```text
{ field: { $elemMatch: { condition } } }
```

查找 items 数组中 quantity 大于 10 的元素:

```text
db.collection.find({ items: { $elemMatch: { quantity: { $gt: 10 } } } })
```


### $size (数组的大小)

语法格式：

```text
{ field: { $size: value } }
```

查找 tags 数组大小为 3 的文档:

```text
db.collection.find({ tags: { $size: 3 } })
```


## 其他操作符

还有一些其他操作符如下：


### $regex (正则表达式匹配)

语法格式：

```text
{ field: { $regex: "pattern" } }
```

查找 name 以 "John" 开头的文档:

```text
db.collection.find({ name: { $regex: /^John/ } })
```


### $near (接近指定点的文档)

语法格式：

```text
{ field: { $near: [longitude, latitude], $maxDistance: distance } }
```

查找距离某个位置近的文档:

```text
db.collection.find({ location: { $near: [10, 20], $maxDistance: 1000 } })
```


## 后续章节

- $geoWithin (查找指定区域内的文档)

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MongoDB 条件操作符` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
