# Vue3：Vue3 样式绑定

- 来源：[Vue3 样式绑定](https://www.runoob.com/vue3/vue3-class-bind.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：学习笔记
- 章节序号：3209

## 本章内容

## Vue.js class

class 与 style 是 HTML 元素的属性，用于设置元素的样式，我们可以用 v-bind 来设置样式属性。

v-bind 在处理 class 和 style 时， 表达式除了可以使用字符串之外，还可以是对象或数组。

v-bind:class 可以简写为 :class。


## class 属性绑定

我们可以为 v-bind:class 设置一个对象，从而动态的切换 class:


## 实例 1

实例中将 isActive 设置为 true 显示了一个绿色的 div 块，如果设置为 false 则不显示：

```html
<div :class="{ 'active': isActive }"></div>
```

以上实例 div class 渲染结果为：

```html
<div class="active"></div>
```

我们也可以在对象中传入更多属性用来动态切换多个 class 。

此外，:class 指令也可以与普通的 class 属性共存。


## 实例 2

text-danger 类背景颜色覆盖了 active 类的背景色：

```html
<div class="static" :class="{ 'active' : isActive, 'text-danger' : hasError }">
</div>
```

以上实例 div class 渲染结果为：

```html
<div class="static text-danger"></div>
```

当 isActive 或者 hasError 变化时，class 属性值也将相应地更新。例如，如果 active 的值为 true，class 列表将变为 "static active text-danger"。

我们也可以直接绑定数据里的一个对象：


## 实例 3

text-danger 类背景颜色覆盖了 active 类的背景色：

```html
<div id="app">
    <div class="static" :class="classObject"></div>
</div>
```

实例 3 与 实例 2 的渲染结果是一样的。

此外，我们也可以在这里绑定一个返回对象的计算属性。这是一个常用且强大的模式：


## 实例 4

```text
data() {
  return {
    isActive: true,
    error: null
  }
},
computed: {
  classObject() {
    return {
      active: this.isActive && !this.error,
      'text-danger': this.error && this.error.type === 'fatal'
    }
  }
}
```


### 数组语法

我们可以把一个数组传给 v-bind:class ，实例如下：


## 实例 5

```html
<div class="static" :class="[activeClass, errorClass]"></div>
```

以上实例 div class 渲染结果为：

```html
<div class="static active text-danger"></div>
```

我们还可以使用三元表达式来切换列表中的 class ：


## 实例 6

errorClass 是始终存在的，isActive 为 true 时添加 activeClass 类：

```html
<div id="app">
    <div class="static" :class="[isActive ? activeClass : '', errorClass]"></div>
</div>
```

以上实例 div class 渲染结果为：

```html
<div class="static text-danger"></div>
```


## 复习重点

- 能说明 `Vue3 样式绑定` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
