# Vue3：Vue3 Tailwind CSS

- 来源：[Vue3 Tailwind CSS](https://www.runoob.com/vue3/vue3-tailwindcss.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：练习笔记
- 章节序号：3225

## 本章内容

在 Vue 项目中使用 Tailwind CSS 是一个很流行的选择，因为它提供了一种实用工具优先的方法来编写 CSS，使得你可以直接在类名中应用样式，这种方法使得样式编写更加简洁和直观。

Tailwind CSS 教程：https://www.runoob.com/tailwindcss/tailwindcss-tutorial.html

Tailwind CSS 官网：https://tailwindcss.com/

Github 地址：https://github.com/tailwindlabs/tailwindcss

Tailwind CSS 是一个功能强大的 CSS 框架，它通过实用工具优先的方法使得样式编写更加简洁和模块化。与传统的基于类的 CSS 框架不同，Tailwind 提供了一组低级实用工具类，这些类可以直接在 HTML 元素上使用，以便快速、灵活地构建自定义设计。

以下是一个使用 Vue 3 和 Tailwind CSS 的完整入门示例，展示了如何将 Tailwind CSS 与 Vue 3 集成并使用其功能来构建响应式界面。


### 安装 Vue 3 和 Tailwind CSS

首先，确保你已经安装了 Vue 3 和 Tailwind CSS。

安装 Vue 3 在终端中执行 npm create vue@latest 命令创建一个新的 Vue 3 项目：

```text
npm create vue@latest
```

在输出窗口中，输入项目名称，然后一路回车即可：

执行以上命令需要设置一些初始化的选项，使用方向键选择即可。

进入初始化的目录 vue-tailwind-app，安装依赖：

```text
cd vue-tailwind-app
npm install
```

安装 Tailwind CSS 安装 Tailwind CSS 和相关依赖：

```text
npm install -D tailwindcss@latest postcss@latest autoprefixer@latest
npx tailwindcss init -p
```

创建完成，目录结构如下：

配置 Tailwind CSS 打开 tailwind.config.js 文件并修改为：


## 实例

添加 Tailwind 指令 在 src/assets 目录下创建一个 styles.css 文件，并添加以下内容：

```text
/* src/assets/styles.css */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

然后在 src/assets/main.js 中导入该文件：

```text
import './assets/styles.css
```


## 创建 Vue 组件和样式

现在，你可以开始编写你的 Vue 3 组件，并使用 Tailwind CSS 来美化页面。


### App.vue

App.vue 是应用的主要组件，它包含了 Vue 3 和 Tailwind CSS 的基础用法。


## 实例

另外我们可以在 vite.config.js 文件中设置自己的端口，比如以下设置端口后为 3000：


## 实例

设置完成后，执行以 npm run dev 命令输出内容如下：

```text
# npm run dev

> vue-tailwind-app@0.0.0 dev
> vite


  VITE v6.0.3  ready in 333 ms

  ➜  Local:   http://localhost:3000/
  ➜  Network: use --host to expose
  ➜  Vue DevTools: Open http://localhost:3000/__devtools__/ as a separate window
  ➜  Vue DevTools: Press Option(⌥)+Shift(⇧)+D in App to toggle the Vue DevTools

  ➜  press h + enter to show help
```

访问 http://localhost:3000/，显示如下：

接下来我们尝试创建一个列表，修改 App.vue 文件，代码如下所示：


## 实例

代码解析：

- 头部 (header): 使用 bg-blue-600 设置背景颜色，text-white 设置文本颜色，py-4 设置上下内边距，container mx-auto 用来设置固定宽度并居中。
- 列表 (main): 使用 flex-grow 来使列表部分填满剩余空间，py-8 添加垂直内边距。每个列表项使用了 p-4, bg-white, border, rounded-lg, shadow-md 等 Tailwind 类来设置外观。
- 底部 (footer): 使用 bg-gray-800 设置深色背景，text-white 设置白色文本，py-4 设置内边距。

访问 http://localhost:3000/，显示如下：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Vue3 Tailwind CSS` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
