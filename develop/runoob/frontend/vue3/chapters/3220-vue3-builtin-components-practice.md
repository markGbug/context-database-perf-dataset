# Vue3：Vue3 内置组件

- 来源：[Vue3 内置组件](https://www.runoob.com/vue3/vue3-builtin-components.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：练习笔记
- 章节序号：3220

## 本章内容

在 Vue.js 中，有一些内置的全局组件和内置组件，它们提供了一些常用的功能和布局支持，可以帮助开发者快速构建应用界面。

以下是一些常见的 Vue 内置组件和它们的作用：


### 1. component

<component> 是一个抽象的组件，用于动态地渲染不同的组件或元素。

通过绑定 is 属性可以实现动态组件的切换和渲染。

```html
<component :is="currentComponent"></component>
```


### 2. transition 和 transition-group

<transition> 和 <transition-group> 提供了在 Vue.js 中实现过渡和动画效果的功能。

通过定义过渡的 CSS 类名，可以控制元素在进入或离开 DOM 时的动画效果。

```html
<transition name="fade">
  <div v-if="show">Hello!</div>
</transition>
```

```html
<transition-group name="list" tag="ul">
  <li v-for="item in items" :key="item.id">{{ item.text }}</li>
</transition-group>
```


### 3. keep-alive

<keep-alive> 是一个抽象组件，用于保持组件状态或避免多次渲染。

当组件被 <keep-alive> 包裹时，其状态将会被缓存，而不是每次切换时重新渲染。

```html
<keep-alive>
  <component :is="currentComponent"></component>
</keep-alive>
```


### 4. slot

<slot> 是 Vue.js 中用于插入内容的插槽组件。它允许父组件将子组件的内容传递到特定的插槽位置，使得组件更加灵活和可复用。

```html
<child-component>
  <template #header>
    <h2>Header Content</h2>
  </template>
  <template #default>
    <p>Default Content</p>
  </template>
</child-component>
```


### 5. teleport

<teleport> 允许你将 DOM 元素渲染到应用的任何地方，而不受当前 DOM 结构的限制。这在需要在应用中动态移动元素时非常有用，例如在模态框中渲染弹出内容。

```html
<teleport to="body">
  <modal-dialog v-if="showModal">
    <!-- modal content -->
  </modal-dialog>
</teleport>
```


### 6. Suspense

<Suspense> 是 Vue.js 3.x 中新增的组件，用于处理异步组件的加载和状态。它可以在异步组件加载完成之前显示占位内容，并处理加载状态和错误。

```html
<Suspense>
  <template #default>
    <AsyncComponent />
  </template>
  <template #fallback>
    <div>Loading...</div>
  </template>
</Suspense>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Vue3 内置组件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
