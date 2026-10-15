# Next.js：Next.js 目录结构

- 来源：[Next.js 目录结构](https://www.runoob.com/nextjs/nextjs-layouts-and-pages.html)
- 分类：前端开发
- 技术：Next.js
- 笔记类型：练习笔记
- 章节序号：3024

## 本章内容

在 Next.js 中，目录结构是基于文件系统的路由机制来组织的，这意味着你的文件和文件夹结构直接决定了你应用的路由和页面布局。

- app/ 目录用于存放页面和布局文件，是 Next.js 中的核心目录。
- public/ 用于存放公开的静态资源文件。
- styles/ 用于存放样式文件。
- node_modules/ 存放项目的所有依赖包。
- package.json 是项目的配置文件，包含项目依赖和脚本命令。
- next.config.js 用于定制 Next.js 的配置。


### 根目录（Root Directory）

根目录下通常包含一些基础配置文件和依赖项。常见的文件和文件夹如下：

```text
my-next-app/
├── app/                 # 存放应用页面和布局文件
├── public/              # 存放静态资源文件（如图片、字体）
├── styles/              # 存放样式文件（CSS、Sass等）
├── node_modules/        # 存放项目依赖
├── package.json         # 项目配置文件
├── next.config.js       # Next.js 配置文件（可选）
└── .gitignore           # Git 忽略文件
```

- app/：这个目录是 Next.js 中的新方式来组织页面和布局文件。所有的路由和页面都基于这个目录来创建。
- public/：这个目录存放的是公开的静态文件，比如图片、字体、favicon 等。你可以直接通过 URL 访问这些文件。
- styles/：存放你的 CSS、Sass 或其他样式文件。


### app/ 目录

app/ 目录是 Next.js 中的核心，存放页面、布局和其他相关文件。

以下是 app/ 目录的一些常见结构：

```text
app/
├── layout.tsx           # 根布局文件
├── page.tsx             # 根页面
└── [slug]/              # 动态路由目录
    ├── page.tsx         # 动态页面
    └── layout.tsx       # 特定页面的布局
```

- layout.tsx：在这个文件中定义了根布局或页面布局，通常用于设置全局结构（如 <html> 和 <body> 标签）。所有子页面都会被嵌套在这个布局内。
- page.tsx：每个页面组件都应该有一个 page.tsx 文件。这个文件代表该路由对应的页面内容。例如，app/page.tsx 对应的是根路径 (/) 的页面。
- 动态路由：Next.js 支持动态路由，动态路由目录的名称用方括号包围，如 [slug]。这意味着你可以根据 URL 中的不同部分加载不同的页面。例如，[slug]/page.tsx 会根据 slug 参数动态渲染页面。


### public/ 目录

这个目录用于存放静态资源，它允许你将图片、字体、图标等资源暴露在应用中，且能通过直接访问文件路径来加载。

```text
public/
├── images/              # 存放图片文件
├── fonts/               # 存放字体文件
└── favicon.ico          # 网站图标
```

- 文件可以通过 /images/ 等路径直接访问。例如，public/images/logo.png 可以通过 http://localhost:3000/images/logo.png 访问。


### styles/ 目录

在 styles/ 目录中，你可以组织和管理你的样式文件。Next.js 支持 CSS 模块、全局样式和其他 CSS 解决方案。

```text
styles/
├── Home.module.css      # CSS 模块化样式
└── globals.css          # 全局样式
```

- Home.module.css：这是一个 CSS 模块文件，默认情况下，Next.js 会自动为每个组件使用 CSS 模块，确保样式作用域仅限于该组件。
- globals.css：存放全局样式，通常用于设置全局字体、颜色等。


### node_modules/ 目录

这个目录存放项目的所有依赖包。它由 npm 或 yarn 根据 package.json 文件中的依赖信息自动生成，不需要手动操作。


### package.json 文件

package.json 是项目的核心配置文件，记录了项目的依赖、脚本和其他元数据。你可以在这里定义启动、构建和开发等命令。


## 实例


### next.config.js 文件（可选）

这是一个可选的配置文件，用于配置 Next.js 的行为。例如，你可以在这个文件中设置静态文件的优化、路由规则、Webpack 配置等。


## 实例


## 项目结构实例

以下是一个典型的 Next.js 项目结构示例：


## 实例: Next.js 项目结构


### app 目录与传统 pages 目录的对比

Next.js 13 引入了新的 app 目录，它与传统的 pages 目录共存，并提供了更灵活的路由和布局组织方式。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Next.js 目录结构` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
