# TypeScript：使用 VS Code 开发 TypeScript

- 来源：[TypeScript VS Code](https://www.runoob.com/typescript/ts-vscode.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：学习笔记
- 章节序号：3121

## 本章内容

很多 IDE 都有支持 TypeScript 插件，如：VS Code，Sublime Text 2，WebStorm / PHPStorm，Eclipse 等。

本章节主要介绍 VS Code，VS Code 是一个可以运行于 Mac OS X、Windows 和 Linux 之上的，针对于编写现代 Web 和云应用的跨平台源代码编辑器，由 Microsoft 公司开发。

VS Code 原生内置 TypeScript 语言语法支持，但不含 TypeScript 编译工具 tsc，如需将 TS 源码转译为 JS（执行命令 tsc HelloWorld.ts），需要在全局或项目工作区单独安装 TypeScript 编译器。 VS Code 教程：https://www.runoob.com/vscode/vscode-tutorial.html

另外国内阿里与字节也有基于 VS Code 开发的 AI IDE：


### 安装 TypeScript 编译器

最简安装方式是通过 Node.js 包管理器 npm 安装，已装好 npm 的前提下，执行下方命令即可全局（-g）安装：

```text
npm install -g typescript
```

安装完成后可通过输出版本号验证：

```text
tsc --version
```


### Windows 上安装 Visual Studio Code

1、下载 Visual Studio Code。

2、双击 VSCodeSetup.exe 图标 安装。

3、安装完成后，打开 Visual Studio Code 界面类似如下：

4、 我们可以在左侧窗口中点击当前编辑的代码文件，选择 open in command prompt（在终端中打开），这时候我们就可以在屏幕的右侧下半部分使用 tsc 命令来执行 TypeScript 文件代码了。


### Mac OS X 安装 Visual Studio Code

Mac OS X 安装配置 Visual Studio Code 可以查看： https://code.visualstudio.com/Docs/editor/setup


### Linux 安装 Visual Studio Code

Linux 安装配置 Visual Studio Code 可以查看： https://code.visualstudio.com/Docs/editor/setup


## 入门示例：Hello World

我们以 Node.js 环境的极简 Hello World 项目为例，新建项目文件夹并打开 VS Code：

```text
mkdir HelloWorld
cd HelloWorld
code .
```

在资源管理器中新建文件 helloworld.ts。

写入下述 TS 代码，能看到 TS 专属关键字 let 与字符串类型标注：

```javascript
let message : string = "Hello World";
console.log(message);
```

打开【集成终端】（快捷键 kb(workbench.action.terminal.toggleTerminal)），输入 tsc helloworld.ts 编译代码，编译成功后会自动生成 JS 文件 helloworld.js。

本机已安装 Node.js 时，运行 node helloworld.js 即可执行代码。

打开编译后的 helloworld.js 可以发现：代码移除了类型声明，let 被降级为 ES5 的 var：

```javascript
var message = "Hello World";
console.log(message);
```


## 智能提示（IntelliSense）

智能提示提供代码自动补全、悬浮文档、函数参数签名提示，提升编码效率与准确率。

VS Code 对单个 TS 文件、带 tsconfig.json 配置的 TS 项目均提供全套智能提示。


### 悬浮文档提示

鼠标悬浮在任意 TS 标识符上，快速查看变量/函数的类型与说明文档； 快捷键 kb(editor.action.showHover) 可在光标位置手动唤起悬浮提示。


### 函数签名提示

编写函数调用代码时，编辑器自动展示函数入参说明，并高亮当前正在填写的参数； 输入左括号 ( 或逗号 , 自动触发签名提示，快捷键 kb(editor.action.triggerParameterHints) 手动唤起。


## 代码片段（Snippets）

除智能补全外，VS Code 内置基础 TS 代码片段，输入关键字时自动弹出快捷模板。

可安装第三方扩展扩充片段库，也能自定义 TS 代码片段，详情参考【用户自定义代码片段】文档。

小贴士：在配置文件中将 editor.snippetSuggestions 设为 "none" 可关闭片段提示；如需保留，可配置片段展示优先级：top（置顶）、bottom（置底）、inline（和普通提示混排、字母排序，默认配置）。


## 错误与警告提示

TS 语言服务实时校验代码，自动标记语法与逻辑问题：

- 编辑器状态栏汇总当前项目错误、警告总数；
- 点击状态栏统计数字，或快捷键 kb(workbench.actions.view.problems) 打开【问题】面板，罗列全部报错；
- 存在异常的代码行，行内标红提示，同时在右侧缩略标尺标注错误位置。

快捷键 kb(editor.action.marker.nextInFiles) / kb(editor.action.marker.prevInFiles) 跳转当前文件上下一处问题，弹窗展示详情与可用快速修复。


## 代码跳转导航

依托导航功能快速浏览大型 TS 项目源码：

- 跳转到定义 kb(editor.action.revealDefinition)：定位标识符源码定义处；
- 预览定义 kb(editor.action.peekDefinition)：弹窗预览源码，不切换当前文件；
- 查找所有引用 kb(editor.action.goToReferences)：列出项目内所有调用该标识符的位置；
- 跳转至类型定义：定位变量所属的类型源码（类实例会跳转至类本体，而非实例创建代码）；
- 跳转至实现 kb(editor.action.goToImplementation)：查找接口/抽象方法的具体实现代码。

通过命令面板（kb(workbench.action.showCommands)）的符号检索实现快速跳转：

- 当前文件内查找符号 kb(editor.action.gotoSymbol)
- 全工作区检索符号 kb(workbench.action.showAllSymbols)


## 代码格式化

VS Code 内置 TS 格式化工具，默认规则开箱即用。

通过 js/ts.format.* 系列配置自定义格式化规则（例如大括号单独换行）不需要内置格式化时，设置:

```text
"js/ts.format.enable": false
```

关闭。

如需贴合团队自定义编码规范，可在插件市场安装专用格式化扩展。


## 代码重构

VS Code 自带常用 TS 重构能力，如提取函数、提取常量。选中待重构代码，点击编辑器侧边灯泡图标或快捷键 kb(editor.action.quickFix) 调出重构菜单。

更多重构规则、自定义重构快捷键参考【TypeScript代码重构】文档。


### 统一重命名

选中变量/方法，快捷键 kb(editor.action.rename) 一键修改项目内所有同名标识符。


## 调试功能

VS Code 原生完善支持 TS 调试，兼容源码映射（SourceMap），支持断点、变量查看、调用栈追溯、调试控制台交互；详情查阅【TS调试指南】与通用调试文档。


### 前端网页调试

借助内置 Chrome/Edge 调试插件，或 Firefox 调试扩展，调试浏览器端 TS 代码。


### 后端Node调试

使用内置调试器调试 Node.js 服务，官方配套教程可快速上手 Express 项目调试。


## 代码校验工具（Linter）

Linter 用于检查代码隐患、规范编码风格。VS Code 未内置 TS 校验工具，可在插件市场安装对应扩展。

主流工具 ESLint 全面兼容 TS，安装 ESLint 插件后，编辑器实时标错，大量问题支持一键快速修复；typescript-eslint 文档指导 TS 项目 ESLint 环境配置。


## 复习重点

- 能说明 `TypeScript VS Code` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
