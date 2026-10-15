# React：React Sass

- 来源：[React Sass](https://www.runoob.com/react/react-sass.html)
- 分类：前端开发
- 技术：React
- 笔记类型：练习笔记
- 章节序号：3058

## 本章内容

Sass（Syntactically Awesome Stylesheets）是一种 CSS 预处理器。

Sass 允许你使用 CSS 中尚不存在的特性，比如变量、嵌套规则、混入、函数等等。

Sass 文件在服务器上执行，并将生成的 CSS 发送到浏览器。

你可以在我们的 Sass 教程 中了解更多关于 Sass 的信息。


### 安装 Sass

在终端中运行以下命令来安装 Sass：

```text
npm i sass
```

现在你已经准备好在项目中包含 Sass 文件了！


### 创建一个 Sass 文件

创建 Sass 文件的方式与创建 CSS 文件相同，但 Sass 文件的扩展名是 .scss。

在 Sass 文件中，你可以使用变量和其他 Sass 功能。


### 实例例

创建一个变量来定义文本的颜色：

my-sass.scss 文件代码：


## my-sass.scss

像导入 CSS 文件一样导入 Sass 文件：


## 实例

以上代码中，我们创建了一个 Sass 文件 my-sass.scss，并在其中使用了 Sass 变量 $myColor 来定义 h1 的颜色。然后，我们在 index.js 中像导入普通 CSS 文件一样导入了这个 Sass 文件，并在 Header 组件中使用了这些样式。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `React Sass` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
