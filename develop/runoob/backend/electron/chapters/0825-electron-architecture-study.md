# Electron：Electron 架构

- 来源：[Electron 架构](https://www.runoob.com/electron/electron-architecture.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：学习笔记
- 章节序号：0825

## 本章内容

可以把 Electron 看成是：

一个多进程的应用容器，内置了一个浏览器引擎 (Chromium) 和一个 Node.js 运行时， 通过进程间通信（IPC）协同运行，实现"网页 + 系统能力"的桌面应用。

它的核心组成是：


### 主进程 (Main Process)

主进程是 Electron 应用的"大脑"，每个 Electron 应用有且只有一个主进程。它负责：

- 创建和管理应用窗口（渲染进程）
- 处理应用程序生命周期（启动、退出、前后台切换）
- 与操作系统原生 API 交互
- 管理菜单、对话框等系统级组件


## 实例


### 渲染进程 (Renderer Process)

渲染进程负责显示用户界面，每个 Electron 窗口都是一个独立的渲染进程：

- 运行在 Chromium 浏览器环境中
- 使用 HTML、CSS、JavaScript 构建界面
- 每个窗口都是独立的进程，互不影响
- 通过 IPC 与主进程通信


## 实例


### 预加载脚本 (Preload Scripts)

预加载脚本是连接主进程和渲染进程的"桥梁"：

- 在渲染进程加载网页之前运行
- 有权访问 Node.js API 和 DOM
- 通过 contextBridge 安全地暴露 API 给渲染进程


## 实例


## 进程间通信 (IPC)


### IPC 通信模式

IPC（Inter-Process Communication） 是 Electron 的通信核心。

由于主进程与渲染进程是独立的，所以必须通过 IPC 传递数据。


### 通信方向


### 基本通信示例

主进程代码：


## 实例

渲染进程代码：


## 实例


## 架构优势与特点


### 优势对比


### 核心特点

- 跨平台一致性：应用在所有操作系统上外观和行为一致
- Web 生态利用：可以直接使用 npm 包和 Web 框架
- 快速原型开发：基于熟悉的 Web 技术，开发周期短
- 丰富的 API：提供访问系统原生功能的完整 API 集


## 实际应用示例

让我们创建一个简单的文件管理器应用来演示 Electron 架构：

主进程 (main.js)：


## 实例

预加载脚本 (preload.js)：


## 实例

渲染进程 (index.html)：


## 实例


## 其他重要模块（主进程可用）


## 安全架构与沙箱隔离

由于渲染进程能运行网页，为防止恶意代码攻击系统，Electron 推行以下安全设计：


## 运行流程（从启动到渲染）

```text
1、启动应用 (electron .)
     ↓
2、执行 main.js（主进程启动）
     ↓
3、app.whenReady() 触发，创建 BrowserWindow
     ↓
4、BrowserWindow 启动新的渲染进程（Chromium 实例）
     ↓
5、preload.js 先执行（在隔离上下文中）
     ↓
6、index.html 加载并显示（运行前端框架）
     ↓
7、渲染进程通过 IPC 调用主进程逻辑
     ↓
8、主进程处理请求、返回结果
     ↓
9、用户关闭窗口 → 主进程监听 → app.quit()
```


## 主从多窗口模型（多进程并行）

- 一个 Electron 应用始终只有 一个主进程；
- 但可以有 多个渲染进程（每个窗口独立）；
- 它们之间通信要通过主进程中转或使用 ipcMain.handle 进行异步桥接。

示意：

```text
主进程 (Main)
 ├── 窗口1 → 渲染进程A (index.html)
 ├── 窗口2 → 渲染进程B (settings.html)
 └── 窗口3 → 渲染进程C (dashboard.html)
```


## Electron 内部核心组件（底层依赖）

你写的 JS 代码跑在 Electron 封装的 Node 环境里，而渲染界面跑在 Chromium WebView 里。


## 复习重点

- 能说明 `Electron 架构` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
