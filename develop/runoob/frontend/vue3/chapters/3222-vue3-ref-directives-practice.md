# Vue3：Vue3 内置指令

- 来源：[Vue3 内置指令](https://www.runoob.com/vue3/vue3-ref-directives.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：练习笔记
- 章节序号：3222

## 本章内容

Vue.js 内置了多个指令（Directives），用于在模板中添加特定的响应式行为或操作 DOM。

以下是 Vue.js 中常用的内置指令：

```html
<div v-memo="[valueA, valueB]">
  ...
</div>
```

缓存一个模板的子树。

当组件重新渲染，如果 valueA 和 valueB 都保持不变，这个 <div> 及其子项的所有更新都将被跳过。实际上，甚至虚拟 DOM 的 vnode 创建也将被跳过，因为缓存的子树副本可以被重新使用。


### v-text

- 用法: <p v-text="message"></p>
- 说明: 更新元素的 textContent，类似于插值 {{ }}，但是是单向绑定。可以用于设置元素的纯文本内容。


## 实例


## 实例


### v-html

- 用法: <div v-html="htmlContent"></div>
- 说明: 更新元素的 innerHTML，用于输出包含 HTML 结构的内容。需要注意安全性，避免 XSS 攻击。


## 实例


## 实例


### v-model

- 用法: <input v-model="value">
- 说明: 在表单控件元素上创建双向数据绑定，将输入字段与数据属性同步，支持多种表单控件类型。


## 实例


## 实例


### v-show

- 用法: <div v-show="isVisible"></div>
- 说明: 根据表达式的真假切换元素的显示与隐藏，使用 CSS 的 display 属性控制元素的可见性。


## 实例


## 实例


### v-if / v-else / v-else-if

- 用法: <p v-if="isVisible">Visible</p><p v-else>Not Visible</p>
- 说明: 根据表达式的真假条件性地渲染元素。v-else 和 v-else-if 是 v-if 的补充指令，用于多条件判断。


## 实例


## 实例


### v-for

- 用法: <li v-for="(item, index) in items" :key="index">{{ item }}</li>
- 说明: 遍历数组或对象的每个元素，生成相应数量的元素，支持指定键（key）来提高渲染效率。


## 实例


## 实例


### v-on (@)

- 用法: <button v-on:click="handleClick">Click me</button>
- 说明: 绑定事件监听器，用于监听 DOM 事件，可以简写为 @。支持修饰符和动态事件名。


## 实例


## 实例


### v-bind ( : )

- 用法: <img v-bind:src="imageSrc">
- 说明: 动态绑定 HTML 属性，可以简写为 :。用于动态设置元素的属性，例如 src、href 等。


## 实例


## 实例


## 后续章节

- v-slot
- 实例
- 实例
- v-pre
- 实例
- 实例
- v-cloak
- 实例
- 实例
- 实例
- v-once
- 实例
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Vue3 内置指令` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
