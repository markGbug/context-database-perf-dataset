# TypeScript：TypeScript Set 和 WeakMap

- 来源：[TypeScript Set/WeakMap](https://www.runoob.com/typescript/ts-set-weakmap.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：练习笔记
- 章节序号：3149

## 本章内容

TypeScript 继承自 JavaScript 的 Set 和 WeakMap 数据结构，提供了更强大的类型支持。

这些数据结构在处理唯一值集合、键值对映射、缓存等场景非常有用。


## 为什么需要 Set 和 WeakMap

在开发中，我们经常需要处理唯一值集合和键值对映射。

Set 提供了自动去重的集合功能，比数组更方便处理唯一值。

WeakSet 和 WeakMap 使用弱引用，不会阻止垃圾回收，适用于需要避免内存泄漏的场景，如缓存 DOM 节点。

概念说明：Set 是值的集合，值唯一；Map 是键值对集合，键可以是任意类型。WeakSet 和 WeakMap 使用弱引用，不影响垃圾回收。


## Set

Set 是值的集合，值唯一，不允许重复。


## 实例

运行结果：

```text
Set 大小: 3
是否包含 2: true
值: 1
值: 2
值: 3
转换为数组: 1,2,3
```

去重：Set 会自动忽略重复的值，这使得它非常适合用于数组去重。


## Set 类型注解

可以显式指定 Set 中值的类型。


## 实例

泛型：使用 Set<T> 语法指定 Set 中元素的类型。


## WeakSet

WeakSet 存储对象引用，引用为弱引用（不影响垃圾回收）。


## 实例

注意：WeakSet 不能遍历，类型注解只能是 object。这使得 WeakSet 适合存储需要被垃圾回收的对象。


## Map

Map 是键值对集合，键可以是任意类型。


## 实例

运行结果：

```text
获取 two: 2
Map 大小: 3
是否包含 three: true
one: 1
two: 2
three: 3
转换为数组: one,1,two,2,three,3
```

优势：Map 的键可以是任意类型（对象、函数等），这比使用对象作为键更灵活。


## WeakMap

WeakMap 的键是弱引用，不影响垃圾回收。


## 实例

应用场景：WeakMap 常用于缓存 DOM 节点数据，当 DOM 节点被移除时，缓存数据也会被自动清理，避免内存泄漏。


## 实际应用场景

使用 Map 统计数组元素出现次数。


## 实例

运行结果：

```text
apple: 3
banana: 2
orange: 1
```

实用：Map 是实现缓存、统计、索引等功能的理想选择。


## 注意事项

- Set 唯一性：Set 自动忽略重复值
- WeakSet/WeakMap：键必须是对象，不能遍历
- Map 键类型：Map 的键可以是任意类型
- 内存管理：WeakSet/WeakMap 不阻止垃圾回收

选择建议：需要唯一值集合用 Set，需要键值映射用 Map，需要避免内存泄漏用 WeakSet/WeakMap。


## 总结

Set 和 Map 是 TypeScript 中非常有用的数据结构。

- Set：值的集合，值唯一，自动去重
- WeakSet：对象弱引用集合，不可遍历，适用于需要被垃圾回收的场景
- Map：键值对集合，键可以是任意类型
- WeakMap：键弱引用，不可遍历，适用于缓存和私有数据

建议：根据具体需求选择合适的数据结构：需要去重用 Set，需要映射用 Map，需要内存优化用 Weak 版本。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `TypeScript Set/WeakMap` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
