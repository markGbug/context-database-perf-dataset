# Electron：Electron 核心概念

- 来源：[Electron 核心概念](https://www.runoob.com/electron/electron-core-concepts.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：学习笔记
- 章节序号：0829

## 本章内容

Electron 的本质是一个多进程桌面应用框架，它结合了 Chromium（渲染层） 和 Node.js（系统层），通过独立的进程模型实现界面显示、逻辑控制和安全通信。

下面是 Electron 核心架构，展示了主进程、渲染进程、IPC 通信、以及 Preload 的关系。

主进程（A）：

- 运行 Node.js，控制窗口与系统交互。
- 使用 BrowserWindow 创建渲染进程。

渲染进程（B）：

- 每个窗口独立运行 HTML/CSS/JS，用于展示界面。

预加载脚本（B2）：

- 运在渲染进程加载前执行，连接主进程与网页层。
- 通过 contextBridge 安全地暴露 API。

IPC 通信（虚线箭头）：

- 主进程和渲染进程通过 ipcMain、ipcRenderer 双向通信。

操作系统（C）：

- 主进程可访问系统功能，例如文件、托盘、通知等。


## 主进程（Main Process）

主进程是 Electron 应用的"指挥中心"，运行在 Node.js 环境中。 它负责创建窗口、管理应用生命周期、调用系统 API，以及与渲染进程通信。 整个应用启动后，系统会首先运行主进程脚本（通常是 main.js）。

- 启动与退出应用
- 创建和销毁 BrowserWindow（窗口）
- 注册菜单、托盘、全局快捷键
- 调用操作系统功能（文件系统、通知、对话框）
- 监听渲染进程发送的事件

主进程的生命周期与应用生命周期一致，从 app 模块开始：


## 实例

- app.whenReady()：Electron 初始化完成后触发。
- window-all-closed：所有窗口关闭时触发。
- app.quit()：退出整个应用。
- macOS 上常见特例：用户关闭所有窗口时，程序仍保持后台运行。

app 模块用于控制整个应用生命周期：

- app.on('ready')：当 Electron 初始化完毕时触发。
- app.quit()：退出应用。
- app.getPath('userData')：获取系统路径。
- app.setAppUserModelId(id)：设置 Windows 的任务栏 ID。
- app.isPackaged：判断当前是否为打包状态。

主进程通过 BrowserWindow 创建可视化窗口：


## 实例

- width, height：窗口尺寸
- resizable：是否可调整大小
- webPreferences：用于配置渲染进程行为 preload：预加载脚本 nodeIntegration：是否允许渲染进程使用 Node.js

Electron 提供多个模块访问系统功能：

- Menu / MenuItem：自定义菜单栏
- Tray：创建系统托盘图标
- Dialog：调用系统文件选择、警告框
- Notification：原生通知
- shell：打开外部链接或文件，例如：const { dialog } = require('electron'); dialog.showOpenDialog({ properties: ['openFile', 'multiSelections'] });


## 渲染进程（Renderer Process）

渲染进程负责显示界面，运行在 Chromium 环境中。 每个 BrowserWindow 都有一个独立的渲染进程。

- 基于 Chromium，运行 HTML/CSS/JS
- 默认 无法直接访问 Node.js API（出于安全考虑）
- 可使用 Web 技术栈：Vue、React、Svelte 等
- 每个窗口对应独立线程，互不影响

Electron 的每个窗口（BrowserWindow）会启动一个独立渲染进程： 关闭一个窗口不会影响其他窗口，类似浏览器的多标签页模型。 这使得应用在崩溃恢复时更安全、可靠。

渲染进程的内容由主进程加载：

```text
win.loadFile('index.html');    // 加载本地页面
// 或者
win.loadURL('https://example.com'); // 加载远程网页
```

- 出于安全原因，不能直接使用 Node.js 模块（如 fs、path）。
- 不建议在渲染进程执行高负载计算（会卡 UI）。
- 与系统交互需通过 IPC 通信或 preload 暴露 API。


## 进程间通信（IPC）

Electron 的核心机制之一是 主进程与渲染进程之间的通信，称为 IPC（Inter-Process Communication）。

- ipcMain：在主进程中使用，接收消息。
- ipcRenderer：在渲染进程中使用，发送消息。

单向通信示例：


## 实例

双向通信示例（主进程回传数据）：

```text
ipcMain.on('getVersion', (event) => {
  event.reply('getVersionResponse', app.getVersion());
});
```

渲染端接收：

```javascript
ipcRenderer.on('getVersionResponse', (event, version) => {
  console.log(version);
});
```

Electron 提供了更简洁的异步请求方式：

主进程：

```text
ipcMain.handle('get-app-path', () => app.getPath('userData'));
```

渲染进程：

```javascript
const result = await ipcRenderer.invoke('get-app-path');
console.log(result);
```

这种方式类似 fetch 请求，避免多层回调。

- 使用 明确的通道名（如 "user:getData"）。
- 避免传递复杂对象（建议 JSON）。
- 对来自渲染进程的数据要验证来源与类型。
- 尽量通过 invoke/handle 实现结构化通信。


## 预加载脚本（Preload Scripts）

预加载脚本运行在渲染进程创建前，介于主进程与网页之间。 作用是安全地把 Node.js 功能"桥接"给渲染页面。

- 可访问 Node.js API（因为在隔离上下文）
- 可安全暴露少量 API 给渲染页面
- 常用于文件读写、系统路径获取、应用信息传递等

```javascript
// preload.js
const { contextBridge, ipcRenderer } = require('electron');

contextBridge.exposeInMainWorld('electronAPI', {
  getAppVersion: () => ipcRenderer.invoke('getVersion')
});
```

渲染进程使用：

```html
// index.html
<script>
  window.electronAPI.getAppVersion().then(v => {
    console.log('App version:', v);
  });
</script>
```

contextBridge 是 Electron 提供的安全 API，用于：

- 只暴露需要的函数（白名单机制）
- 防止恶意网页访问 Node.js 环境
- 在 contextIsolation: true 模式下仍可安全通信

如果启用了沙箱（sandbox: true），渲染进程完全无法使用 Node.js。 此时 preload 是唯一桥梁，负责：

- 接收渲染端调用
- 通过 IPC 转发到主进程
- 返回结果给网页端


## 总结

一句话理解： 主进程像"总控室"，渲染进程像"每个窗口的工作人员"， IPC 是"对讲机"，Preload 是"过滤后的安全通道"。


## 复习重点

- 能说明 `Electron 核心概念` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
