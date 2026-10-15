# TypeScript：TypeScript + React 实战

- 来源：[TypeScript + React 实战](https://www.runoob.com/typescript/ts-react.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：练习笔记
- 章节序号：3189

## 本章内容

TypeScript 为 React 开发提供完整的类型支持，提高代码可靠性。

使用 TypeScript 可以让 React 组件、Props、State 等都有完整的类型检查，减少运行时错误。

React 教程查看：https://www.runoob.com/vue3/react-tutorial.html


## 为什么需要在 React 中使用 TypeScript

React 组件化开发会产生大量的 Props、State、Context 等数据流。

没有类型定义时，很难追踪数据的来源和结构，容易出现运行时错误。

TypeScript 为 React 提供了完整的类型系统：组件 Props 有类型检查、useState 有类型推断、事件处理有类型提示。

数据流：React 中的数据流（Props、State、Context）都需要类型定义，TypeScript 可以确保数据流的类型安全。


## 创建项目

使用现代脚手架创建支持 TypeScript 的 React 项目。


## 初始化

推荐：Vite 是目前最推荐的 React 构建工具，速度快，开发体验好。


## 组件类型

使用 React.FC 类型定义函数组件。


## src/components/Button.tsx

运行结果：

```text
Button 组件渲染成功
```

React.FC：这是 React 函数组件的类型，包含了 children、propTypes 等内置类型。


## Props 类型

定义组件的 Props 接口，传递数据给子组件。


## src/components/UserCard.tsx


## useState 类型

为 useState 提供类型参数，确保状态类型正确。


## src/components/Counter.tsx

运行结果：

```text
Counter 组件渲染成功
```

泛型参数：useState<T> 中的 T 就是状态的类型，如果提供初始值，TypeScript 可以自动推断。


## useEffect 类型

useEffect 同样有完整的类型支持。


## src/components/DataFetcher.tsx

依赖数组：useEffect 的第二个参数是依赖数组，TypeScript 会检查回调中使用的变量是否都已在数组中声明。


## 事件处理

React 事件有专门的类型定义。


## src/components/Form.tsx

运行结果：

```text
Form 组件渲染成功
```

事件类型：React 为每种 DOM 事件都提供了类型，如 FormEvent、ChangeEvent、MouseEvent 等。


## 注意事项

- React.FC：推荐使用，可获得完整的类型支持
- Props 接口：为每个组件定义 Props 类型
- useState 泛型：复杂类型需要显式指定
- 事件类型：使用 React 提供的事件类型

最佳实践：将类型定义和组件放在同一文件，或集中管理在 types 目录。


## 总结

TypeScript 大幅提升了 React 开发体验。

- React.FC：React 函数组件的标准类型
- Props：使用 interface 定义组件属性
- useState：使用泛型参数指定状态类型
- useEffect：完整的类型支持
- 事件：使用 React 事件类型避免 any

建议：新项目直接使用 TypeScript，可以显著减少运行时错误。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `TypeScript + React 实战` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
