# R：R 判断语句

- 来源：[R 判断语句](https://www.runoob.com/r/r-decision-making.html)
- 分类：Python / 数据科学
- 技术：R
- 笔记类型：练习笔记
- 章节序号：4229

## 本章内容

判断结构要求程序员指定一个或多个要评估或测试的条件，以及条件为真时要执行的语句（必需的）和条件为假时要执行的语句（可选的）。

下面是大多数编程语言中典型的判断结构的一般形式：

R 语言提供了以下类型的判断语句：

- if 语句
- if...else 语句
- switch 语句


### if 语句

一个 if 语句 由一个布尔表达式后跟一个或多个语句组成。

```text
if(boolean_expression) {
    // 布尔表达式为真将执行的语句
}
```

如果布尔表达式 boolean_expression 为 ture 执行这里面的代码，如果 为 false 则不执行。


## 实例

执行以上代码，输出结果为：

```text
[1] "X 是一个整数"
```


### if...else 语句

一个 if 语句 后可跟一个可选的 else 语句，else 语句在布尔表达式为假时执行。

语法格式如下：

```text
if(boolean_expression) {
    // 如果布尔表达式为真将执行的语句
} else {
    // 如果布尔表达式为假将执行的语句
}
```

如果布尔表达式 boolean_expression 为 true，则执行 if 块内的代码。如果布尔表达式为 false，则执行 else 块内的代码。


## 实例

执行以上代码，输出结果为：

```text
[1] "包含 runoob"
```

如果有多个条件判断，可以使用 if...else if...else：

```text
if(boolean_expression 1) {
    // 如果布尔表达式 boolean_expression 1 为真将执行的语句
} else if( boolean_expression 2) {
    // 如果布尔表达式 boolean_expression 2 为真将执行的语句
} else if( boolean_expression 3) {
    // 如果布尔表达式 boolean_expression 3 为真将执行的语句
} else {
    // 以上所有的布尔表达式都为 false 时执行
}
```


## 实例

执行以上代码，输出结果为：

```text
[1] "第二个 if 包含 runoob"
```


### switch 语句

一个 switch 语句允许测试一个变量等于多个值时的情况。每个值称为一个 case。

语法格式如下：

```text
switch(expression, case1, case2, case3....)
```

switch 语句必须遵循下面的规则：

- switch 语句中的 expression 是一个常量表达式，可以是整数或字符串，如果是整数则返回对应的 case 位置值，如果整数不在位置的范围内则返回 NULL。
- 如果匹配到多个值则返回第一个。
- expression如果是字符串，则对应的是 case 中的变量名对应的值，没有匹配则没有返回值。
- switch 没有默认参数可用。


## 实例

执行以上代码，输出结果为：

```text
[1] "taobao"
```

如果是字符串返回字符串变量对应的值：


## 实例

执行以上代码，输出结果为：

```text
[1] "www.runoob.com"
```

如果整数不在范围内的则返回 NULL


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `R 判断语句` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
