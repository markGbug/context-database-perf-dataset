# XQuery：XQuery 语法

- 来源：[XQuery 语法](https://www.runoob.com/xquery/xquery-syntax.html)
- 分类：XML / Web Service
- 技术：XQuery
- 笔记类型：学习笔记
- 章节序号：4488

## 本章内容

XQuery 对大小写敏感，XQuery 的元素、属性以及变量必须是合法的 XML 名称。


## XQuery 的基础语法规则：

一些基本的语法规则：

- XQuery 对大小写敏感
- XQuery 的元素、属性以及变量必须是合法的 XML 名称。
- XQuery 字符串值可使用单引号或双引号。
- XQuery 变量由 "$" 并跟随一个名称来进行定义，举例，$bookstore
- XQuery 注释被 (: 和 :) 分割，例如，(: XQuery 注释 :)


## XQuery 条件表达式

"If-Then-Else" 可以在 XQuery 中使用。

请看下面的例子：

请注意 "If-Then-Else" 的语法：if 表达式后的圆括号是必需的。else 也是必需的，不过只写 "else ()" 也可以。

上面的例子的结果：


## XQuery 比较

在 XQuery 中，有两种方法来比较值。

- 通用比较：=, !=, <, <=, >, >=
- 值的比较：eq、ne、lt、le、gt、ge


### 这两种比较方法的差异如下：

请看下面的 XQuery 表达式：

如果 q 属性的值大于 10，上面的表达式的返回值为 true。

如下实例，如果仅返回一个 q，且它的值大于 10，那么表达式返回 true。如果不止一个 q 被返回，则会发生错误：


## 复习重点

- 能说明 `XQuery 语法` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
