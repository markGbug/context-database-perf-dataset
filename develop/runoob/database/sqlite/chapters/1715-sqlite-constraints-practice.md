# SQLite：SQLite 约束

- 来源：[SQLite 约束](https://www.runoob.com/sqlite/sqlite-constraints.html)
- 分类：数据库
- 技术：SQLite
- 笔记类型：练习笔记
- 章节序号：1715

## 本章内容

约束（Constraint）是数据库表中用于限制数据的规则，可以帮助保证数据的完整性、一致性和可靠性。

例如，可以通过约束要求员工姓名不能为空、邮箱不能重复、工资必须大于零，或者规定某个字段必须引用另一张表中存在的记录。

SQLite 支持多种约束，常见的包括：

- NOT NULL：限制列不能存储 NULL 值。
- DEFAULT：插入数据时未指定列值，则使用默认值。
- UNIQUE：要求指定列或列组合中的值保持唯一。
- PRIMARY KEY：为表中的记录定义主键。
- CHECK：要求数据满足指定的条件表达式。
- FOREIGN KEY：建立表之间的引用关系，维护引用完整性。

约束通常在执行 CREATE TABLE 创建表时定义，也可以通过相应的表结构修改操作进行调整。


## SQLite 约束的基本语法

SQLite 支持列级约束和表级约束。

列级约束直接写在列定义后面，例如：

```text
CREATE TABLE COMPANY (
    ID INTEGER PRIMARY KEY,
    NAME TEXT NOT NULL,
    AGE INTEGER CHECK (AGE >= 18),
    SALARY REAL DEFAULT 50000.00
);
```

表级约束写在所有列定义之后，通常用于多个列共同参与约束的情况。

```text
CREATE TABLE EMPLOYEE (
    ID INTEGER PRIMARY KEY,
    NAME TEXT NOT NULL,
    DEPARTMENT TEXT NOT NULL,
    EMPLOYEE_NO TEXT NOT NULL,
    UNIQUE (DEPARTMENT, EMPLOYEE_NO)
);
```

上面的 UNIQUE (DEPARTMENT, EMPLOYEE_NO) 要求部门与员工编号的组合不能重复。

需要注意，SQLite 中的 NOT NULL 只能作为列约束声明，而 UNIQUE、CHECK 和 PRIMARY KEY 等可以根据用途采用列级或表级写法。


## NOT NULL 约束

默认情况下，SQLite 表中的普通列允许存储 NULL。

如果某列必须提供有效值，可以使用 NOT NULL 约束。

NULL 表示缺失或未知的值，不等于数字 0，也不等于空字符串 ''。


### 实例

下面创建一个 COMPANY 表，要求员工姓名和年龄不能为空。


## 实例

插入正常数据：

```text
INSERT INTO COMPANY (NAME, AGE, ADDRESS, SALARY)
VALUES ('Zhang San', 28, 'Beijing', 60000);
```

插入成功后，可以通过以下语句查询：

```text
SELECT * FROM COMPANY;
```

查询结果：

如果尝试插入 NAME 为 NULL 的记录：

```text
INSERT INTO COMPANY (NAME, AGE)
VALUES (NULL, 25);
```

SQLite 会拒绝该操作，错误信息类似：

```java
NOT NULL constraint failed: COMPANY.NAME
```

注意：NOT NULL 只能阻止 NULL，不能阻止空字符串。

例如，下面的语句不会因为 NOT NULL 而失败：

```text
INSERT INTO COMPANY (NAME, AGE)
VALUES ('', 25);
```

如果还要求姓名不能为空字符串，可以结合 CHECK 约束进行限制。


## DEFAULT 约束

DEFAULT 用于指定列的默认值。

当 INSERT INTO 语句没有提供某列的值时，SQLite 会使用该列的默认值。


### 实例

下面创建 COMPANY 表，将 SALARY 的默认值设置为 50000.00。


## 实例

插入数据时不指定工资：

```text
INSERT INTO COMPANY (NAME, AGE)
VALUES ('Li Si', 30);

SELECT ID, NAME, SALARY FROM COMPANY;
```

查询结果：

需要注意，没有提供列值与显式提供 NULL 是两种不同情况。

例如：

```text
INSERT INTO COMPANY (NAME, AGE, SALARY)
VALUES ('Wang Wu', 26, NULL);
```

这条语句明确将工资设置为 NULL，不会使用默认值 50000.00。

如果不允许工资为 NULL，可以组合使用：

```text
SALARY REAL NOT NULL DEFAULT 50000.00
```


### 使用日期作为默认值

SQLite 还支持 CURRENT_DATE、CURRENT_TIME 和 CURRENT_TIMESTAMP 等默认值。

```text
CREATE TABLE LOGS (
    ID INTEGER PRIMARY KEY,
    MESSAGE TEXT NOT NULL,
    CREATED_AT TEXT DEFAULT CURRENT_TIMESTAMP
);
```

插入日志时，不必手动指定创建时间：

```text
INSERT INTO LOGS (MESSAGE)
VALUES ('User logged in');
```

CURRENT_TIMESTAMP 通常生成 UTC 时间，格式为 YYYY-MM-DD HH:MM:SS。


## UNIQUE 约束

UNIQUE 约束用于保证指定列或多个列的组合不出现重复值。

例如，在员工表中，可以要求邮箱地址保持唯一。


### 实例


## 实例

插入第一条记录：

```text
INSERT INTO COMPANY (NAME, EMAIL)
VALUES ('Zhang San', 'zhang@example.com');
```

再次插入相同邮箱：

```text
INSERT INTO COMPANY (NAME, EMAIL)
VALUES ('Li Si', 'zhang@example.com');
```

第二次插入会失败，错误信息类似：

```java
UNIQUE constraint failed: COMPANY.EMAIL
```


### UNIQUE 允许多个 NULL

SQLite 的 UNIQUE 约束允许多个 NULL 值，因为在唯一性检查中，NULL 被视为彼此不同。

例如：

```text
INSERT INTO COMPANY (NAME, EMAIL)
VALUES ('Wang Wu', NULL);

INSERT INTO COMPANY (NAME, EMAIL)
VALUES ('Zhao Liu', NULL);
```

以上两条记录都可以成功插入。

如果希望邮箱既不能为空，又不能重复，可以使用：

```text
EMAIL TEXT NOT NULL UNIQUE
```


### 组合唯一约束

如果需要保证多个列的组合不重复，可以使用表级 UNIQUE 约束。


## 实例

这表示同一个部门内不能出现重复的员工编号，但不同部门可以使用相同的员工编号。

如果组合中的列允许 NULL，需要额外考虑 SQLite 对 NULL 的唯一性处理规则。业务上要求完整组合唯一时，通常应该同时声明 NOT NULL。


## PRIMARY KEY 约束

PRIMARY KEY 用于指定表的主键，通常用于唯一标识每一条记录。

一个表最多只能定义一个主键，但主键可以由一个或多个列组成。

在 SQLite 中，主键有一些需要特别注意的实现细节。


### INTEGER PRIMARY KEY

对于普通的 SQLite 行表，如果将一个列声明为 INTEGER PRIMARY KEY，该列通常会成为表的 rowid 别名。

例如：


## 实例

查询结果：

由于没有显式指定 ID，SQLite 会自动为记录选择合适的整数主键值。

这里的自动生成不等于一定连续递增，也不保证已删除的编号永远不会再次使用。


### INT PRIMARY KEY 与 INTEGER PRIMARY KEY 的区别

在 SQLite 中，INT PRIMARY KEY 和 INTEGER PRIMARY KEY 并不完全相同。

因此，如果希望在 SQLite 普通行表中使用常见的自动整数主键，通常推荐：

```text
ID INTEGER PRIMARY KEY
```


### SQLite 主键允许 NULL 的特殊情况

根据 SQL 标准，主键列应当不允许 NULL。

但 SQLite 为了兼容早期版本，保留了一个特殊行为：在普通行表中，某些非 INTEGER PRIMARY KEY 的主键列可能允许 NULL。

例如：

```text
CREATE TABLE TEST_PK (
    ID INT PRIMARY KEY,
    NAME TEXT
);

INSERT INTO TEST_PK (ID, NAME)
VALUES (NULL, 'Test');
```

在普通 SQLite 行表中，上述插入可以成功。

以下情况则不适用这一宽松规则：

- 主键列声明了 NOT NULL。
- 使用了符合特殊规则的 INTEGER PRIMARY KEY。
- 表使用 WITHOUT ROWID。
- 表使用 STRICT 模式。

因此，创建普通非整数主键时，如果要求主键不能为空，建议明确添加 NOT NULL。


### 复合主键

一个主键还可以由多个列组成，这种主键称为复合主键（Composite Primary Key）。


## 实例

该表允许一个订单包含多个商品，但同一订单中不能存在重复的商品编号组合。

这里明确为两个主键列添加了 NOT NULL，避免 SQLite 普通行表的 NULL 兼容行为影响数据完整性。


## CHECK 约束

CHECK 约束用于限制数据必须满足指定的条件表达式。

例如，可以要求员工年龄不小于 18，工资必须大于零。


### 实例


## 实例

插入正常数据：

```text
INSERT INTO COMPANY (NAME, AGE, SALARY)
VALUES ('Zhang San', 28, 60000);
```

如果尝试插入负数工资：

```text
INSERT INTO COMPANY (NAME, AGE, SALARY)
VALUES ('Li Si', 30, -1000);
```

将产生类似错误：

```java
CHECK constraint failed: SALARY > 0
```


## 后续章节

- CHECK 与 NULL
- 表级 CHECK 约束
- 实例
- FOREIGN KEY 外键约束
- 启用外键检查
- 实例
- 实例
- 外键删除规则
- 组合使用多个约束
- 实例
- 删除或修改约束
- 实例：删除 UNIQUE 约束
- 实例
- 添加约束
- 通过唯一索引实现唯一性
- 约束冲突处理

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SQLite 约束` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
