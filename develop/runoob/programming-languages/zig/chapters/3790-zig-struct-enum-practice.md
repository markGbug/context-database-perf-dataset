# Zig：Zig 结构体和枚举

- 来源：[Zig 结构体和枚举](https://www.runoob.com/zig/zig-struct-enum.html)
- 分类：编程语言
- 技术：Zig
- 笔记类型：练习笔记
- 章节序号：3790

## 本章内容

在 Zig 编程语言中，结构体（struct）和枚举（enum）是两种基本的数据类型。

结构体和枚举是定义和使用自定义数据类型的两种主要方式。

结构体和枚举提供了更高层次的数据组织和类型安全，适用于不同的编程场景。

- 结构体（Struct）：用于将相关变量组合成一个复合数据类型。结构体可以包含字段和方法，适用于组织复杂的数据。
- 枚举（Enum）：用于定义一组命名的常量，可以是无值或带值的枚举。枚举适用于表示有限的离散值。


## 结构体（Struct）

结构体是一种复合数据类型，它允许将多个不同类型的数据项组合成一个单一的类型。

Zig 中结构体的语法如下：

```javascript
const structName = struct {
    field1: FieldType1,
    field2: FieldType2,
    // 其他字段
};
```

以下代码中，MyStruct 是一个结构体类型，它有三个字段：field1 是一个 32 位整数，field2 是一个双精度浮点数，field3 是一个指向字节数组的指针。

```javascript
struct MyStruct {
    field1: i32,
    field2: f64,
    field3: []const u8,
}
```


## 实例

编译执行以上代码，输出结果为：

```text
Name: Alice
Age: 30
```

要修改结构体中的字段，确保你使用 var 来定义结构体实例，以便能够修改字段值。如果你使用 const 定义结构体实例，则不能修改其字段值。


## 实例

编译执行以上代码，输出结果为：

```text
Initial Name: Alice
Initial Age: 30
Modified Name: Bob
Modified Age: 35
```


### 方法

在 Zig 中，结构体方法通过 fn 关键字定义，类似于其他编程语言中的类方法。


## 实例

编译执行以上代码，输出结果为：

```text
Area: 50
```


## 枚举（Enum）

枚举是一种数据类型，它由一组固定的常量值组成。

Zig 中枚举的语法如下：

```javascript
const enumName = enum {
    Variant1,
    Variant2,
    // 其他变体
};
```

以下代码中，MyEnum 是一个枚举类型，它有三个可能的值：Option1、Option2 和 Option3。

```text
enum MyEnum {
    Option1,
    Option2,
    Option3,
}
```


## 实例

编译执行以上代码，输出结果为：

```text
Green
```


### 带值的枚举

Zig 允许为枚举的每个变体指定具体的值，这可以用来表示更多的信息或进行比较。


## 实例

编译执行以上代码，输出结果为：

```text
InProgress
```


### 使用枚举作为字段

枚举可以用作结构体字段，使得结构体更加灵活和功能强大。


## 实例

编译执行以上代码，输出结果为：

```text
User: Alice
Status: Active
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Zig 结构体和枚举` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
