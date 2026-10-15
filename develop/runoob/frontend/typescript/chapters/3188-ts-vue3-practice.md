# TypeScript：TypeScript + Vue3 实战

- 来源：[TypeScript + Vue3 实战](https://www.runoob.com/typescript/ts-vue3.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：练习笔记
- 章节序号：3188

## 本章内容

Vue 3 对 TypeScript 有很好的支持，本教程介绍 Vue 3 + TypeScript 的开发实践。

Vue 3 的 Composition API 和 TypeScript 的类型系统完美结合，可以让代码更安全、更易维护。

Vue3 教程查看：https://www.runoob.com/vue3/vue3-tutorial.html


## 为什么需要在 Vue 3 中使用 TypeScript

Vue 3 从设计之初就全面拥抱 TypeScript，提供了极好的类型支持。

Composition API 的函数式写法与 TypeScript 类型系统完美配合：ref 有泛型支持、computed 有类型推断、props 有完整的类型检查。

使用 TypeScript 可以让 Vue 组件的属性、事件、响应式数据都有类型保护。

Vue 3 原生支持：Vue 3 的源码使用 TypeScript 编写，与 TypeScript 无缝集成。


## 创建项目

使用 Vite 创建支持 TypeScript 的 Vue 3 项目。


## 初始化

推荐：Vite 是 Vue 官方推荐的建设工具，创建项目时直接选择 vue-ts 模板即可。


## 组件类型

使用 defineComponent 和 PropType 定义组件和 Props 类型。


## src/components/UserCard.vue

运行结果：

```text
UserCard 组件渲染成功
```

PropType：当 props 的类型是复杂对象时，需要使用 PropType 进行类型断言。


## 组合式 API 类型

使用 ref、computed 等响应式 API 时，TypeScript 提供完整的类型支持。


## src/components/Counter.vue

运行结果：

```text
Counter 组件渲染成功
```

类型推断：Vue 3 的组合式 API 会根据初始值自动推断类型，复杂类型可以显式指定泛型。


## 接口定义

在 types 目录集中定义项目的类型接口。


## src/types/index.ts

类型集中管理：将类型定义放在 types 目录，便于在多个组件中复用。


## 注意事项

- defineComponent：提供完整的类型推断
- PropType：复杂 Props 类型需要使用
- ref 泛型：复杂类型显式指定
- emits：声明事件类型

最佳实践：Vue 3 推荐使用组合式 API + TypeScript，可以获得最佳的开发体验。


## 总结

Vue 3 与 TypeScript 完美结合。

- defineComponent：获得完整的类型推断
- PropType：为 props 提供类型安全
- ref：泛型参数指定响应式类型
- computed：自动推断计算属性类型

建议：Vue 3 项目强烈建议使用 TypeScript，特别是在大型应用中。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `TypeScript + Vue3 实战` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
