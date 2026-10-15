# C#：C# 可空类型（Nullable）

- 来源：[C# 可空类型](https://www.runoob.com/csharp/csharp-nullable.html)
- 分类：后端开发
- 技术：C#
- 笔记类型：概念卡
- 章节序号：0764

## 本章内容

在 C# 中，int、float、bool、DateTime 等都是值类型，它们默认必须有一个值，不能为 null：

```java
int a = null;  // 编译错误：无法将 null 转换为 int
```

可空类型（Nullable Types） 解决了这个问题——它让值类型额外拥有一个"没有值"的状态（即 null），在处理数据库字段、API 返回值等可能缺失数据的场景中非常实用。

声明方式很简单，在类型后面加一个 ?：

```text
int? a = null;  // 合法
int? b = 42;    // 合法
```

这里的 int? 是 Nullable<int> 的语法糖（简写形式），两者完全等价：

```html
Nullable<int> a = null;   // 完整写法
int? a = null;              // 简写，效果相同
```

下图展示了可空类型在内存中的工作方式——它用一个额外的布尔标记来记录"是否有值"：


## 单问号 ? 与双问号 ?? 的区别

C# 中与可空类型相关的两个运算符经常一起使用，但含义完全不同：

一个简单的对比：

```java
int i;     // 普通值类型，默认值为 0，永远不能是 null
int? ii;   // 可空类型，默认值为 null
```


## 可空类型的声明与赋值


### 声明语法

```html
<data_type>? <variable_name> = null;
```

例如：

```text
int? age = null;
double? temperature = 36.6;
bool? isActive = new bool?();   // 显式构造，默认为 null
DateTime? birthday = null;
```

Nullable<T> 可以表示其基础值类型的正常范围，再加上一个 null 值。例如 Nullable<int> 可以是 -2,147,483,648 到 2,147,483,647 之间的任意整数，或者 null。


### 完整示例


## 实例

输出结果：

```text
num1 = 0
num2 = 45
num3 = 0
num4 = 3.14157
boolVal =
```


## Null 合并运算符（??）

?? 运算符用于为可空类型或引用类型提供一个兜底默认值。当左侧不为 null 时返回左侧值，否则返回右侧值：

```text
<表达式1> ?? <表达式2>
```

- 如果 <表达式1> 不为 null，返回 <表达式1>；
- 否则返回 <表达式2>。

从 C# 8.0 起，还可以使用 ??=（空合并赋值运算符），仅当变量为 null 时才赋值：

```text
int? x = null;
x ??= 10;   // x 为 null，赋值为 10
x ??= 20;   // x 已有值 10，不再赋值
```


## 实例

输出结果：

```text
num1 ?? 5.34 = 5.34
num2 ?? 5.34 = 3.14157
a ?? b ?? c ?? 0 = 42
```


## 可空类型的常用属性和方法


## 实例


## 实际应用场景

可空类型在实际开发中非常常见，尤其是处理可能缺失的数据时：


### 数据库字段映射

数据库中的字段允许为 NULL，用可空类型可以精确对应：

```text
int? age = GetUserAgeFromDB(userId: 2);

// 安全处理 null
string display = age.HasValue
    ? $"用户年龄：{age.Value}"
    : "年龄未知";

// 或者更简洁的写法
string display2 = $"用户年龄：{age ?? 0}";
```


### 可选参数与配置

```java
// 配置项可能未设置
int? timeout = GetConfigValue("timeout");
int actualTimeout = timeout ?? 30;  // 未设置时使用默认值 30 秒
```


### 链式空值检查（C# 6.0+）

```text
// 使用 ?. 运算符安全访问可能为 null 的对象
string? name = user?.Address?.City?.Name;
// 如果 user、Address、City 中任何一个为 null，结果就是 null，不会抛异常
```


## 小结


## C# 8.0 的"可空引用类型"

从 C# 8.0 开始，引入了 可空引用类型（Nullable Reference Types），它与本文介绍的可空值类型是两套不同的机制：

可空引用类型是编译期的安全检查工具——它不会改变程序的运行时行为，但会在代码可能产生 NullReferenceException 的地方发出编译器警告，帮助你在开发阶段就发现潜在问题。


## 记忆卡片

- 一句话定义：`C# 可空类型` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
