# Vue.js：Vue.js 目录结构

- 来源：[Vue.js 目录结构](https://www.runoob.com/vue2/vue-directory-structure.html)
- 分类：前端开发
- 技术：Vue.js
- 笔记类型：练习笔记
- 章节序号：3249

## 本章内容

上一章节中我们使用了 npm 安装项目，我们在 IDE（Eclipse、Atom等） 中打开该目录，结构如下所示：


### 目录解析

这里是我们要开发的目录，基本上要做的事情都在这个目录里。里面包含了几个目录及文件：

- assets: 放置一些图片，如logo等。
- components: 目录里面放了一个组件文件，可以不用。
- App.vue: 项目入口文件，我们也可以直接将组件写这里，而不使用 components 目录。
- main.js: 项目的核心文件。

在前面我们打开 APP.vue 文件，代码如下（解释在注释中）：


## src/APP.vue

```html
<!-- 展示模板 -->
<template>
  <div id="app">
    <img src="./assets/logo.png">
    <hello></hello>
  </div>
</template>

<script>
// 导入组件
import Hello from './components/Hello'

export default {
  name: 'app',
  components: {
    Hello
  }
}
</script>
<!-- 样式代码 -->
<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
```

接下来我们可以尝试修改下初始化的项目，将 Hello.vue 修改为以下代码：


## src/components/Hello.vue

```html
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: '欢迎来到菜鸟教程！'
    }
  }
}
</script>
```

重新打开页面 http://localhost:8080/，一般修改后会自动刷新，显示效果如下所示:


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Vue.js 目录结构` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
