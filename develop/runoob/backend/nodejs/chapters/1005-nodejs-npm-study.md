# Node.js：NPM 使用介绍

- 来源：[NPM 使用介绍](https://www.runoob.com/nodejs/nodejs-npm.html)
- 分类：后端开发
- 技术：Node.js
- 笔记类型：学习笔记
- 章节序号：1005

## 本章内容

NPM（Node Package Manager）是一个 JavaScript 包管理工具，也是 Node.js 的默认包管理器。

NPM 允许开发者轻松地下载、安装、共享、管理项目的依赖库和工具。

NPM 是 Node.js 自带的包管理工具，因此，通常你只需安装 Node.js，NPM 就会自动安装在系统中。

主要功能：

- 包管理：NPM 可以帮助你安装并管理项目所需的各种第三方库（包）。例如，可以通过简单的命令来安装、更新、或删除依赖。
- 版本管理：NPM 支持版本控制，允许你锁定某个特定版本的依赖，或根据需求选择最新的版本。
- 包发布：NPM 允许开发者将自己的库发布到 NPM 仓库中，其他开发者可以通过 NPM 下载并使用这些库。
- 命令行工具：NPM 提供了强大的命令行工具，可以用于安装包、运行脚本、初始化项目等多种操作。

由于新版的 Node.js 已经集成了 NPM，所以我们可以直接通过输入 npm -v 来测试是否成功安装，出现版本提示表示安装成功:

```text
$ npm -v
2.3.0
```

如果你安装的是旧版本的 npm，可以很容易得通过 npm 命令来升级，命令如下：

```text
$ sudo npm install npm -g
/usr/local/bin/npm -> /usr/local/lib/node_modules/npm/bin/npm-cli.js
npm@2.14.2 /usr/local/lib/node_modules/npm
```

如果是 Window 系统使用以下命令即可：

```text
npm install npm -g
```


## 使用 npm 命令安装模块

npm 安装 Node.js 模块语法格式如下：

```html
$ npm install <Module Name>
```

以下实例，我们使用 npm 命令安装常用的 Node.js web框架模块 express:

```text
$ npm install express
```

安装好之后，express 包就放在了工程目录下的 node_modules 目录中，因此在代码中只需要通过 require('express') 的方式就好，无需指定第三方包路径。

```javascript
var express = require('express');
```


## 全局安装与本地安装

npm 的包安装分为本地安装（local）、全局安装（global）两种，从敲的命令行来看，差别只是有没有 -g 参数。

本地安装：将包安装到 node_modules 目录，并将信息保存到 package.json 的 dependencies 中。

```text
npm install express          # 本地安装
```

全局安装：用于安装命令行工具或需要在多个项目中使用的包。

```text
npm install express -g   # 全局安装
```

如果出现以下错误：

```text
npm err! Error: connect ECONNREFUSED 127.0.0.1:8087
```

解决办法为：

```text
$ npm config set proxy null
```


### 本地安装

- 作用范围：默认情况下，npm 会将包安装在当前项目的 node_modules 文件夹中。这意味着每个使用该包的项目都会有自己的包副本。
- 用途：本地安装通常用于项目依赖。每个项目可以有自己的依赖版本，这有助于确保项目的稳定性和可复现性。
- 安装命令：在项目目录中运行 npm install <package-name> 会将包安装在 node_modules 文件夹中，并在 package.json 文件中添加依赖项。
- 版本管理：通过 package.json 和 package-lock.json 文件管理依赖的版本，确保项目在不同环境中的一致性。


### 全局安装

- 作用范围：全局安装会将包安装在系统级别的目录中，通常是 /usr/local/bin（在 Unix-like 系统上）或 %AppData%\npm（在 Windows 上）。
- 用途：全局安装用于那些不需要在每个项目中重复安装的工具或命令行实用程序。例如，安装一个全局的 create-react-app 可以用于创建新的 React 项目。
- 安装命令：使用 -g 标志来全局安装包，例如 npm install -g <package-name>。
- 版本管理：全局安装的包版本由 npm 管理，但不会在项目的 package.json 中体现。这意味着全局安装的包可能在不同项目之间共享，但也可能因为版本冲突而导致问题。

如果你希望具备两者功能，则需要在两个地方安装它或使用 npm link。

接下来我们使用全局方式安装 express

```text
$ npm install express -g
```

安装过程输出如下内容，第一行输出了模块的版本号及安装位置。

```text
express@4.13.3 node_modules/express
├── escape-html@1.0.2
├── range-parser@1.0.2
├── merge-descriptors@1.0.0
├── array-flatten@1.1.1
├── cookie@0.1.3
├── utils-merge@1.0.0
├── parseurl@1.3.0
├── cookie-signature@1.0.6
├── methods@1.1.1
├── fresh@0.3.0
├── vary@1.0.1
├── path-to-regexp@0.1.7
├── content-type@1.0.1
├── etag@1.7.0
├── serve-static@1.10.0
├── content-disposition@0.5.0
├── depd@1.0.1
├── qs@4.0.0
├── finalhandler@0.4.0 (unpipe@1.0.0)
├── on-finished@2.3.0 (ee-first@1.1.1)
├── proxy-addr@1.0.8 (forwarded@0.1.0, ipaddr.js@1.0.1)
├── debug@2.2.0 (ms@0.7.1)
├── type-is@1.6.8 (media-typer@0.3.0, mime-types@2.1.6)
├── accepts@1.2.12 (negotiator@0.5.3, mime-types@2.1.6)
└── send@0.13.0 (destroy@1.0.3, statuses@1.2.1, ms@0.7.1, mime@1.3.4, http-errors@1.3.1)
```


### 查看安装信息

你可以使用以下命令来查看所有全局安装的模块：

```text
$ npm list -g

├─┬ cnpm@4.3.2
│ ├── auto-correct@1.0.0
│ ├── bagpipe@0.3.5
│ ├── colors@1.1.2
│ ├─┬ commander@2.9.0
│ │ └── graceful-readlink@1.0.1
│ ├─┬ cross-spawn@0.2.9
│ │ └── lru-cache@2.7.3
……
```

如果要查看某个模块的版本号，可以使用命令如下：

```text
$ npm list grunt

projectName@projectVersion /path/to/project/folder
└── grunt@0.4.1
```


## 卸载模块

我们可以使用以下命令来卸载 Node.js 模块。

```text
$ npm uninstall express
```


## 复习重点

- 能说明 `NPM 使用介绍` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
