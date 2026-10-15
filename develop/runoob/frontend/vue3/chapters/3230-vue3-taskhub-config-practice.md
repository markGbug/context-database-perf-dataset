# Vue3：环境搭建

- 来源：[环境搭建](https://www.runoob.com/vue3/vue3-taskhub-config.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：练习笔记
- 章节序号：3230

## 本章内容

我们将使用 Vite 快速构建项目 TaskHub，Vite 内容参考：Vite 教程。


### 1. 创建项目

打开终端，执行以下命令创建 Vite + Vue3 项目（选择 Script Setup 语法）：

```text
# npm 命令
npm create vite@latest task-hub -- --template vue

# yarn 命令
yarn create vite task-hub --template vue

# pnpm 命令（推荐，速度更快）
pnpm create vite task-hub -- --template vue
```

执行成功后，输出如下：

启动成功后，访问终端提示的本地地址（默认 http://localhost:5173/），即可看到 Vue3 初始页面。

2. 项目目录

我们可以进入目录：

```text
cd task-hub
```

如果安装了 VS Code，可以使用 VS Code 的 code 命令打开目录，VS Code 内容参考：VS Code 教程。

```text
code .
```

启动后目录结构如下：

其他相关命令：

```text
# 安装依赖
npm install

# 启动
npm run dev
# 清理默认代码
```


### 2. 清理默认代码

删除 src/components/HelloWorld.vue。

清空 src/style.css。

修改 src/App.vue，代码如下：


## 实例


### 引入 Tailwind CSS

安装并配置原子化 CSS 框架。

```text
npm install tailwindcss @tailwindcss/vite
```

修改 vite.config.js：


## 实例

在 v4 中，Tailwind 作为一个 Vite 插件运行，它会自动扫描你的 .vue 文件。

在 src/style.css 中引入：

在 Tailwind v4 中，所有的配置（主题、变量）都直接写在 CSS 里。 重置 src/style.css 如下：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `环境搭建` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
