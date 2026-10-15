# 知识点 33525：PostgreSQL：PostgreSQL AUTO INCREMENT - 本章内容

- 来源：[PostgreSQL AUTO INCREMENT](https://www.runoob.com/postgresql/postgresql-autoincrement.html)
- 来源章节：[1589-postgresql-autoincrement-practice.md](../chapters/1589-postgresql-autoincrement-practice.md)
- 分类：数据库
- 技术：PostgreSQL
- 所在小节：本章内容
- 知识类型：代码
- 原章节序号：1589

## 原文片段

```text
CREATE TABLE IF NOT EXISTS `runoob_tbl`(
   `runoob_id` INT UNSIGNED AUTO_INCREMENT,
   `runoob_title` VARCHAR(100) NOT NULL,
   `runoob_author` VARCHAR(40) NOT NULL,
   `submission_date` DATE,
   PRIMARY KEY ( `runoob_id` )
)ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `本章内容` 这一小节和 `PostgreSQL AUTO INCREMENT` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
