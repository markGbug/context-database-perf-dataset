# Electron：Electron 入门实例

- 来源：[Electron 入门实例](https://www.runoob.com/electron/electron-start.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：学习笔记
- 章节序号：0827

## 本章内容

在上一章节我们已经学会了如何安装 Electron。

本章节我们将一步步介绍如何创建一个简单的 Electron 实例。


### 1、创建项目目录

打开终端，依次执行：

```text
mkdir my-electron-app
cd my-electron-app
npm init -y
npm install electron --save-dev
```

生成结构如下：

```text
my-electron-demo/
├─ package.json
├─ main.js
└─ index.html
```


### 2、配置 package.json

打开 package.json，修改成以下内容：

```text
{
  "name": "my-electron-app",
  "version": "1.0.0",
  "description": "RUNOOB Electron 测试",
  "main": "main.js",
  "scripts": {
    "start": "electron ."
  },
  "devDependencies": {
    "electron": "latest"
  }
}
```

说明：


### 3、编写主进程文件 main.js

这是 Electron 的核心控制中心，负责创建应用窗口和加载页面。

创建文件 main.js，输入以下完整代码（带详细注释）：


## 实例

说明：


### 4、编写渲染页面 index.html

创建 index.html 文件，输入以下内容：


## 实例


### 5、运行项目

回到终端，执行：

```text
npm start
```

运行后，你会看到一个桌面窗口，显示：

```text
Hello, Electron!
RUNOOB Electron 测试。这是你创建的第一个 Electron 桌面应用 🎉
```


## 复习重点

- 能说明 `Electron 入门实例` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
