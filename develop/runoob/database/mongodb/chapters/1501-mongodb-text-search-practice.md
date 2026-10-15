# MongoDB：MongoDB 全文检索

- 来源：[MongoDB 全文检索](https://www.runoob.com/mongodb/mongodb-text-search.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：练习笔记
- 章节序号：1501

## 本章内容

全文检索对每一个词建立一个索引，指明该词在文章中出现的次数和位置，当用户查询时，检索程序就根据事先建立的索引进行查找，并将查找的结果反馈给用户的检索方式。

这个过程类似于通过字典中的检索字表查字的过程。

MongoDB 从 2.4 版本开始支持全文检索，目前支持15种语言的全文索引。

- danish
- dutch
- english
- finnish
- french
- german
- hungarian
- italian
- norwegian
- portuguese
- romanian
- russian
- spanish
- swedish
- turkish


## 启用全文检索

MongoDB 在 2.6 版本以后是默认开启全文检索的，如果你使用之前的版本，你需要使用以下代码来启用全文检索:

```text
>db.adminCommand({setParameter:true,textSearchEnabled:true})
```

或者使用命令：

```text
mongod --setParameter textSearchEnabled=true
```


## 创建全文索引

考虑以下 posts 集合的文档数据，包含了文章内容（post_text）及标签(tags)：

```text
{
   "post_text": "enjoy the mongodb articles on Runoob",
   "tags": [
      "mongodb",
      "runoob"
   ]
}
```

我们可以对 post_text 字段建立全文索引，这样我们可以搜索文章内的内容：

```text
>db.posts.ensureIndex({post_text:"text"})
```


## 使用全文索引

现在我们已经对 post_text 建立了全文索引，我们可以搜索文章中的关键词 runoob：

```text
>db.posts.find({$text:{$search:"runoob"}})
```

以下命令返回了如下包含 runoob 关键词的文档数据：

```text
{
   "_id" : ObjectId("53493d14d852429c10000002"),
   "post_text" : "enjoy the mongodb articles on Runoob",
   "tags" : [ "mongodb", "runoob" ]
}
```

如果你使用的是旧版本的 MongoDB，你可以使用以下命令：

```text
>db.posts.runCommand("text",{search:"runoob"})
```

使用全文索引可以提高搜索效率。


## 删除全文索引

删除已存在的全文索引，可以使用 find 命令查找索引名：

```text
>db.posts.getIndexes()
```

通过以上命令获取索引名，本例的索引名为post_text_text，执行以下命令来删除索引：

```text
>db.posts.dropIndex("post_text_text")
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MongoDB 全文检索` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
