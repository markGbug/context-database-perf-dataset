# 知识点 62685：SQL：SQL PRIMARY KEY - CREATE TABLE 时的 SQL PRIMARY KEY 约束

- 来源：[SQL PRIMARY KEY](https://www.runoob.com/sql/sql-primarykey.html)
- 来源章节：[1651-sql-primarykey-practice.md](../chapters/1651-sql-primarykey-practice.md)
- 分类：数据库
- 技术：SQL
- 所在小节：CREATE TABLE 时的 SQL PRIMARY KEY 约束
- 知识类型：代码
- 原章节序号：1651

## 原文片段

```text
CREATE TABLE Persons
(
    P_Id int NOT NULL PRIMARY KEY,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255)
)
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `CREATE TABLE 时的 SQL PRIMARY KEY 约束` 这一小节和 `SQL PRIMARY KEY` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
