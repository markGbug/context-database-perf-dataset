# TypeScript：TypeScript null 和 undefined

- 来源：[TypeScript null/undefined](https://www.runoob.com/typescript/ts-null-undefined.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：练习笔记
- 章节序号：3146

## 本章内容

在 TypeScript 中，null 和 undefined 有特殊的处理方式。

启用 strictNullChecks 后，需要显式处理这些值，这有助于编写更安全的代码。


## 为什么需要处理 null 和 undefined

JavaScript 中 null 和 undefined 是常见的错误来源，很多运行时错误都与之相关。

TypeScript 的 strictNullChecks 选项要求开发者显式处理可能为空的值。

这虽然增加了编码工作量，但能大幅减少空值导致的运行时错误，提高代码可靠性。

概念说明：null 表示"空值"，即这里没有值；undefined 表示"未定义"，即这里还没有被赋值。


## null 和 undefined 基础

null 表示"空值"，undefined 表示"未定义"。两者在 TypeScript 中是独立的类型。


## 实例

运行结果：

```text
null: null
undefined: undefined
```

说明：在不启用 strictNullChecks 的情况下，这些类型可以相互赋值。启用后需要显式声明。


## 联合类型处理 null

启用 strictNullChecks 后，需要使用联合类型显式声明可能为 null 的值。


## 实例

运行结果：

```text
长度: 5
长度: 0
```

最佳实践：使用类型守卫（if 检查）来收窄类型，让 TypeScript 知道具体是什么类型。


## 可选参数和属性

可选参数和可选属性自动包含 undefined，不需要显式声明 null。


## 实例

运行结果：

```text
Hello, Alice!
Hello, stranger!
用户: {"name":"Bob"}
```

说明：可选参数 name?: string 等同于 string | undefined。


## 非空断言运算符

使用 ! 告诉编译器值不为 null 或 undefined。这应该谨慎使用。


## 实例

警告：非空断言会绕过 TypeScript 的类型检查，如果值实际为 null，运行时仍会报错。尽量避免使用。


## 空值合并运算符

使用 ?? 提供默认值，只有当值为 null 或 undefined 时才使用默认值。


## 实例

运行结果：

```text
显示名称: Guest
?? 结果: 0
|| 结果: 100
```

建议：优先使用 ?? 而不是 ||，因为 ?? 只会处理 null 和 undefined，不会错误地将 0 或空字符串视为 falsy。


## 可选链

使用 ?. 安全访问可能不存在的嵌套属性，避免多层嵌套时的空值检查。


## 实例

运行结果：

```text
城市: undefined
城市: 未知
```

最佳实践：可选链 ?. 是处理嵌套可选属性的最佳方式，配合 ?? 可以提供默认值的兜底。


## 注意事项

- 严格模式：建议启用 strictNullChecks 以获得更好的类型安全
- 避免断言：尽量不要使用非空断言 !
- ?? vs ||：优先使用 ?? 避免误判 0 和空字符串
- 可选链：处理嵌套可选属性时使用 ?.

最佳实践：使用类型守卫、可选链和空值合并运算符来处理 null 和 undefined，让代码更安全、更易读。


## 总结

正确处理 null 和 undefined 是编写安全 TypeScript 代码的关键。

- 严格模式：启用 strictNullChecks 后需显式处理
- 联合类型：使用 string | null 声明
- 可选参数/属性：自动包含 undefined
- 非空断言：使用 !（谨慎使用）
- 空值合并：使用 ?? 提供默认值
- 可选链：使用 ?. 安全访问

建议：养成处理空值的习惯，使用可选链和空值合并运算符让代码更健壮。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `TypeScript null/undefined` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
