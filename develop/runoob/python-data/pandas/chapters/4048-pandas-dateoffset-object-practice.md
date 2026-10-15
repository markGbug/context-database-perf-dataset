# Pandas：Pandas DateOffset 对象

- 来源：[Pandas DateOffset 对象](https://www.runoob.com/pandas/pandas-dateoffset-object.html)
- 分类：Python / 数据科学
- 技术：Pandas
- 笔记类型：练习笔记
- 章节序号：4048

## 本章内容

Pandas 的 DateOffset 对象是用于处理日期和时间数据时进行时间偏移的一种工具。

以下是 DateOffset 的一些关键特性和用法：


### 基本概念

DateOffset 对象类似于 Timedelta，但它遵循日历中的日期时间规则，而不是直接进行时间性质的算术计算，这意味着 DateOffset 会考虑到实际的日历天数，例如在处理跨月或跨年的日期时，它会正确地计算天数差异，而 Timedelta 则是简单地加上指定的天数，不考虑月份和年份的变化。


### 使用方法

DateOffset 可以通过算数运算符（如 +）或 apply 方法来执行日期偏移操作。

例如，你可以这样使用 DateOffset 来增加月份或小时：


## 实例

如果不指定任何参数，DateOffset() 默认增加一个日历日：

```text
ts + DateOffset()  # 默认增加一天
```


### 支持的参数

DateOffset 支持多种参数，可以指定增加或替换的时间单位，如年、月、周、日、小时、分钟、秒等。这些参数可以是增加到偏移值的（如 years、months、weeks、days、hours、minutes、seconds 等），也可以是替换偏移值的（如 year、month、day、weekday、hour、minute、second 等）。


### 特殊方法

DateOffset 还提供了 rollforward() 和 rollback() 方法，用于将日期向前或向后滚动到最近的一个有效日期。例如，如果你使用工作日偏移（BDay），它会跳过周末，直接滚动到下一个工作日。


## 实例


### 频率字符串

DateOffset 支持频率字符串或偏移别名，可以作为 freq 参数传入。这些频率字符串表示的是 DateOffset 对象及其子类，它们定义了日期时间索引的频率。

DateOffset 是 Pandas 中处理时间序列数据时非常有用的工具，它使得日期和时间的偏移操作更加符合实际日历规则。


## 常用函数


### DateOffset 构造函数


### 常用 DateOffset 子类


### DateOffset 属性


### DateOffset 方法


### 实例


## 实例


### 详细参数说明

如果需要更详细的信息，可以参考 Pandas 官方文档。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pandas DateOffset 对象` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
