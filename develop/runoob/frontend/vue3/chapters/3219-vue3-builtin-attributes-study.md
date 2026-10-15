# Vue3：Vue3 内置属性

- 来源：[Vue3 内置属性](https://www.runoob.com/vue3/vue3-builtin-attributes.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：学习笔记
- 章节序号：3219

## 本章内容

在 Vue.js 中，is、key 和 ref 是三个常用的内置属性，用法如下。

<标签 is="组件名"> <component :is="变量">

```html
<ul><li is="my-component"></li></ul>
```

```html
<div v-for="item in list" :key="item.id">{{item}}</div>
```

```html
<input ref="inputRef">
this.$refs.inputRef.focus()
```


## is 属性

在 Vue.js 中，is 属性通常用于动态组件的实现，特别是当你希望在运行时动态地切换不同的组件时非常有用。

- 类型: String 或 Object
- 作用: is 属性用于动态地指定当前 <component> 组件应该渲染哪一个子组件。通常结合 <component> 元素和动态组件的特性一起使用，允许你在运行时基于数据来切换不同的组件。


## 实例

以上代码中，currentComponent 是一个数据属性，它决定了 <component> 元素要渲染的具体组件。当点击按钮时，调用 toggleComponent 方法会切换 currentComponent 的值，从而动态改变渲染的组件。

注意事项：

- 注意事项:is 属性的值可以是组件的名称字符串，也可以是组件对象。当使用字符串时，组件名称应该与注册的组件名一致。如果使用对象，可以直接引用组件对象或者使用动态计算属性返回组件对象。


## key 属性

- 类型: String 或 Number
- 作用: 在 Vue.js 的列表渲染中，每个 v-for 循环中的元素需要有一个唯一的 key 属性。key 的作用是帮助 Vue 识别每个节点的唯一性，从而高效地更新虚拟 DOM。当 Vue 重新渲染列表时，会根据 key 来决定是否重新使用现有 DOM 元素或者重新创建。 实例 <ul> <li v-for="item in items" :key="item.id">{{ item.name }}</li> </ul> 以上代码中，item.id 作为 key 属性，确保了每个列表项在数据更新时可以正确地被 Vue 辨识和处理。
- 注意事项: key 应该是唯一且稳定的。稳定的意思是，key 不应该随着数据的变化而变化，否则会影响 Vue 的性能和虚拟 DOM 的复用策略。 避免使用索引作为 key，除非你明确知道列表项的顺序不会改变。


## ref 属性

- 类型: String 或 Object
- 作用: ref 是用来给元素或子组件注册引用信息的。在实际开发中，你可以使用 ref 来访问具体的 DOM 元素或子组件实例，从而进行一些操作，如调用方法、访问属性等。

给 DOM 元素添加 ref


## 实例

给子组件添加 ref


## 实例

注意事项:

- 在模板中使用 ref 时，Vue 将会提供一个对应的 $refs 对象，通过该对象可以访问到注册的 DOM 元素或子组件实例。
- 避免滥用 ref，尽可能通过数据驱动和事件处理来操作 DOM 和子组件，保持代码的可维护性和清晰性。


## 复习重点

- 能说明 `Vue3 内置属性` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
