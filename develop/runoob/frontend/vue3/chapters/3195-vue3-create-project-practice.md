# Vue3：Vue3 创建项目

- 来源：[Vue3 创建项目](https://www.runoob.com/vue3/vue3-create-project.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：练习笔记
- 章节序号：3195

## 本章内容

在上一章节 Vue3 安装 我们使用了 npm init 命令创建过一个项目，本章节我们主要介绍 npm create 命令创建项目以及使用 vue ui 命令打开图形化的安装界面。

Vue 开发推荐的 IDE 配置是 Visual Studio Code + Vue - Official 扩展：

其他的 IDE 支持如下：

- Sublime Text 通过 LSP-Volar 支持。
- vim / Neovim 通过 coc-volar 支持。
- emacs 通过 lsp-mode 支持。


## npm create 命令

使用 npm create 命令来创建 Vue 项目，通常是通过 Vite（Vue 官方推荐的构建工具）来创建 Vue 应用。

在 Vite 中，npm create 是用来执行脚手架工具（如 vite@latest）来快速生成一个新的项目模板。

Vite 详细内容可以参考：Vite 教程。

npm create 命令创建项目语法格式如下：

```html
npm create vite@latest <project-name> --template vue
```

说明：

- npm create ：用于执行项目模板的命令，它会创建一个新的项目，并从给定的模板中初始化。
- vite@latest ：vite 是创建 Vue 3 项目的工具，@latest 是指定使用最新版的 Vite，确保你创建的项目是基于最新版本的 Vite。如果没有 @latest，npm 会尝试使用当前安装的版本。
- <project-name>：新创建项目的文件夹名称。命令会创建一个文件夹，并将模板代码放入其中。例如，运行 npm create vite@latest my-vue-app --template vue 会在当前目录下创建一个名为 my-vue-app 的文件夹，并将 Vue 项目的模板文件放入其中。
- --template vue：--template vue 指定了要使用的模板类型。Vite 支持多种模板，vue 是专门为 Vue 3 提供的模板。还有其他模板，如 vanilla、react、svelte 等。

接下来我们创建 runoob-vue3-app 项目：

```text
npm create vite@latest
```

执行以上命令会让你先输入项目名，并选择一个框架：

```text
> Project name: … runoob-vue3-app
? Select a framework: › - Use arrow-keys. Return to submit.
❯   Vanilla
    Vue
    React
    Preact
    Lit
    Svelte
    Solid
    Qwik
    Angular
    Others
```

Vite 支持多个模板，常见的有：

- vue: Vue 3 项目（默认使用 Vue 3）
- vanilla: 无框架的基本模板
- react: React 项目
- svelte: Svelte 项目
- preact: Preact 项目
- 还可以根据具体需求选择其他模板。

可以使用方向键来选择，我们选择 Vue，然后出现选项变体界面，我们可以选择 JavaScript 快速开始：

```text
> Project name: … runoob-vue3-app
> Select a framework: › Vue
> Select a variant: › JavaScript

Scaffolding project in /Users/runoob/runoob-test/runoob-vue3-app...

Done. Now run:

  cd runoob-vue3-app
  npm install
  npm run dev
```

安装完成后，我们进入项目目录：

```text
cd runoob-vue3-app
```

整个目录结构如下图：

安装依赖，并启动应用：

```text
npm install
npm run dev
```


## 实例


## vue ui 命令

除了使用 vue create 命令创建项目，我们还可以使用可视化创建工具来创建项目。

运行命令：

```text
$ vue ui
->  Starting GUI...
->  Ready on http://localhost:8000
...
```

执行以上命令，会在浏览器弹出一个项目管理的界面：

我们可以点击"创建"选项来创建一个项目，选择底部"在此创建项目"，页面上方也可以选择路径：

配置选择默认即可:

接下来就等待完成安装，安装完成管理界面如下：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Vue3 创建项目` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
