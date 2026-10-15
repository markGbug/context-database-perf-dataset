# Tailwind CSS：Tailwind CSS4 安装(NPM)

- 来源：[Tailwind CSS4 安装(NPM)](https://www.runoob.com/tailwindcss/tailwindcss4-installbynpm.html)
- 分类：前端开发
- 技术：Tailwind CSS
- 笔记类型：练习笔记
- 章节序号：3097

## 本章内容

在开始之前，确保你已经安装了 Node.js 和 npm，你可以通过以下命令检查它们是否已经安装：

```text
node -v
npm -v
```

如果你的系统还不支持 Node.js 及 NPM 可以参考我们的 Node.js 教程。

国内使用 npm 速度很慢，你可以使用淘宝定制的 cnpm (gzip 压缩支持) 命令行工具代替默认的 npm:

```text
$ npm install -g cnpm --registry=https://registry.npmmirror.com
$ npm config set registry https://registry.npmmirror.com
```

这样就可以使用 cnpm 命令来安装模块了：

```text
$ cnpm install [name]
```

更多信息可以查阅：http://npm.taobao.org/。


## 安装 Tailwind CSS

与 Tailwind CSS 3 相比较，Tailwind CSS 4 自动检测 HTML 和 JavaScript 等文件，省去了手动配置内容源的麻烦。


### npm 安装

从零开始使用 Tailwind CSS 的最简单和最快方法是通过 Tailwind CLI 工具。

通过 npm 安装 在本地项目中安装并配置 Tailwind CSS：

```text
npm install tailwindcss @tailwindcss/cli
```

1、在 CSS 中导入 Tailwind: 在 CSS 文件中添加 @import "tailwindcss";。

比如在 src/input.css 文件开头导入：


## src/input.css 文件

2、启动 Tailwind CLI 构建流程：运行 CLI 工具以扫描源文件中的类并构建 CSS。

```text
npx @tailwindcss/cli -i ./src/input.css -o ./src/output.css --watch
```

3、在 HTML 中开始使用 Tailwind：将编译后的 CSS 文件添加到 <head> 中，并开始使用 Tailwind 的实用类来设置内容的样式。


## src/index.html 文件


### 作为 Vite 插件安装

Vite 详细内容可以参见：Vite 教程。

将 Tailwind CSS 作为 Vite 插件安装是将其与 Laravel、SvelteKit、React Router、Nuxt 和 SolidJS 等框架集成的最无缝的方式。

1、安装 Tailwind CSS

通过 npm 安装 tailwindcss 和 @tailwindcss/vite：

```text
npm install tailwindcss @tailwindcss/vite
```

2、配置 Vite 插件

在 Vite 配置文件 vite.config.ts 中添加 @tailwindcss/vite 插件：


## vite.config.ts 文件

3、导入 Tailwind CSS

在的 CSS 文件中添加 @import 以导入 Tailwind CSS：

```text
@import "tailwindcss";
```

4、启动构建流程

运行构建流程，使用 npm run dev 或你在 package.json 文件中配置的其他命令：

```text
npm run dev
```

5、在 HTML 中开始使用 Tailwind

确保编译后的 CSS 已包含在 <head> 中（框架可能会自动处理），然后开始使用 Tailwind 的实用类来设置内容的样式。


## 实例


### 作为 PostCSS 插件安装

将 Tailwind CSS 作为 PostCSS 插件安装可以将其与 Next.js 和 Angular 等框架无缝结合。

1、安装 Tailwind CSS

通过 npm 安装 tailwindcss、@tailwindcss/postcss 和 postcss。

```text
npm install tailwindcss @tailwindcss/postcss postcss
```

2、将 Tailwind 添加到 PostCSS 配置中

在项目的 postcss.config.mjs 文件中（或任何配置 PostCSS 的地方）添加 @tailwindcss/postcss。


## postcss.config.mjs 文件

3、导入 Tailwind CSS

在 CSS 文件中添加 @import 以导入 Tailwind CSS。

```text
@import "tailwindcss";
```

4、启动构建流程

运行构建流程，使用 npm run dev 或你在 package.json 文件中配置的其他命令。

```text
npm run dev
```

5、在 HTML 中开始使用 Tailwind

确保编译后的 CSS 已包含在 <head> 中（框架可能会自动处理），然后开始使用 Tailwind 的实用类来设置内容的样式。


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Tailwind CSS4 安装(NPM)` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
