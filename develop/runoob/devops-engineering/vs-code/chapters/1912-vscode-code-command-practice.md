# VS Code：VSCode code 命令

- 来源：[VSCode code 命令](https://www.runoob.com/vscode/vscode-code-command.html)
- 分类：DevOps / 工程化
- 技术：VS Code
- 笔记类型：练习笔记
- 章节序号：1912

## 本章内容

在 Visual Studio Code 中，code 命令是一个命令行工具，用于快速打开 VS Code 并执行一些与代码相关的操作。

code 命令直接可以帮助开发者从终端或命令提示符中直接启动 VS Code 或处理特定的任务。

最常用的方式就是使用 code 命令直接从命令行中打开文件目录，此时需要先安装 code 命令。

Windows 系统安装 VS Code 后，code 命令会自动注册到系统环境变量中，如果未注册，可以手动添加 VS Code 的安装路径到 PATH 环境变量中。

启用 VSCode 的 code 命令 非常简单，先打开命令面板：

- macOS 系统快捷键：⇧⌘P（command + shift + p）
- Windows/Linux 快捷键: Ctrl + Shift + P

搜索安装 >shell command:

然后选择 在 PATH 中 安装"code"命令 - Shell Command: Install 'code' command in PATH 即可为系统 PATH 路径添加了 code 命令的引用。

我们可以通过命令行打开文件、安装扩展、修改显示语言，甚至查看诊断信息。

以下是一些常用的命令行选项，可以通过 code --help 命令查看：

我们可以在命令行中使用 code . 命令让文件夹在 VS Code 中打开：


### code 命令的常用功能

1. 打开文件或文件夹

```text
code <文件路径>
```

例如打开 app.js 文件：

```text
code app.js
```

打开文件夹（以工作区的方式）：

```text
code <文件夹路径>
```

例如打开 my-project 文件夹：

```text
code my-project
```

2. 创建新文件

如果指定的文件不存在，code 会创建该文件并打开它：

```text
code newfile.js
```

3. 以当前目录为工作区打开 VS Code

直接运行 code 命令会以当前终端所在目录为工作区启动 VS Code：

```text
code .
```

4. 对比文件

code 命令支持文件内容对比：

```text
code --diff <文件1> <文件2>
```

示例：

```text
code --diff index.html index-backup.html
```

5. 查看帮助

查看 code 命令的所有可用选项：

```text
code --help
```


## 使用 code 命令打开 vue 项目


### 创建 vue 项目

打开终端或命令提示符，输入以下命令创建 vue 项目：

```text
npm create vue@latest
```

系统会提示输入项目名称，我这边输入 runoob-vue3-app：

```text
Vue.js - The Progressive JavaScript Framework

? 请输入项目名称： › runoob-vue3-app
```

之后会有一些选项，可以根据自己的需求选择，或者一路回车：

```java
Vue.js - The Progressive JavaScript Framework

> 请输入项目名称： … runoob-vue3-app
> 是否使用 TypeScript 语法？ … 否 / 是
> 是否启用 JSX 支持？ … 否 / 是
> 是否引入 Vue Router 进行单页面应用开发？ … 否 / 是
> 是否引入 Pinia 用于状态管理？ … 否 / 是
> 是否引入 Vitest 用于单元测试？ … 否 / 是
> 是否要引入一款端到端（End to End）测试工具？ › 不需要
> 是否引入 ESLint 用于代码质量检测？ › 否

正在初始化项目 /Users/Runoob/runoob-vue3-app...

项目初始化完成，可执行以下命令：

  cd runoob-vue3-app
  npm install
  npm run dev
```

项目创建完成后，进入项目文件夹并安装依赖：

```text
cd runoob-vue3-app
npm install
```

安装依赖可能也需要几分钟。

输入以下命令快速启动你的 Vue 应用：

```text
npm run dev
```

在浏览器中打开 http://localhost:5173，显示如下：

按下 Ctrl+C 可以停止 vue-cli-service 服务器。


### 使用 code 命令打开 vue 项目

从终端或命令提示符中进入我们创建的 Vue 项目文件夹 runoob-vue3-app，然后使用 code 命令让项目在 VS Code 中打开：

```text
cd runoob-vue3-app
code .
```

VS Code 将启动并在文件资源管理器中显示你的 Vue 项目，显示如下：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `VSCode code 命令` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
