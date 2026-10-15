# Vue3：Vue3 博客项目

- 来源：[Vue3 博客项目](https://www.runoob.com/vue3/vue3-blog-project.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：练习笔记
- 章节序号：3237

## 本章内容

本章带你从零开始，用 Vite 创建一个 Vue3 博客项目，并理解项目里每个文件的作用。


## 环境准备

在开始之前，需要确保电脑上已经安装了 Node.js。

Node.js 是 JavaScript 的运行时环境，它让我们可以在浏览器之外运行 JS 代码。

Vue3 的开发工具链（Vite、npm）都依赖 Node.js。


### 检查 Node.js 是否已安装

打开终端（Windows 用 CMD 或 PowerShell，Mac 用终端），输入以下命令：

```text
$ node -v
v20.10.0
```

如果显示版本号（建议 v16 以上），说明已安装。

如果没有，去 nodejs.org 下载 LTS 版本安装即可。

安装 Node.js 时会自动附带 npm（Node 包管理器）。

验证命令：

```text
npm -v
```


## 创建 Vue3 项目

Vue 官方推荐使用 create-vue 脚手架工具来初始化项目。

在终端中进入你想存放项目的目录，执行：

```text
npm create vue@latest blog-app
```

执行后会出现一系列选项，按以下方式选择：

选择完成后，按提示依次执行：

```text
$ cd blog-app
$ npm install
$ npm run dev
```

此时浏览器会自动打开 http://localhost:5173，看到 Vue 的默认欢迎页面，说明项目启动成功。

npm install 会根据 package.json 下载所有依赖包到 node_modules 目录，这一步需要联网，首次执行可能需要几分钟。


## 项目目录结构详解

打开 blog-app 文件夹，你会看到以下结构：

```text
blog-app/
├── index.html              # 入口 HTML 文件
├── package.json            # 项目配置与依赖列表
├── vite.config.js          # Vite 构建工具配置
├── public/                 # 不经过编译的静态资源
├── src/
│   ├── main.js             # JS 入口，创建并挂载 Vue 应用
│   ├── App.vue             # 根组件，所有页面的外壳
│   ├── assets/             # 需要编译的静态资源（CSS、图片）
│   ├── components/         # 可复用的 Vue 组件
│   ├── views/              # 页面级组件（路由对应的页面）
│   ├── router/             # 路由配置
│   └── stores/             # Pinia 状态管理
```


### 核心文件作用

index.html — 浏览器访问的入口文件。

Vite 会自动将 src/main.js 注入到这个文件中，你不需要手动引入任何 JS。

src/main.js — Vue 应用的启动文件。

它负责创建 Vue 应用实例、注册插件（路由、状态管理）、并将应用挂载到 HTML 页面上。

src/App.vue — 根组件。

它是所有页面的最外层容器，通常包含导航栏、页脚和路由出口。


## 单文件组件（SFC）

Vue 中每个 .vue 文件称为一个「单文件组件」（Single File Component）。

它把同一个组件的模板、逻辑和样式封装在一起，一个文件就是一个独立的功能单元。


### SFC 三段式结构


## 实例

这三个标签的顺序可以任意排列，但业界习惯是：script → template → style。

scoped 属性让当前组件的样式只作用于自身，不会污染其他组件。这是 Vue 单文件组件的核心特性之一。


## 模板语法 vs JSX

Vue 默认使用 模板语法 来编写界面。

模板语法就是写在 <template> 中的、带 Vue 特殊指令的 HTML。

本教程全部使用模板语法，因为它是 Vue 最自然、最适合初学者的写法。


## 动手：清空模板，写出博客骨架

现在把默认生成的 App.vue 内容清空，换成我们博客的基础骨架。


## 实例

保存后，浏览器会自动刷新，你会看到一个干净的博客骨架：顶部导航栏 + 中间内容区 + 底部页脚。

这就是我们后续所有章节的起点。


## 本章小结

本章你完成了三件事：用 Vite 创建了 Vue3 项目、理解了目录结构和 SFC 三段式、写出了博客的基础 HTML 骨架。

核心收获：知道一个 .vue 文件由 template / script / style 三部分组成，以及如何让 Vue 项目跑起来。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Vue3 博客项目` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
