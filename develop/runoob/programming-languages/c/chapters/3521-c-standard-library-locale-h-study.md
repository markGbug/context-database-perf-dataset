# C：C 标准库 - <locale.h>

- 来源：[C 标准库 - <locale.h>](https://www.runoob.com/cprogramming/c-standard-library-locale-h.html)
- 分类：编程语言
- 技术：C
- 笔记类型：学习笔记
- 章节序号：3521

## 本章内容

## 简介

<locale.h> 是 C 标准库中的一个头文件，用于支持程序的国际化和本地化。它提供了一组函数和宏来设置或查询程序的本地化信息，例如日期、时间、货币、数字格式等。

接下来我们将介绍一些宏，以及一个重要的结构 struct lconv 和两个重要的函数。


## 库宏

下面列出了头文件 locale.h 中定义的宏，这些宏将在下列的两个函数中使用：


## 库函数

下面列出了头文件 locale.h 中定义的函数：


### 实例

设置和查询本地化信息:


## 实例

编译输出结果为：

```text
Current locale for LC_ALL: zh_CN.UTF-8
Current locale for LC_TIME: zh_CN.UTF-8
Current locale for LC_NUMERIC: zh_CN.UTF-8
```

获取数字和货币格式信息:


## 实例

编译输出结果为：

```java
Decimal point character: .
Thousands separator: ,
Currency symbol: ￥
```

使用自定义本地化对象:


## 实例

编译输出结果为：

```text
Current locale for LC_NUMERIC: C
```


## 复习重点

- 能说明 `C 标准库 - <locale.h>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
