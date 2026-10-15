# Next.js：Next.js CSS 样式

- 来源：[Next.js CSS 样式](https://www.runoob.com/nextjs/nextjs-css-styles.html)
- 分类：前端开发
- 技术：Next.js
- 笔记类型：学习笔记
- 章节序号：3028

## 本章内容

在 Next.js 中，样式的使用非常灵活，我们可以选择多种方式来为你的应用添加样式。


## 全局样式

全局样式是影响整个应用的 CSS 样式，它通常用于设置页面的基础样式，如字体、颜色、布局等。

Next.js 通过 app/layout.tsx 中引入全局 CSS 文件。

默认情况下 app 目录已经有了全局样式 globals.css 文件，如果不存在，你也可以创建一个新的 CSS 文件。

在 styles 目录下创建globals.css 文件，然后在 app/layout.tsx 中引入。


## app/globals.css 文件代码：

然后，在根布局（app/layout.tsx）中导入该文件，以便将样式应用到应用中每个路由：


## app/layout.tsx 文件代码：

注意事项：全局样式可以导入到 app 目录中的任何布局、页面或组件中。然而，由于 Next.js 使用 React 的内置样式表支持来与 Suspense 集成，当前的内置支持在你在路由之间导航时并不会移除样式表。因此，我们建议将 全局样式 用于真正的全局 CSS，而将 CSS 模块 用于作用域 CSS。

app/page.tsx 代码如下：


## 实例

访问 http://localhost:3000/，测试显示效果如下：


## Sass

Next.js 还支持 Sass，这是一种更加功能丰富的 CSS 预处理器。

如果你更喜欢使用 Sass 来编写样式，可以通过安装相应的依赖来启用 Sass 内容可以参见 Sass 教程。

安装：

```text
npm install sass
```

Next.js 与 Sass 集成，支持 .scss 和 .sass 扩展名及语法。

你还可以通过 CSS 模块使用组件级别的 Sass，扩展名为 .module.scss 或 .module.sass。


### 自定义 Sass 配置

如果你想配置 Sass 的选项，可以在 next.config.js 中使用 sassOptions 选项。


## 实例

通过这种方式，你可以配置一些默认的 Sass 数据，或者进行其他自定义设置。

创建一个 SCSS 文件，如 styles/Button.module.scss：


## 实例

在组件中使用 SCSS 模块：


## 实例


## 复习重点

- 能说明 `Next.js CSS 样式` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
