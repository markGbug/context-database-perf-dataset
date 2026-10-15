# 知识点 46545：Vue3：Vue3 自定义指令 - 实例

- 来源：[Vue3 自定义指令](https://www.runoob.com/vue3/vue3-custom-directive.html)
- 来源章节：[3212-vue3-custom-directive-study.md](../chapters/3212-vue3-custom-directive-study.md)
- 分类：前端开发
- 技术：Vue3
- 所在小节：实例
- 知识类型：代码
- 原章节序号：3212

## 原文片段

```text
<div id="app">
    <p>页面载入时，input 元素自动获取焦点：</p>
    <input v-focus>
</div>

<script>
const app = {
   data() {
      return {
      }
   },
   directives: {
      focus: {
         // 指令的定义
         mounted(el) {
            el.focus()
         }
      }
   }
}

Vue.createApp(app).mount('#app')
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `实例` 这一小节和 `Vue3 自定义指令` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
