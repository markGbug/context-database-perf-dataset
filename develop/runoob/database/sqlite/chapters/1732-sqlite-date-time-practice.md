# SQLite：SQLite 日期 & 时间

- 来源：[SQLite 日期 & 时间](https://www.runoob.com/sqlite/sqlite-date-time.html)
- 分类：数据库
- 技术：SQLite
- 笔记类型：练习笔记
- 章节序号：1732

## 本章内容

SQLite 支持以下五个日期和时间函数：

上述五个日期和时间函数把时间字符串作为参数。时间字符串后跟零个或多个 modifier 修饰符。strftime() 函数也可以把格式字符串 format 作为其第一个参数。下面将为您详细讲解不同类型的时间字符串和修饰符。


## 时间字符串

一个时间字符串可以采用下面任何一种格式：

您可以使用 "T" 作为分隔日期和时间的文字字符。


## 修饰符（Modifier）

时间字符串后边可跟着零个或多个的修饰符，这将改变有上述五个函数返回的日期和/或时间。任何上述五大功能返回时间。修饰符应从左到右使用，下面列出了可在 SQLite 中使用的修饰符：

- NNN days
- NNN hours
- NNN minutes
- NNN.NNNN seconds
- NNN months
- NNN years
- start of month
- start of year
- start of day
- weekday N
- unixepoch
- localtime
- utc


## 格式化

SQLite 提供了非常方便的函数 strftime() 来格式化任何日期和时间。您可以使用以下的替换来格式化日期和时间：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SQLite 日期 & 时间` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
