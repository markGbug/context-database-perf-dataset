# Electron：Electron 安装

- 来源：[Electron 安装](https://www.runoob.com/electron/electron-install.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：练习笔记
- 章节序号：0826

## 本章内容

在安装 Electron 之前，需要准备两个基础环境：


### 1、Node.js

Electron 是基于 Node.js 的框架，因此必须先安装 Node.js。

检查是否已安装：

```text
node -v
npm -v
```

如果输出版本号，说明已安装。 若没有，请前往 Node.js 官网 下载 LTS（长期支持版）。

安装完成后，系统会自动附带 npm（Node 包管理器）。

如果不熟悉 Node.js，可以参考： Node.js


### 2、npm 或 yarn

Electron 的安装依赖 npm 或 yarn 管理包。

可以选择：

```text
# 使用 npm
npm install electron --save-dev

# 或使用 yarn
yarn add electron --dev
```


## 安装 Electron

Electron 的安装方式有两种：全局安装 和 项目内安装。 推荐使用 项目内安装（更安全、更易维护）。


### 1、项目内安装

```text
# 创建一个项目文件夹
mkdir my-electron-app
cd my-electron-app

# 初始化 Node 项目
npm init -y

# 安装 Electron
npm install electron --save-dev
```

安装成功后，会在项目目录中出现：

```text
node_modules/
package.json
package-lock.json
```


## 验证是否安装成功

创建一个简单的 Electron 启动文件：

main.js


## 实例

index.html


## 实例

然后在 package.json 里添加启动命令：

```text
"scripts": {
  "start": "electron ."
}
```

运行：

```text
npm start
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Electron 安装` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
