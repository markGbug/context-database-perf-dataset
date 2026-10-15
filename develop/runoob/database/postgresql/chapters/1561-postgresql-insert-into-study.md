# PostgreSQL：PostgreSQL INSERT INTO 语句

- 来源：[PostgreSQL INSERT INTO](https://www.runoob.com/postgresql/postgresql-insert-into.html)
- 分类：数据库
- 技术：PostgreSQL
- 笔记类型：学习笔记
- 章节序号：1561

## 本章内容

PostgreSQL INSERT INTO 语句用于向表中插入新记录。

我们可以插入一行也可以同时插入多行。


### 语法

INSERT INTO 语句语法格式如下：

```text
INSERT INTO TABLE_NAME (column1, column2, column3,...columnN)
VALUES (value1, value2, value3,...valueN);
```

- column1, column2,...columnN 为表中字段名。
- value1, value2, value3,...valueN 为字段对应的值。

在使用 INSERT INTO 语句时，字段列必须和数据值数量相同，且顺序也要对应。

如果我们向表中的所有字段插入值，则可以不需要指定字段，只需要指定插入的值即可：

```text
INSERT INTO TABLE_NAME VALUES (value1,value2,value3,...valueN);
```

下表列出执行插入后返回结果的说明：

INSERT oid 1

只插入一行并且目标表具有 OID的返回信息， 那么 oid 是分配给被插入行的 OID。

INSERT 0 #

插入多行返回的信息， # 为插入的行数。


### 实例

在 runoobdb 数据库中创建 COMPANY 表：

```text
runoobdb=# CREATE TABLE COMPANY(
   ID INT PRIMARY KEY     NOT NULL,
   NAME           TEXT    NOT NULL,
   AGE            INT     NOT NULL,
   ADDRESS        CHAR(50),
   SALARY         REAL,
   JOIN_DATE      DATE
);
```

在 COMPANY 表中插入以下数据：

```text
runoobdb=# INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY,JOIN_DATE) VALUES (1, 'Paul', 32, 'California', 20000.00,'2001-07-13');
INSERT 0 1
```

以下插入语句忽略 SALARY 字段：

```text
runoobdb=# INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,JOIN_DATE) VALUES (2, 'Allen', 25, 'Texas', '2007-12-13');
INSERT 0 1
```

以下插入语句 JOIN_DATE 字段使用 DEFAULT 子句来设置默认值，而不是指定值：

```text
runoobdb=# INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY,JOIN_DATE) VALUES (3, 'Teddy', 23, 'Norway', 20000.00, DEFAULT );
INSERT 0 1
```

以下实例插入多行：

```text
runoobdb=# INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY,JOIN_DATE) VALUES (4, 'Mark', 25, 'Rich-Mond ', 65000.00, '2007-12-13' ), (5, 'David', 27, 'Texas', 85000.00, '2007-12-13');
INSERT 0 2
```

使用 SELECT 语句查询表格数据：

```text
runoobdb=# SELECT * FROM company;

ID        NAME        AGE        ADDRESS     SALARY   JOIN_DATE
----      ----------  -----      ----------  -------      --------
1         Paul        32         California  20000.0      2001-07-13
2         Allen       25         Texas                    2007-12-13
3         Teddy       23         Norway      20000.0
4         Mark        25         Rich-Mond   65000.0      2007-12-13
5         David       27         Texas       85000.0      2007-12-13
```


## 复习重点

- 能说明 `PostgreSQL INSERT INTO` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
