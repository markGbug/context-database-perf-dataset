# CSS：CSS 编辑器

- 来源：[CSS 编辑器](https://www.runoob.com/css/css-editor.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：学习笔记
- 章节序号：2391

## 本章内容

可以使用专业的 CSS 编辑器来编辑 CSS，为大家推荐几款常用的编辑器：

你可以从以上软件的官网中下载对应的软件，按步骤安装即可。

也可以使用我们的在线编辑器：https://www.jyshare.com/front-end/61/

接下来我们将为大家演示如何使用 VS Code 工具来创建 CSS 文件。


## VS Code

Visual Studio Code（简称 VS Code）是一个由微软开发，同时支持 Windows 、 Linux 和 macOS 等操作系统且开放源代码的代码编辑器，编辑器中内置了扩展程序管理的功能。

VS Code 安装教程参考：https://www.runoob.com/vscode/vscode-tutorial.html

安装必备插件 (Extensions): 点击 VS Code 左侧边栏的方块图标（Extensions），搜索并安装以下两个插件，它们对新手至关重要：

- Live Server: 允许你在浏览器中实时预览网页，保存代码后浏览器会自动刷新。
- HTML CSS Support: 增强 CSS 的智能提示。


### 第一步: 建立项目结构

在你的电脑上创建一个名为 my-first-css 的文件夹

在 VS Code 中打开： 点击 VS Code 左上角的 File -> Open Folder...，选择刚才的文件夹。

- 在左侧资源管理器空白处右键，新建文件 index.html (这是网页骨架)。
- 再次右键，新建文件 style.css (这是网页的皮肤)。


### 第二步：编写 HTML 骨架

CSS 必须依附于 HTML 存在，以下是 index.html 文件代码。

在 <body> 标签内输入以下代码，并一定要加上 <link> 标签来关联 CSS 文件：

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>我的 CSS 练习</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <div class="card">
        <h1>Hello, CSS!</h1>
        <p>这是我用 VS Code 写的第一个样式卡片。</p>
        <button>点击我</button>
    </div>

</body>
</html>
```


### 第三步：编写 CSS 样式

在 style.css 文件中输入以下代码:


## 实例


## 复习重点

- 能说明 `CSS 编辑器` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
