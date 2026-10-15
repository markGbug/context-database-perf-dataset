# TypeScript：TypeScript 安装

- 来源：[TypeScript 安装](https://www.runoob.com/typescript/ts-install.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：学习笔记
- 章节序号：3120

## 本章内容

本文介绍 TypeScript 环境的安装。

我们需要使用到 npm 工具安装，如果你还不了解 npm，可以参考我们的NPM 使用介绍。


### NPM 安装 TypeScript

如果你的本地环境已经安装了 npm 工具，可以使用以下命令来安装。

使用国内镜像：

```text
npm config set registry https://registry.npmmirror.com
```

安装 typescript：

```text
npm install -g typescript
```

安装完成后我们可以使用 tsc 命令来执行 TypeScript 的相关代码，以下是查看版本号：

```text
$ tsc -v
Version 3.2.2
```

然后我们新建一个 app.ts 的文件，代码如下：

```javascript
var message:string = "Hello World"
console.log(message)
```

通常我们使用 .ts 作为 TypeScript 代码文件的扩展名。

然后执行以下命令将 TypeScript 转换为 JavaScript 代码：

```text
tsc app.ts
```

这时候在当前目录下（与 app.ts 同一目录）就会生成一个 app.js 文件，代码如下：

```javascript
var message = "Hello World";
console.log(message);
```

使用 node 命令来执行 app.js 文件：

```text
$ node app.js
Hello World
```

TypeScript 转换为 JavaScript 过程如下图：


## VS Code 介绍

很多 IDE 都有支持 TypeScript 插件，如：VS Code，Sublime Text 2，WebStorm / PHPStorm，Eclipse 等。

本章节主要介绍 VS Code，VS Code 是一个可以运行于 Mac OS X、Windows 和 Linux 之上的，针对于编写现代 Web 和云应用的跨平台源代码编辑器，由 Microsoft 公司开发。

VS Code 教程：https://www.runoob.com/vscode/vscode-tutorial.html

另外国内阿里与字节也有基于 VS Code 开发的 AI IDE：

- 阿里 Qoder：https://qoder.com/
- 字节 Trae：https://www.trae.cn/


### Windows 上安装 Visual Studio Code

1、下载 Visual Studio Code。

2、双击 VSCodeSetup.exe 图标 安装。

3、安装完成后，打开 Visual Studio Code 界面类似如下：

4、 我们可以在左侧窗口中点击当前编辑的代码文件，选择 open in command prompt（在终端中打开），这时候我们就可以在屏幕的右侧下半部分使用 tsc 命令来执行 TypeScript 文件代码了。


### Mac OS X 安装 Visual Studio Code

Mac OS X 安装配置 Visual Studio Code 可以查看： https://code.visualstudio.com/Docs/editor/setup


### Linux 安装 Visual Studio Code

Linux 安装配置 Visual Studio Code 可以查看： https://code.visualstudio.com/Docs/editor/setup


## 复习重点

- 能说明 `TypeScript 安装` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
