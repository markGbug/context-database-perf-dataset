# Electron：React + Electron 实战项目

- 来源：[React + Electron 实战项目](https://www.runoob.com/electron/react-electron.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：练习笔记
- 章节序号：0843

## 本章内容

本章节我们将使用 React + Electron 制作一个笔记应用，这个实战项目名为 ReactElectronNotes，功能涵盖多窗口、托盘、文件操作和 IPC 通信，是初学者练手非常合适的项目。

如果你还不了解 React，可以先参考：React 教程。

ReactElectronNotes 项目将教你从零开始构建一个 跨平台桌面笔记应用，包含以下特性：

- React 前端渲染
- Electron 主进程管理
- IPC 通信（主进程 ↔ 渲染进程）
- 笔记数据本地持久化（electron-store）
- 系统托盘与菜单集成


### 项目结构说明

```text
ReactElectronNotes/
│
├── src/                  # React 源码目录
├── build/                # 打包后的 React 静态文件
├── electron-main.js      # Electron 主进程
├── preload.js            # 渲染与主进程通信桥
├── note.html             # 子窗口页面
├── note.js               # 子窗口脚本
├── package.json
└── assets/
    └── icon.png          # 托盘图标
```


## 一、项目功能概述


## 二、项目初始化


### 1. 创建 React 项目

```text
npx create-react-app ReactElectronNotes
cd ReactElectronNotes
```


### 2. 安装 Electron 及依赖

```text
npm install --save-dev electron electron-builder concurrently wait-on
npm install electron-store
```


### 3. 修改 package.json

确保在 scripts 中添加 Electron 启动命令：

```text
"main": "electron-main.js",
"scripts": {
  "react-start": "react-scripts start",
  "react-build": "react-scripts build",
  "electron-start": "concurrently \"npm run react-start\" \"wait-on http://localhost:3000 && electron .\"",
  "electron-build": "react-scripts build && electron-builder"
}
```


## 三、创建 Electron 主进程

新建文件 electron-main.js：


## 实例


## 四、创建 Preload 脚本

新建 preload.js：


## 实例

说明： 通过 contextBridge 安全地暴露 API 给渲染进程。


## 五、React 前端界面


### src/App.js


## 实例


### 新建 note.html 与 note.js


## 实例


## 实例


## 六、运行与打包


### 启动开发环境

```text
npm run electron-start
```

打开后会出现 React 主窗口，可点击"新建笔记"弹出输入窗口。


### 打包发布

```text
npm run electron-build
```

会生成跨平台的可执行文件（.exe、.app、.AppImage 等）。


## 七、扩展方向


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `React + Electron 实战项目` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
