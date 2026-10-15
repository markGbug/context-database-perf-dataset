# Node.js：pnpm 使用介绍

- 来源：[PNPM 使用介绍](https://www.runoob.com/nodejs/nodejs-pnpm.html)
- 分类：后端开发
- 技术：Node.js
- 笔记类型：练习笔记
- 章节序号：1006

## 本章内容

作为 Node.js 开发者，你一定听说过 npm 和 yarn，它们是管理项目依赖的利器。但你是否遇到过 node_modules 文件夹巨大无比、安装速度缓慢、或者磁盘空间被迅速占满的烦恼？这就是 pnpm 能解决的问题。

pnpm 是一个快速、节省磁盘空间的 Node.js 包管理器，它通过内容寻址的方式存储包，所有版本的依赖会集中存储在系统的一个位置，然后通过硬链接的方式链接到项目中，避免了重复安装。

pnpm 的 slogan 是 Fast, disk space efficient package manager（快速、节省磁盘空间的包管理器），它不仅速度飞快，更通过其独特的链接机制，为你节省大量的磁盘空间和带宽。


## 安装 pnpm

安装 pnpm 有多种方式，你可以根据喜好和系统环境选择。


### 方法一：使用 npm 安装（推荐给所有用户）

这是最通用、最简单的方法。打开你的终端（Windows 用户可使用 PowerShell 或 CMD），运行以下命令：

```text
npm install -g pnpm
```

这条命令会通过 npm 将 pnpm 安装到你的全局环境。

验证安装是否成功： 安装完成后，运行以下命令检查版本。如果能正常显示版本号，说明安装成功。

```text
pnpm --version
```

输出类似：8.15.0


### 方法二：使用独立脚本安装

对于 macOS 或 Linux 用户，可以使用以下脚本安装：

```text
# macOS/Linux
curl -fsSL https://get.pnpm.io/install.sh | sh -

# Windows (PowerShell)
iwr https://get.pnpm.io/install.ps1 -useb | iex
```


## pnpm 使用

学会了安装，现在让我们开始实际使用 pnpm。它的命令设计非常直观，如果你熟悉 npm，几乎可以无缝切换。


### 初始化一个新项目

类似于 npm init，pnpm 可以用来初始化项目并创建 package.json 文件。

```text
# 交互式地回答问题，创建 package.json
pnpm init

# 快速创建一个带有默认值的 package.json
pnpm init -y
```

运行 pnpm init -y 后，你会得到一个最基本的 package.json 文件：


## 实例


### 安装依赖包

pnpm 的安装命令是 pnpm add <package-name>，相当于 npm install <package-name>。

```html
# 安装所有依赖
pnpm install

# 添加依赖包
pnpm add <package-name>

# 添加开发依赖
pnpm add -D <package-name>

# 添加全局包
pnpm add -g <package-name>

# 安装指定版本
pnpm add <package-name>@<version>
```


### 更新依赖

```html
# 更新所有依赖
pnpm update

# 更新指定包
pnpm update <package-name>

# 更新到最新版本(忽略 package.json 中的版本范围)
pnpm update --latest
```


### 删除依赖

```html
pnpm remove <package-name>
```


### 运行脚本

```html
# 运行 package.json 中定义的脚本
pnpm run <script-name>
# 一些常见的简写
pnpm start
pnpm test
pnpm build
```


### npm 到 pnpm 命令对照表


## 配置文件

pnpm 支持通过 .npmrc 文件进行配置。

在项目根目录创建此文件可以自定义 pnpm 的行为。


### 常用配置示例

```text
# 设置国内镜像源(淘宝)
registry=https://registry.npmmirror.com

# 自动安装 peer dependencies
auto-install-peers=true

# 严格模式
strict-peer-dependencies=true

# shamefully-hoist(提升依赖,兼容某些工具)
shamefully-hoist=true

# 指定 node_modules 目录结构
node-linker=hoisted

# 设置存储目录
store-dir=~/.pnpm-store
```

查看当前配置

```text
pnpm config list
```

设置配置项:

```html
pnpm config set <key> <value>
```


## Workspace 工作区

pnpm 内置了强大的 monorepo 支持。

通过在项目根目录创建 pnpm-workspace.yaml 文件来定义工作区。

配置示例:

```html
packages:
  - 'packages/*'
  - 'apps/*'
<p>  - '!**/test/**'
```

```text
my-monorepo/
├── pnpm-workspace.yaml
├── package.json
├── packages/
│   ├── package-a/
│   │   └── package.json
│   └── package-b/
│       └── package.json
└── apps/
    └── web-app/
        └── package.json
```


### 工作区命令

```html
# 在所有工作区包中安装依赖
pnpm install

# 在指定工作区执行命令
pnpm --filter <package-name> <command>

# 在所有工作区执行命令
pnpm -r <command>

# 递归运行脚本
pnpm -r run build

# 为工作区添加依赖
pnpm --filter <package-name> add <dependency>

# 添加工作区内部依赖
pnpm --filter package-a add package-b@workspace:*
```


### 工作区协议

在工作区内引用其他包时, 使用 workspace: 协议:

```text
json{
  "dependencies": {
    "package-a": "workspace:*",
    "package-b": "workspace:^1.0.0"
  }
}
```


## 高级特性


### pnpm exec 与 pnpm dlx

```html
# 执行本地安装的包
pnpm exec <command>

# 执行远程包(类似 npx)
pnpm dlx create-react-app my-app

# 使用特定版本
pnpm dlx create-react-app@latest my-app
```


### 查看依赖树

```text
# 查看依赖树
pnpm list

# 指定深度
pnpm list --depth 2

# 只显示生产依赖
pnpm list --prod

# 查看全局包
pnpm list -g
```


### 查看过期依赖

```text
pnpm outdated
```


### 审计依赖安全性

```text
pnpm audit

# 自动修复安全问题
pnpm audit --fix
```


### 清理缓存

```text
# 清理未使用的包
pnpm store prune

# 查看存储位置
pnpm store path

# 查看存储状态
pnpm store status
```


### 导入 lockfile

从其他包管理器迁移时:

```text
# 从 package-lock.json 导入
pnpm import

# 从 yarn.lock 导入
pnpm import
```


### Patch 包

当需要临时修改某个依赖包时:

```html
# 创建补丁
pnpm patch <package-name>@<version>

# 应用补丁后提交
pnpm patch-commit <path>
```


## 后续章节

- pnpm 是什么？核心优势何在？
- 传统包管理器的问题
- pnpm 的革命性方案：内容可寻址存储与硬链接

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PNPM 使用介绍` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
