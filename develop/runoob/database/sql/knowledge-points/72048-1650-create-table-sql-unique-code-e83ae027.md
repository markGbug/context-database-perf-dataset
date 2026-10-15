# 知识点 72048：SQL：SQL UNIQUE - CREATE TABLE 时的 SQL UNIQUE 约束

- 来源：[SQL UNIQUE](https://www.runoob.com/sql/sql-unique.html)
- 来源章节：[1650-sql-unique-practice.md](../chapters/1650-sql-unique-practice.md)
- 分类：数据库
- 技术：SQL
- 所在小节：CREATE TABLE 时的 SQL UNIQUE 约束
- 知识类型：代码
- 原章节序号：1650

## 原文片段

```text
CREATE TABLE Persons (
    P_Id INT NOT NULL,
    LastName VARCHAR(255) NOT NULL,
    FirstName VARCHAR(255),
    Address VARCHAR(255),
    City VARCHAR(255),
    UNIQUE (P_Id)
);
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `CREATE TABLE 时的 SQL UNIQUE 约束` 这一小节和 `SQL UNIQUE` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
