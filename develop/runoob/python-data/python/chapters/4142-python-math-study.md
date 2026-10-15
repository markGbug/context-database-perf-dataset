# Python：Python math 模块

- 来源：[Python math](https://www.runoob.com/python3/python-math.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：学习笔记
- 章节序号：4142

## 本章内容

Python math 模块提供了大量常用数学函数，可用于完成：

- 三角函数计算（sin / cos / tan）
- 对数与指数运算（log / exp / pow）
- 取整与舍入（ceil / floor / trunc）
- 组合排列与阶乘（comb / perm / factorial）
- 距离与几何计算（dist / hypot / sqrt）

它是 Python 进行数学运算最常用的标准库之一。

就需要借助 math 模块完成。

math 模块下的函数，返回值均为浮点数，除非另有明确说明。

如果你需要计算复数，请使用 cmath 模块中的同名函数。

要使用 math 函数必须先导入：

```text
import math
```

查看 math 模块中的内容:


### 为什么使用 math 模块？

虽然 Python 自带许多基本运算符（如 +、-、*、/），但对于更复杂的数学计算，例如：

- 开平方
- 三角函数
- 自然对数
- 浮点精度处理


### Python math 模块使用示例

输出结果为：

```text
4.0
8.0
5
4
1.0
```


### math 模块常量


### math 模块函数


### 版本兼容说明

以下函数为 Python 3.8+ / 3.9+ / 3.11+ 新增：

- math.comb()：Python 3.8+
- math.perm()：Python 3.8+
- math.lcm()：Python 3.9+
- math.cbrt()：Python 3.11+
- math.exp2()：Python 3.11+
- math.sumprod()：Python 3.12+


## 复习重点

- 能说明 `Python math` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
