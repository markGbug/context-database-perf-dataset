# 知识点 89904：MongoDB：MongoDB Limit 与 Skip 方法 - 实例

- 来源：[MongoDB Limit 与 Skip 方法](https://www.runoob.com/mongodb/mongodb-limit-skip.html)
- 来源章节：[1479-mongodb-limit-skip-study.md](../chapters/1479-mongodb-limit-skip-study.md)
- 分类：数据库
- 技术：MongoDB
- 所在小节：实例
- 知识类型：代码
- 原章节序号：1479

## 原文片段

```text
> db.col.find({},{"title":1,_id:0}).limit(2)
{ "title" : "PHP 教程" }
{ "title" : "Java 教程" }
>
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `实例` 这一小节和 `MongoDB Limit 与 Skip 方法` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
