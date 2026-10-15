# Pandas：Pandas 数据重塑（pivot / melt / stack / unstack）

- 来源：[Pandas 数据重塑](https://www.runoob.com/pandas/pandas-pivot.html)
- 分类：Python / 数据科学
- 技术：Pandas
- 笔记类型：练习笔记
- 章节序号：4039

## 本章内容

数据重塑是数据分析中的常见操作，用于改变数据的布局结构。Pandas 提供了 pivot、melt、stack、unstack 等函数来实现长格式和宽格式之间的转换。


## pivot 透视表

pivot 将长格式数据转换为宽格式，类似于 Excel 的透视表功能。


### 基本用法


## 实例


### 多重索引


## 实例


### 聚合函数


## 实例

pivot 不允许有重复值，有重复值时使用 pivot_table 并指定聚合函数。


## melt 逆透视

melt 将宽格式数据转换为长格式，是 pivot 的逆操作。


## 实例


### 保持多列不变


## 实例


## stack 与 unstack

stack 和 unstack 是 MultiIndex 专用的重塑函数。


### unstack


## 实例


### stack


## 实例


## 实战：业务报表转换


## 实例


## 重塑函数选择

数据重塑的目的是为了让数据更适合分析或展示。根据下游需求选择合适的转换方式。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pandas 数据重塑` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
