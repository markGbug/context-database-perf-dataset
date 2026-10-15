# Vue.js：Vue.js 计算属性

- 来源：[Vue.js 计算属性](https://www.runoob.com/vue2/vue-computed.html)
- 分类：前端开发
- 技术：Vue.js
- 笔记类型：练习笔记
- 章节序号：3254

## 本章内容

计算属性关键词: computed。

计算属性在处理一些复杂逻辑时是很有用的。

可以看下以下反转字符串的例子：


## 实例 1

```html
<div id="app">
  {{ message.split('').reverse().join('') }}
</div>
```

实例 1 中模板变的很复杂起来，也不容易看懂理解。

接下来我们看看使用了计算属性的实例：


## 实例 2

```html
<div id="app">
  <p>原始字符串: {{ message }}</p>
  <p>计算后反转字符串: {{ reversedMessage }}</p>
</div>

<script>
var vm = new Vue({
  el: '#app',
  data: {
    message: 'Runoob!'
  },
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
  }
})
</script>
```

实例 2 中声明了一个计算属性 reversedMessage 。

提供的函数将用作属性 vm.reversedMessage 的 getter 。

vm.reversedMessage 依赖于 vm.message，在 vm.message 发生改变时，vm.reversedMessage 也会更新。


## computed vs methods

我们可以使用 methods 来替代 computed，效果上两个都是一样的，但是 computed 是基于它的依赖缓存，只有相关依赖发生改变时才会重新取值。而使用 methods ，在重新渲染的时候，函数总会重新调用执行。


## 实例 3

```javascript
methods: {
  reversedMessage2: function () {
    return this.message.split('').reverse().join('')
  }
}
```

可以说使用 computed 性能会更好，但是如果你不希望缓存，你可以使用 methods 属性。


## computed setter

computed 属性默认只有 getter ，不过在需要时你也可以提供一个 setter ：


## 实例 4

```html
var vm = new Vue({
  el: '#app',
  data: {
    name: 'Google',
    url: 'http://www.google.com'
  },
  computed: {
    site: {
      // getter
      get: function () {
        return this.name + ' ' + this.url
      },
      // setter
      set: function (newValue) {
        var names = newValue.split(' ')
        this.name = names[0]
        this.url = names[names.length - 1]
      }
    }
  }
})
// 调用 setter， vm.name 和 vm.url 也会被对应更新
vm.site = '菜鸟教程 http://www.runoob.com';
document.write('name: ' + vm.name);
document.write('<br>');
document.write('url: ' + vm.url);
```

从实例运行结果看在运行 vm.site = '菜鸟教程 http://www.runoob.com'; 时，setter 会被调用， vm.name 和 vm.url 也会被对应更新。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Vue.js 计算属性` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
