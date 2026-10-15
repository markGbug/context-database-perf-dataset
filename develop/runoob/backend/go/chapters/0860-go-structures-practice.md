# Go：Go 语言结构体

- 来源：[Go 语言结构体](https://www.runoob.com/go/go-structures.html)
- 分类：后端开发
- 技术：Go
- 笔记类型：练习笔记
- 章节序号：0860

## 本章内容

Go 语言中数组可以存储同一类型的数据，但在结构体中我们可以为不同项定义不同的数据类型。

结构体是由一系列具有相同类型或不同类型的数据构成的数据集合。

结构体表示一项记录，比如保存图书馆的书籍记录，每本书有以下属性：

- Title ：标题
- Author ： 作者
- Subject：学科
- ID：书籍ID


## 定义结构体

结构体定义需要使用 type 和 struct 语句。struct 语句定义一个新的数据类型，结构体中有一个或多个成员。type 语句设定了结构体的名称。结构体的格式如下：

```text
type struct_variable_type struct {
   member definition
   member definition
   ...
   member definition
}
```

一旦定义了结构体类型，它就能用于变量的声明，语法格式如下：

```text
variable_name := structure_variable_type {value1, value2...valuen}
或
variable_name := structure_variable_type { key1: value1, key2: value2..., keyn: valuen}
```

实例如下：


## 实例

输出结果为：

```text
{Go 语言 www.runoob.com Go 语言教程 6495407}
{Go 语言 www.runoob.com Go 语言教程 6495407}
{Go 语言 www.runoob.com  0}
```


## 访问结构体成员

如果要访问结构体成员，需要使用点号 . 操作符，格式为：

```text
结构体.成员名"
```

结构体类型变量使用 struct 关键字定义，实例如下：


## 实例

以上实例执行运行结果为：

```text
Book 1 title : Go 语言
Book 1 author : www.runoob.com
Book 1 subject : Go 语言教程
Book 1 book_id : 6495407
Book 2 title : Python 教程
Book 2 author : www.runoob.com
Book 2 subject : Python 语言教程
Book 2 book_id : 6495700
```


## 结构体作为函数参数

你可以像其他数据类型一样将结构体类型作为参数传递给函数。并以以上实例的方式访问结构体变量：


## 实例

以上实例执行运行结果为：

```text
Book title : Go 语言
Book author : www.runoob.com
Book subject : Go 语言教程
Book book_id : 6495407
Book title : Python 教程
Book author : www.runoob.com
Book subject : Python 语言教程
Book book_id : 6495700
```


## 结构体指针

你可以定义指向结构体的指针类似于其他指针变量，格式如下：

```javascript
var struct_pointer *Books
```

以上定义的指针变量可以存储结构体变量的地址。查看结构体变量地址，可以将 & 符号放置于结构体变量前：

```text
struct_pointer = &Book1
```

使用结构体指针访问结构体成员，使用 "." 操作符：

```text
struct_pointer.title
```

接下来让我们使用结构体指针重写以上实例，代码如下：


## 实例

以上实例执行运行结果为：

```text
Book title : Go 语言
Book author : www.runoob.com
Book subject : Go 语言教程
Book book_id : 6495407
Book title : Python 教程
Book author : www.runoob.com
Book subject : Python 语言教程
Book book_id : 6495700
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Go 语言结构体` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
