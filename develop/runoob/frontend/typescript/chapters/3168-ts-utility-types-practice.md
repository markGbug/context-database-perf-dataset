# TypeScript：TypeScript 工具类型

- 来源：[TypeScript 工具类型](https://www.runoob.com/typescript/ts-utility-types.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：练习笔记
- 章节序号：3168

## 本章内容

工具类型（Utility Types）是 TypeScript 内置的一系列高级类型。

它们可以帮助开发者快速创建和转换类型，提高代码的可复用性和类型安全性。

工具类型本质上是泛型类型，通过映射类型和条件类型实现。


## 为什么需要工具类型

在实际的 TypeScript 开发中，我们经常需要基于现有类型创建新的类型。

手动创建这些类型不仅繁琐，而且容易出错。

工具类型提供了一种声明式的方式来转换和创建类型，大大提高了开发效率。

概念说明：工具类型是 TypeScript 预定义的一系列泛型类型。它们使用映射类型和条件类型来实现类型的转换和生成。


## Partial<T> - 可选属性

Partial 将类型 T 的所有属性设置为可选。

这在创建部分更新对象或处理表单数据时非常有用。


## 实例

运行结果：

```text
部分用户: {"name":"Alice"}
```

应用场景：Partial 常用于更新对象数据。例如：只更新用户的一部分信息时，不需要传入完整的用户对象。


## Required<T> - 必填属性

Required 与 Partial 相反，将所有可选属性设置为必填。

当需要确保对象包含所有属性时使用。


## 实例

运行结果：

```text
配置: {"host":"localhost","port":8080}
```

说明：Required 不仅移除可选属性（?），还会移除 readonly 修饰符。


## Readonly<T> - 只读属性

Readonly 将所有属性设置为只读。

创建后不允许修改的 对象时非常有用。


## 实例

应用场景：Readonly 常用于定义配置对象、枚举值映射等不希望被修改的数据。


## Pick<T, K> - 选择属性

Pick 从类型 T 中选择指定的属性 K 组成新类型。

当你只需要某个类型的部分属性时使用。


## 实例

运行结果：

```text
用户基本信息: {"id":1,"name":"Alice"}
```

对比：Pick 和 Partial 结合使用，可以创建只包含部分可选属性的类型。


## Omit<T, K> - 排除属性

Omit 从类型 T 中排除指定的属性 K，返回剩余属性组成的新类型。

与 Pick 相反，用于删除不需要的属性。


## 实例

运行结果：

```text
无密码用户: {"id":1,"name":"Alice","email":"a@b.com"}
```

提示：Omit 是 Pick 的反向操作。当你需要排除少数属性时用 Omit，需要选择少数属性时用 Pick。


## Record<K, T> - 构造对象类型

Record 构造一个对象类型，键的类型为 K，值的类型为 T。

常用于创建键值对映射、字典类型等。


## 实例

运行结果：

```text
管理员权限: read,write,delete
访客权限: read
```

应用场景：Record 常用于创建配置映射、状态映射、权限映射等需要根据键快速查找值的场景。


## Exclude<T, U> - 排除类型

Exclude 从类型 T 中排除可以赋值给类型 U 的类型。

主要用于联合类型，排除特定的类型成员。


## 实例

运行结果：

```text
值: d
```

说明：Exclude 的原理是：如果 T 中的某个类型可以赋值给 U，就从 T 中移除它。


## Extract<T, U> - 提取类型

Extract 与 Exclude 相反，从类型 T 中提取可以赋值给类型 U 的类型。

用于筛选联合类型中的特定成员。


## 实例

运行结果：

```text
字母: a
```

对比：Extract 和 Exclude 是互补的。Extract(T, U) 等价于 Exclude(T, Exclude<T, U>)。


## NonNullable<T> - 排除空值

NonNullable 从类型 T 中排除 null 和 undefined。

确保类型不包含空值时使用。


## 实例

说明：NonNullable<T> 等价于 Exclude<T, null | undefined>。


## ReturnType<T> - 获取返回类型

ReturnType 获取函数类型 T 的返回类型。

常用于从已存在的函数中提取返回类型。


## 实例

运行结果：

```text
用户: {"name":"Bob","age":30}
配置: {"host":"example.com","port":3000}
```

提示：ReturnType<T> 中的 T 必须是函数类型。可以使用 typeof 获取函数的类型。


## 注意事项

- 工具类型都是泛型：使用时应传入具体的类型参数
- 只读和可选：工具类型可以组合使用，如 Partial<Readonly<T>>
- 内置类型：这些工具类型都是 TypeScript 内置的，无需安装
- 自定义工具类型：可以基于映射类型和条件类型创建自定义工具类型

进阶：如果内置工具类型不满足需求，可以参考 TypeScript 源码自行实现自定义工具类型。


## 总结

TypeScript 工具类型是类型系统的重要组成部分。

- Partial<T>：将所有属性变为可选
- Required<T>：将所有属性变为必填
- Readonly<T>：将所有属性变为只读
- Pick<T,K>：选择指定属性
- Omit<T,K>：排除指定属性
- Record<K,T>：构造对象类型
- Exclude/Extract：类型过滤
- NonNullable：排除 null 和 undefined
- ReturnType：获取函数返回类型

最佳实践：善用工具类型可以使代码更加类型安全，减少重复的类型定义，提高代码可维护性。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `TypeScript 工具类型` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
