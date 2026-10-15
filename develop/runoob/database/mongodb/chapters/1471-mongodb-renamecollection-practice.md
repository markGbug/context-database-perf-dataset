# MongoDB：MongoDB 更新集合名

- 来源：[MongoDB 更新集合名](https://www.runoob.com/mongodb/mongodb-renamecollection.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：练习笔记
- 章节序号：1471

## 本章内容

在 MongoDB 中，不能直接通过命令来重命名集合。

MongoDB 可以使用 renameCollection 方法来来重命名集合。

renameCollection 方法在 MongoDB 的 admin 数据库中运行，可以将一个集合重命名为另一个名称。

renameCollection 命令的语法：

```html
db.adminCommand({
  renameCollection: "sourceDb.sourceCollection",
  to: "targetDb.targetCollection",
  dropTarget: <boolean>
})
```

参数说明：

- renameCollection：要重命名的集合的完全限定名称（包括数据库名）。
- to：目标集合的完全限定名称（包括数据库名）。
- dropTarget（可选）：布尔值。如果目标集合已经存在，是否删除目标集合。默认值为 false。


### 实例

假设你要将 test 数据库中的 oldCollection 重命名为 newCollection，可以按以下步骤进行：

1. 确保已连接到 test 数据库

```text
use test
```

2. 运行 renameCollection 命令

```text
db.adminCommand({
  renameCollection: "test.oldCollection",
  to: "test.newCollection"
});
```

如果你要将集合重命名到另一个数据库，例如将 test 数据库中的 oldCollection 重命名为 production 数据库中的 newCollection，可以这样做：

```text
db.adminCommand({
  renameCollection: "test.oldCollection",
  to: "production.newCollection"
});
```


### 注意事项

- 权限要求：执行 renameCollection 命令需要具有对源数据库和目标数据库的适当权限。通常需要 dbAdmin 或 dbOwner 角色。
- 目标集合不存在：目标集合不能已经存在。如果目标集合存在，则会返回错误。
- 索引和数据：重命名集合会保留所有文档和索引。


### 检查重命名结果

重命名后，可以通过以下命令检查新的集合是否存在：

```text
use test
show collections
```

如果集合已重命名为 newCollection，你应该会在结果中看到 newCollection。


### 处理重命名失败的情况

如果重命名过程中发生错误，你可以根据错误消息采取相应的措施。例如，如果目标集合已经存在，可以先删除目标集合（如果确认不需要），然后重新执行重命名操作：


## 实例

通过 renameCollection 方法，你可以有效地管理 MongoDB 集合的名称，确保数据库结构符合应用需求。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MongoDB 更新集合名` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
