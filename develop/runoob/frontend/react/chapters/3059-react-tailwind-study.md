# React：React Tailwind CSS

- 来源：[React Tailwind CSS](https://www.runoob.com/react/react-tailwind.html)
- 分类：前端开发
- 技术：React
- 笔记类型：学习笔记
- 章节序号：3059

## 本章内容

在 React 项目中使用 Tailwind CSS 是一个很流行的选择，因为它提供了一种实用工具优先的方法来编写 CSS，使得你可以直接在类名中应用样式，这种方法使得样式编写更加简洁和直观。

Tailwind CSS 教程：https://www.runoob.com/tailwindcss/tailwindcss-tutorial.html

Tailwind CSS 官网：https://tailwindcss.com/

Github 地址：https://github.com/tailwindlabs/tailwindcss

Tailwind CSS 是一个功能强大的 CSS 框架，它通过实用工具优先的方法使得样式编写更加简洁和模块化。与传统的基于类的 CSS 框架不同，Tailwind 提供了一组低级实用工具类，这些类可以直接在 HTML 元素上使用，以便快速、灵活地构建自定义设计。

以下是如何在 React 项目中使用 Tailwind CSS 的详细步骤。


### 1. 安装 Tailwind CSS

如果你是从零开始创建一个新的 React 项目，可以使用 create-react-app，如果你已经有一个现有的 React 项目，可以跳过项目创建步骤。

创建新的 React 项目：

```text
npx create-react-app my-app
cd my-project
```

安装 Tailwind CSS

在你的项目目录中运行以下命令来安装 Tailwind CSS 及其所需的依赖项：

```text
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

这将创建一个 tailwind.config.js 文件和一个 postcss.config.js 文件。

你的项目结构应该类似于以下内容：

```text
my-app/
├── node_modules/
├── public/
├── src/
│   ├── App.js
│   ├── index.css
│   ├── index.js
│   └── ...（其他文件）
├── .gitignore
├── package-lock.json
├── package.json
├── postcss.config.js
└── tailwind.config.js
```


### 2. 配置 Tailwind CSS

编辑 tailwind.config.js 文件，配置 Tailwind 以清理未使用的样式。更新 content 数组以包含你的所有模板文件路径：


## 实例


### 3. 添加 Tailwind 的基础样式

在你的项目中，打开 src/index.css 文件，并添加以下内容来包含 Tailwind 的基础样式、组件样式和实用工具样式：

```text
@tailwind base;
@tailwind components;
@tailwind utilities;
```


### 4. 使用 Tailwind CSS 编写样式

现在你可以开始在你的 React 组件中使用 Tailwind CSS 类名来编写样式。


## App.js 文件代码：

确保你的 src/index.js 文件正确导入了 App 组件，并渲染到 DOM 中。


## src/index.js 文件代码：

运行：

```text
npm start
```

然后打开你的浏览器并导航到 http://localhost:3000，你应该会看到一个使用 Tailwind CSS 样式的简单 React 应用。

通过以上步骤，你已经成功地在 React 项目中集成了 Tailwind CSS，并使用它来编写样式。Tailwind CSS 的实用工具类名使得你可以快速地为你的组件添加样式，同时保持样式代码的简洁和模块化。


## 复习重点

- 能说明 `React Tailwind CSS` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
