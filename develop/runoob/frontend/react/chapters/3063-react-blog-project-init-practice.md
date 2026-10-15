# React：React 博客项目

- 来源：[React 博客项目](https://www.runoob.com/react/react-blog-project-init.html)
- 分类：前端开发
- 技术：React
- 笔记类型：练习笔记
- 章节序号：3063

## 本章内容

本章带你从零开始，用 Vite 创建一个 React 博客项目，并理解 JSX 语法和项目结构。


## 环境准备

在开始之前，确保电脑上已安装 Node.js（建议 v16 以上）。

Node.js 是 JavaScript 的运行时环境，npm 是其自带的包管理器。


### 检查 Node.js 是否已安装

```text
$ node -v
v20.10.0
```

如果显示版本号，说明已安装。

如果没有，去 nodejs.org 下载 LTS 版本安装。


## 创建 React 项目

Vite 是目前最快的前端构建工具之一，对 React 有原生支持。

在终端中进入你想存放项目的目录，执行：

```text
$ npm create vite@latest blog-app -- --template react
```

这条命令告诉 Vite：创建一个名为 blog-app 的项目，使用 React 模板。

进入项目目录，安装依赖，启动开发服务器：

```text
$ cd blog-app
$ npm install
$ npm run dev
```

浏览器会自动打开 http://localhost:5173，看到 Vite + React 的默认欢迎页面，说明项目启动成功。

如果启动时报错提示缺少依赖，可以尝试执行 npm install 后重新运行。


## 项目目录结构详解

打开 blog-app 文件夹，你会看到以下结构：

```text
blog-app/
├── index.html              # 入口 HTML 文件
├── package.json            # 项目配置与依赖列表
├── vite.config.js          # Vite 构建工具配置
├── public/                 # 不经过编译的静态资源
├── src/
│   ├── main.jsx            # JS 入口，将 React 组件挂载到 DOM
│   ├── App.jsx             # 根组件，所有页面的外壳
│   ├── App.css             # App 组件的样式
│   ├── index.css           # 全局样式
│   └── assets/             # 需要编译的静态资源（图片等）
```


### 核心文件作用

index.html — 浏览器访问的入口文件。

里面有一个 <div id="root"></div>，React 应用就挂载到这个 div 上。

src/main.jsx — React 应用的启动文件。

它负责找到 #root 元素，然后用 createRoot 把 <App /> 组件渲染进去。


## 实例

src/App.jsx — 根组件。

它是所有页面的最外层容器，返回的 JSX 会被渲染到页面上。

<React.StrictMode> 是 React 的严格模式，仅在开发环境生效。它会对组件进行额外检查（如重复渲染），帮你发现潜在问题。生产构建时自动忽略。


## JSX 是什么？

JSX 是 JavaScript 的语法扩展，让你可以在 JS 中写类似 HTML 的代码。

React 组件本质上就是一个返回 JSX 的函数。


### JSX 与 HTML 的关键区别

为什么用 className 而不是 class？因为 JSX 本质是 JavaScript，而 class 是 JS 的保留关键字。同理，for 改为 htmlFor。


## 实例

记住核心规则：JSX 中花括号里可以放任何 JS 表达式——变量、函数调用、三元运算、数组 map 都行。


## React 组件 = 函数

React 函数组件的本质是：一个函数，接收 props 作为参数，返回一段 JSX。


## 实例

组件名必须大写字母开头。小写开头会被 React 当成普通 HTML 标签（div、span 等），大写开头才会被当做自定义组件处理。


## 动手：清空模板，写出博客骨架

把默认生成的 App.jsx 和 App.css 内容清掉，换成博客的基础结构。


## 实例


## 实例

保存后，浏览器会自动刷新，你会看到一个干净的博客骨架：顶部导航栏 + 中间内容区 + 底部页脚。


## 本章小结

本章你完成了三件事：用 Vite 创建了 React 项目、理解了 JSX 与 HTML 的关键区别、写出了博客的基础 JSX 骨架。

核心收获：React 组件就是返回 JSX 的函数，JSX 中花括号可以嵌入任何 JS 表达式。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `React 博客项目` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
