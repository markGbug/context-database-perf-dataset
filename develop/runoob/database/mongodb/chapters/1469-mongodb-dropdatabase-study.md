# MongoDB：MongoDB 删除数据库

- 来源：[MongoDB 删除数据库](https://www.runoob.com/mongodb/mongodb-dropdatabase.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：学习笔记
- 章节序号：1469

## 本章内容

### 语法

MongoDB 删除数据库的语法格式如下：

```text
db.dropDatabase()
```

删除当前数据库，默认为 test，你可以使用 db 命令查看当前数据库名。


### 实例

以下实例我们删除了数据库 runoob。

首先，查看所有数据库：

```text
> show dbs
admin   0.000GB
config  0.000GB
local   0.000GB
runoob  0.000GB
```

接下来我们切换到数据库 runoob：

```text
> use runoob
switched to db runoob
>
```

执行删除命令：

```text
> db.dropDatabase()
{ "dropped" : "runoob", "ok" : 1 }
```

最后，我们再通过 show dbs 命令数据库是否删除成功：

```text
> show dbs
admin   0.000GB
config  0.000GB
local   0.000GB
```


### 删除集合

集合删除语法格式如下：

```text
db.collection.drop()
```

以下实例删除了 runoob 数据库中的集合 site：

```text
> use runoob
switched to db runoob
> db.createCollection("runoob")     # 先创建集合，类似数据库中的表
> show tables             # show collections 命令会更加准确点
runoob
> db.runoob.drop()
true
> show tables
>
```


## 复习重点

- 能说明 `MongoDB 删除数据库` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
