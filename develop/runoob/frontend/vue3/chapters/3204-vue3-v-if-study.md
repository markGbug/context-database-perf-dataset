# Vue3：Vue3 条件语句

- 来源：[Vue3 条件语句](https://www.runoob.com/vue3/vue3-v-if.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：学习笔记
- 章节序号：3204

## 本章内容

在 Vue 3 中，你可以在模板中使用多种条件语句来控制组件的渲染。

主要的条件语句有 v-if、v-else-if、v-else 和 v-show，以下是它们的用法及区别：

- v-if：元素在条件为 false 时不会被渲染到 DOM 中，适用于条件变化不频繁的情况。
- v-show：元素总是渲染到 DOM 中，适用于条件变化频繁的情况，切换显示隐藏性能更好。
- v-else-if 和 v-else：用于处理多个条件分支，配合 v-if 使用。


## 条件判断


### v-if

根据表达式的真假条件性地渲染元素。如果表达式为真，则渲染该元素；如果为假，则不渲染（不会在 DOM 中生成该元素）。

条件判断使用 v-if 指令，指令的表达式返回 true 时才会显示：


## v-if 指令

在元素中使用 v-if 指令：

```html
<div id="app">
    <p v-if="seen">现在你看到我了</p>
</div>

<script>
const app = {
  data() {
    return {
      seen: true /* 改为false，信息就无法显示 */
    }
  }
}

Vue.createApp(app).mount('#app')
</script>
```

这里， v-if 指令将根据表达式 seen 的值( true 或 false )来决定是否插入 p 元素。

因为 v-if 是一个指令，所以必须将它添加到一个元素上。如果是多个元素，可以包裹在 <template> 元素上，并在上面使用 v-if。最终的渲染结果将不包含 <template> 元素。


## v-if 指令

在 <template> 元素上使用 v-if 指令：

```html
<div id="app">
    <template v-if="seen">
        <h1>网站</h1>
        <p>Google</p>
        <p>Runoob</p>
        <p>Taobao</p>
    </template>
</div>

<script>
const app = {
  data() {
    return {
      seen: true /* 改为false，信息就无法显示 */
    }
  }
}

Vue.createApp(app).mount('#app')
</script>
```


## 复习重点

- 能说明 `Vue3 条件语句` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
