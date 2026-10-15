# Vue3：Vue3 项目打包

- 来源：[Vue3 打包](https://www.runoob.com/vue3/vue3-build.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：学习笔记
- 章节序号：3194

## 本章内容

当你准备将应用发布到生产环境时，就需要打包 Vue 项目。

打包 Vue 项目使用以下命令：

```text
npm run build
```

执行以上命令，输出结果如下：

执行完成后，会在 Vue 项目下会生成一个 dist 目录，该目录一般包含 index.html 文件及 static 目录，static 目录包含了静态文件 js、css 以及图片目录 images（如果有图片的话）。

如果直接双击打开 index.html，在浏览器中页面可能是空白了，要正常显示则需要修改下 index.html 文件中 js、css 文件路径。

例如我们打开 dist/index.html 文件看到 css 和 js 文件路径是绝对路径：

```html
<link href=/static/css/app.33da80d69744798940b135da93bc7b98.css rel=stylesheet>
<script type=text/javascript src=/static/js/app.717bb358ddc19e181140.js></script>
...
```

我们把 js、css 文件路径修改为相对路径：

```html
<link href=static/css/app.33da80d69744798940b135da93bc7b98.css rel=stylesheet>
<script type=text/javascript src=static/js/app.717bb358ddc19e181140.js></script>
...
```

这样直接双击 dist/index.html 文件就可以在浏览器中看到效果了。


## 复习重点

- 能说明 `Vue3 打包` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
