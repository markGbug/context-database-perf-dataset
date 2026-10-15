# Next.js：Next.js Tailwind CSS

- 来源：[Next.js Tailwind CSS](https://www.runoob.com/nextjs/nextjs-tailwindcss.html)
- 分类：前端开发
- 技术：Next.js
- 笔记类型：练习笔记
- 章节序号：3029

## 本章内容

在 Next.js 项目中使用 Tailwind CSS 是一个很流行的选择，因为它提供了一种实用工具优先的方法来编写 CSS，使得你可以直接在类名中应用样式，这种方法使得样式编写更加简洁和直观。

Tailwind CSS 教程：https://www.runoob.com/tailwindcss/tailwindcss-tutorial.html

Tailwind CSS 官网：https://tailwindcss.com/

Github 地址：https://github.com/tailwindlabs/tailwindcss

Tailwind CSS 是一个功能强大的 CSS 框架，它通过实用工具优先的方法使得样式编写更加简洁和模块化。与传统的基于类的 CSS 框架不同，Tailwind 提供了一组低级实用工具类，这些类可以直接在 HTML 元素上使用，以便快速、灵活地构建自定义设计。

以下是如何在 Next.js 项目中使用 Tailwind CSS 的详细步骤。


### 1. 安装 Tailwind CSS

如果你是从零开始创建一个新的 Next.js 项目，可以使用 create-react-app，如果你已经有一个现有的 React 项目，可以跳过项目创建步骤。

创建新的 Next.js 项目：

```text
npx create-next-app@latest my-next-app
```

创建的时候，就会提示是否安装 Tailwind CSS，我们可以选 Yes：

```text
...
Would you like to use Tailwind CSS? No / Yes
Would you like your code inside a `src/` directory? No / Yes
Would you like to use App Router? (recommended) No / Yes
...
```

安装 Tailwind CSS

页可以在你的项目目录中运行以下命令来安装 Tailwind CSS 及其所需的依赖项：

```text
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

这将创建一个 tailwind.config.ts 文件和一个 postcss.config.mjs 文件。


### 2. 配置 Tailwind CSS

在 Tailwind 配置文件 tailwind.config.ts 中，添加将使用 Tailwind 类名的文件路径。

一般默认情况下，都配置好了，我们无需修改：


## 实例

我们无需修改 postcss.config.mjs 文件。


### 3. 添加 Tailwind 的基础样式

将 Tailwind CSS 指令添加到应用程序的全局样式表中，Tailwind 会使用这些指令来注入它生成的样式。

在你的项目中，打开 app/globals.css 文件，并添加以下内容来包含 Tailwind 的基础样式、组件样式和实用工具样式：

```text
/* app/globals.css */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

在根布局 app/layout.tsx 中导入 globals.css 样式表，将样式应用到应用中的每个路由：


## 实例


### 4. 使用 Tailwind CSS 编写样式

安装 Tailwind CSS 并添加全局样式后，你可以在应用中使用 Tailwind 的实用工具类：


## app/page.tsx 文件代码：

运行：

```text
npm run dev
```

然后打开你的浏览器并导航到 http://localhost:3000，你应该会看到一个使用 Tailwind CSS 样式的简单 React 应用。

通过以上步骤，你已经成功地在 Next.js 项目中集成了 Tailwind CSS，并使用它来编写样式。Tailwind CSS 的实用工具类名使得你可以快速地为你的组件添加样式，同时保持样式代码的简洁和模块化。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Next.js Tailwind CSS` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
