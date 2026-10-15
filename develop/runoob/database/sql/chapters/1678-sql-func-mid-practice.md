# SQL：SQL MID() 函数

- 来源：[SQL MID()](https://www.runoob.com/sql/sql-func-mid.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：练习笔记
- 章节序号：1678

## 本章内容

## MID() 函数

MID() 函数用于从文本字段中提取字符。


### SQL MID() 语法


## 演示数据库

在本教程中，我们将使用 RUNOOB 样本数据库。

下面是选自 "Websites" 表的数据：

```text
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
| 7  | stackoverflow | http://stackoverflow.com/ |   0 | IND     |
+----+---------------+---------------------------+-------+---------+
```


## SQL MID() 实例

下面的 SQL 语句从 "Websites" 表的 "name" 列中提取前 4 个字符：


## 实例

执行以上 SQL 输出结果如下：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SQL MID()` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
