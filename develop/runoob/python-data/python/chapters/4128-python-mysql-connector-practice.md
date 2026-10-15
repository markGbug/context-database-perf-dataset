# Python：Python MySQL - mysql-connector 驱动

- 来源：[Python3 MySQL(mysql-connector)](https://www.runoob.com/python3/python-mysql-connector.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4128

## 本章内容

MySQL 是最流行的关系型数据库管理系统，如果你不熟悉 MySQL，可以阅读我们的 MySQL 教程。

本章节我们为大家介绍使用 mysql-connector 来连接使用 MySQL， mysql-connector 是 MySQL 官方提供的驱动器。

我们可以使用 pip 命令来安装 mysql-connector：

```text
python -m pip install mysql-connector
```

使用以下代码测试 mysql-connector 是否安装成功：


## demo_mysql_test.py:

```text
import mysql.connector
```

执行以上代码，如果没有产生错误，表明安装成功。

注意：如果你的 MySQL 是 8.0 版本，密码插件验证方式发生了变化，早期版本为 mysql_native_password，8.0 版本为 caching_sha2_password，所以需要做些改变：

先修改 my.ini 配置：

```text
[mysqld]
default_authentication_plugin=mysql_native_password
```

然后在 mysql 下执行以下命令来修改密码：

```text
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '新密码';
```

更多内容可以参考：Python MySQL8.0 链接问题。


## 创建数据库连接

可以使用以下代码来连接数据库：


## demo_mysql_test.py:

```text
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",       # 数据库主机地址
  user="yourusername",    # 数据库用户名
  passwd="yourpassword"   # 数据库密码
)

print(mydb)
```


### 创建数据库

创建数据库使用 "CREATE DATABASE" 语句，以下创建一个名为 runoob_db 的数据库：


## demo_mysql_test.py:

```text
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="root",
  passwd="123456"
)

mycursor = mydb.cursor()

mycursor.execute("CREATE DATABASE runoob_db")
```

创建数据库前我们也可以使用 "SHOW DATABASES" 语句来查看数据库是否存在：


## demo_mysql_test.py:

输出所有数据库列表：

```text
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="root",
  passwd="123456"
)

mycursor = mydb.cursor()

mycursor.execute("SHOW DATABASES")

for x in mycursor:
  print(x)
```

或者我们可以直接连接数据库，如果数据库不存在，会输出错误信息：


## demo_mysql_test.py:

```text
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="root",
  passwd="123456",
  database="runoob_db"
)
```


## 创建数据表

创建数据表使用 "CREATE TABLE" 语句，创建数据表前，需要确保数据库已存在，以下创建一个名为 sites 的数据表：


## demo_mysql_test.py:

```text
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="root",
  passwd="123456",
  database="runoob_db"
)
mycursor = mydb.cursor()

mycursor.execute("CREATE TABLE sites (name VARCHAR(255), url VARCHAR(255))")
```


## demo_mysql_test.py:

```text
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="root",
  passwd="123456",
  database="runoob_db"
)
mycursor = mydb.cursor()

mycursor.execute("SHOW TABLES")

for x in mycursor:
  print(x)
```


### 主键设置

创建表的时候我们一般都会设置一个主键（PRIMARY KEY），我们可以使用 "INT AUTO_INCREMENT PRIMARY KEY" 语句来创建一个主键，主键起始值为 1，逐步递增。

如果我们的表已经创建，我们需要使用 ALTER TABLE 来给表添加主键：


## demo_mysql_test.py:

给 sites 表添加主键。

```text
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="root",
  passwd="123456",
  database="runoob_db"
)
mycursor = mydb.cursor()

mycursor.execute("ALTER TABLE sites ADD COLUMN id INT AUTO_INCREMENT PRIMARY KEY")
```

如果你还未创建 sites 表，可以直接使用以下代码创建。


## demo_mysql_test.py:

给表创建主键。

```text
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="root",
  passwd="123456",
  database="runoob_db"
)
mycursor = mydb.cursor()

mycursor.execute("CREATE TABLE sites (id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(255), url VARCHAR(255))")
```


## 插入数据

插入数据使用 "INSERT INTO" 语句：


## demo_mysql_test.py:

向 sites 表插入一条记录。

```text
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="root",
  passwd="123456",
  database="runoob_db"
)
mycursor = mydb.cursor()

sql = "INSERT INTO sites (name, url) VALUES (%s, %s)"
val = ("RUNOOB", "https://www.runoob.com")
mycursor.execute(sql, val)

mydb.commit()    # 数据表内容有更新，必须使用到该语句

print(mycursor.rowcount, "记录插入成功。")
```

执行代码，输出结果为：

```text
1 记录插入成功
```


### 批量插入

批量插入使用 executemany() 方法，该方法的第二个参数是一个元组列表，包含了我们要插入的数据：


## demo_mysql_test.py:

向 sites 表插入多条记录。

```text
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="root",
  passwd="123456",
  database="runoob_db"
)
mycursor = mydb.cursor()

sql = "INSERT INTO sites (name, url) VALUES (%s, %s)"
val = [
  ('Google', 'https://www.google.com'),
  ('Github', 'https://www.github.com'),
  ('Taobao', 'https://www.taobao.com'),
  ('stackoverflow', 'https://www.stackoverflow.com/')
]

mycursor.executemany(sql, val)

mydb.commit()    # 数据表内容有更新，必须使用到该语句

print(mycursor.rowcount, "记录插入成功。")
```

执行代码，输出结果为：

```text
4 记录插入成功。
```

执行以上代码后，我们可以看看数据表的记录：

如果我们想在数据记录插入后，获取该记录的 ID ，可以使用以下代码：


## demo_mysql_test.py:

```text
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="root",
  passwd="123456",
  database="runoob_db"
)
mycursor = mydb.cursor()

sql = "INSERT INTO sites (name, url) VALUES (%s, %s)"
val = ("Zhihu", "https://www.zhihu.com")
mycursor.execute(sql, val)

mydb.commit()

print("1 条记录已插入, ID:", mycursor.lastrowid)
```

执行代码，输出结果为：

```text
1 条记录已插入, ID: 6
```


## 查询数据

查询数据使用 SELECT 语句：


## demo_mysql_test.py:

```text
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="root",
  passwd="123456",
  database="runoob_db"
)
mycursor = mydb.cursor()

mycursor.execute("SELECT * FROM sites")

myresult = mycursor.fetchall()     # fetchall() 获取所有记录

for x in myresult:
  print(x)
```

执行代码，输出结果为：

```text
(1, 'RUNOOB', 'https://www.runoob.com')
(2, 'Google', 'https://www.google.com')
(3, 'Github', 'https://www.github.com')
(4, 'Taobao', 'https://www.taobao.com')
(5, 'stackoverflow', 'https://www.stackoverflow.com/')
(6, 'Zhihu', 'https://www.zhihu.com')
```

也可以读取指定的字段数据：


## demo_mysql_test.py:

```text
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="root",
  passwd="123456",
  database="runoob_db"
)
mycursor = mydb.cursor()

mycursor.execute("SELECT name, url FROM sites")

myresult = mycursor.fetchall()

for x in myresult:
  print(x)
```

执行代码，输出结果为：

```text
('RUNOOB', 'https://www.runoob.com')
('Google', 'https://www.google.com')
('Github', 'https://www.github.com')
('Taobao', 'https://www.taobao.com')
('stackoverflow', 'https://www.stackoverflow.com/')
('Zhihu', 'https://www.zhihu.com')
```

如果我们只想读取一条数据，可以使用 fetchone() 方法：


## demo_mysql_test.py:

```text
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="root",
  passwd="123456",
  database="runoob_db"
)
mycursor = mydb.cursor()

mycursor.execute("SELECT * FROM sites")

myresult = mycursor.fetchone()

print(myresult)
```

执行代码，输出结果为：

```text
(1, 'RUNOOB', 'https://www.runoob.com')
```


### where 条件语句

如果我们要读取指定条件的数据，可以使用 where 语句：


## demo_mysql_test.py

读取 name 字段为 RUNOOB 的记录：

```text
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="root",
  passwd="123456",
  database="runoob_db"
)
mycursor = mydb.cursor()

sql = "SELECT * FROM sites WHERE name ='RUNOOB'"

mycursor.execute(sql)

myresult = mycursor.fetchall()

for x in myresult:
  print(x)
```

执行代码，输出结果为：

```text
(1, 'RUNOOB', 'https://www.runoob.com')
```

也可以使用通配符 %：


## 后续章节

- demo_mysql_test.py
- demo_mysql_test.py
- 排序
- demo_mysql_test.py
- demo_mysql_test.py
- Limit
- demo_mysql_test.py
- demo_mysql_test.py
- 删除记录
- demo_mysql_test.py
- demo_mysql_test.py
- 更新表数据
- demo_mysql_test.py
- demo_mysql_test.py
- 删除表
- demo_mysql_test.py

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python3 MySQL(mysql-connector)` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
