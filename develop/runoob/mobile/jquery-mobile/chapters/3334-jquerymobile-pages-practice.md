# jQuery Mobile：jQuery Mobile 页面

- 来源：[jQuery Mobile 页面](https://www.runoob.com/jquerymobile/jquerymobile-pages.html)
- 分类：移动开发
- 技术：jQuery Mobile
- 笔记类型：练习笔记
- 章节序号：3334

## 本章内容

## 开始学习 jQuery Mobile


## 实例


### 实例解析：

- data-role="page" 是在浏览器中显示的页面。
- data-role="header" 是在页面顶部创建的工具条 (通常用于标题或者搜索按钮)
- data-role="main" 定义了页面的内容，比如文本， 图片，表单，按钮等。
- "ui-content" 类用于在页面添加内边距和外边距。
- data-role="footer" 用于创建页面底部工具条。
- 在这些容器中你可以添加任何 HTML 元素 - 段落, 图片, 标题, 列表等。


## 在页面中添加 jQuery Mobile

使用 jQuery Mobile, 你可以在单个 HTML 文件中创建多个不同的页面。

你可以使用不同的href属性来区分使用同一个唯一id的页面：


## 实例

注意： 当web应用有大量的内容（文本，图片，脚本等）将会严重影响加载时间。如果你不想使用内页链接可以使用外部文件：

```html
<a href="externalfile.html">访问外部文件</a>
```


## 页面作为对话框使用

对话框是用于显示页面信息显示或者表单信息的输入。

在链接中添加data-rel="dialog"让用户点击链接时弹出对话框:


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery Mobile 页面` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
