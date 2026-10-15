# MongoDB：MongoDB 正则表达式

- 来源：[MongoDB 正则表达式](https://www.runoob.com/mongodb/mongodb-regular-expression.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：练习笔记
- 章节序号：1502

## 本章内容

正则表达式是使用单个字符串来描述、匹配一系列符合某个句法规则的字符串。

许多程序设计语言都支持利用正则表达式进行字符串操作。

MongoDB 使用 $regex 操作符来设置匹配字符串的正则表达式。

MongoDB使用PCRE (Perl Compatible Regular Expression) 作为正则表达式语言。

不同于全文检索，我们使用正则表达式不需要做任何配置。

考虑以下 posts 集合的文档结构，该文档包含了文章内容和标签：

```text
{
   "post_text": "enjoy the mongodb articles on runoob",
   "tags": [
      "mongodb",
      "runoob"
   ]
}
```


## 使用正则表达式

以下命令使用正则表达式查找包含 runoob 字符串的文章：

```text
>db.posts.find({post_text:{$regex:"runoob"}})
```

以上查询也可以写为：

```text
>db.posts.find({post_text:/runoob/})
```


## 不区分大小写的正则表达式

如果检索需要不区分大小写，我们可以设置 $options 为 $i。

以下命令将查找不区分大小写的字符串 runoob：

```text
>db.posts.find({post_text:{$regex:"runoob",$options:"$i"}})
```

集合中会返回所有包含字符串 runoob 的数据，且不区分大小写：

```text
{
   "_id" : ObjectId("53493d37d852429c10000004"),
   "post_text" : "hey! this is my post on  runoob",
   "tags" : [ "runoob" ]
}
```


## 数组元素使用正则表达式

我们还可以在数组字段中使用正则表达式来查找内容。 这在标签的实现上非常有用，如果你需要查找包含以 run 开头的标签数据(ru 或 run 或 runoob)， 你可以使用以下代码：

```text
>db.posts.find({tags:{$regex:"run"}})
```


## 优化正则表达式查询

- 如果你的文档中字段设置了索引，那么使用索引相比于正则表达式匹配查找所有的数据查询速度更快。
- 如果正则表达式是前缀表达式，所有匹配的数据将以指定的前缀字符串为开始。例如： 如果正则表达式为 ^tut ，查询语句将查找以 tut 为开头的字符串。

这里面使用正则表达式有两点需要注意：

正则表达式中使用变量。一定要使用eval将组合的字符串进行转换，不能直接将字符串拼接后传入给表达式。否则没有报错信息，只是结果为空！实例如下：

```javascript
var name=eval("/" + 变量值key +"/i");
```

以下是模糊查询包含title关键词, 且不区分大小写:

```text
title:eval("/"+title+"/i")    // 等同于 title:{$regex:title,$Option:"$i"}
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MongoDB 正则表达式` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
