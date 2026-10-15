# Vue.js：Vue.js 样式绑定

- 来源：[Vue.js 样式绑定](https://www.runoob.com/vue2/vue-class-style.html)
- 分类：前端开发
- 技术：Vue.js
- 笔记类型：练习笔记
- 章节序号：3256

## 本章内容

## Vue.js class

class 与 style 是 HTML 元素的属性，用于设置元素的样式，我们可以用 v-bind 来设置样式属性。

Vue.js v-bind 在处理 class 和 style 时， 专门增强了它。表达式的结果类型除了字符串之外，还可以是对象或数组。


## class 属性绑定

我们可以为 v-bind:class 设置一个对象，从而动态的切换 class:


## 实例 1

实例中将 isActive 设置为 true 显示了一个绿色的 div 块，如果设置为 false 则不显示：

```html
<div v-bind:class="{ 'active': isActive }"></div>
```

以上实例 div class 为：

```html
<div class="active"></div>
```

我们也可以在对象中传入更多属性用来动态切换多个 class 。


## 实例 2

text-danger 类背景颜色覆盖了 active 类的背景色：

```html
<div class="static"
     v-bind:class="{ 'active' : isActive, 'text-danger' : hasError }">
</div>
```

以上实例 div class 为：

```html
<div class="static active text-danger"></div>
```

我们也可以直接绑定数据里的一个对象：


## 实例 3

text-danger 类背景颜色覆盖了 active 类的背景色：

```html
<div id="app">
  <div v-bind:class="classObject"></div>
</div>
```

实例 3 与 实例 2 的渲染结果是一样的。

此外，我们也可以在这里绑定返回对象的计算属性。这是一个常用且强大的模式：


## 实例 4

```javascript
new Vue({
  el: '#app',
  data: {
    isActive: true,
    error: {
      value: true,
      type: 'fatal'
    }
  },
  computed: {
    classObject: function () {
      return {
  base: true,
        active: this.isActive && !this.error.value,
        'text-danger': this.error.value && this.error.type === 'fatal',
      }
    }
  }
})
```


### 数组语法

我们可以把一个数组传给 v-bind:class ，实例如下：


## 实例 5

```html
<div v-bind:class="[activeClass, errorClass]"></div>
```

以上实例 div class 为：

```html
<div class="active text-danger"></div>
```

我们还可以使用三元表达式来切换列表中的 class ：


## 实例 6

errorClass 是始终存在的，isActive 为 true 时添加 activeClass 类：

```html
<div v-bind:class="[errorClass ,isActive ? activeClass : '']"></div>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Vue.js 样式绑定` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
