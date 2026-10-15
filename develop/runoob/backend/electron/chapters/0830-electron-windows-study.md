# Electron：Electron 创建和管理窗口

- 来源：[Electron 创建和管理窗口](https://www.runoob.com/electron/electron-windows.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：学习笔记
- 章节序号：0830

## 本章内容

在 Electron 中，窗口（Window）是应用与用户交互的核心载体。

所有可视界面都运行在 渲染进程（Renderer Process） 中，而这些窗口的创建与控制则由 主进程（Main Process） 负责。


## 创建和管理窗口

Electron 通过 BrowserWindow 类来创建窗口。

主进程中通过以下方式定义一个新窗口：


## 实例

BrowserWindow 配置选项

- width / height：窗口宽高。
- minWidth / minHeight：最小尺寸限制。
- resizable：是否允许调整大小。
- fullscreen / fullscreenable：是否全屏。
- frame：是否显示原生标题栏（常用于自定义标题栏时关闭）。
- transparent：透明窗口（可实现毛玻璃、浮动等效果）。
- alwaysOnTop：窗口是否总在最前。

窗口尺寸、位置与状态 可以通过 API 控制窗口状态：

```text
mainWindow.maximize()   // 最大化
mainWindow.minimize()   // 最小化
mainWindow.restore()    // 还原
mainWindow.setBounds({ x: 100, y: 100, width: 800, height: 600 }) // 调整位置和大小
```

还可监听窗口变化：

```javascript
mainWindow.on('resize', () => console.log('窗口尺寸变化'))
mainWindow.on('move', () => console.log('窗口移动'))
```

无边框窗口与自定义标题栏 设置 frame: false 后，可以自定义标题栏区域，并通过 CSS 与 JS 模拟拖拽：

```text
.titlebar {
  -webkit-app-region: drag;
}
```

需要注意非拖拽区域（如按钮）应加上：

```text
.titlebar {
  -webkit-app-region: drag;
}
```

窗口事件监听

```text
mainWindow.on('close', (e) => {
  e.preventDefault()
  mainWindow.hide()
})
```

常用事件包括：

- ready-to-show：页面加载完成，可安全显示。
- focus / blur：窗口获得或失去焦点。
- closed：窗口已被销毁。


## 加载页面内容

Electron 窗口可以加载本地 HTML 文件或远程网站。

加载本地 HTML 文件

```text
mainWindow.loadFile('index.html')
```

加载远程 URL

```text
mainWindow.loadURL('https://example.com')
```

使用前端框架 如果你使用 Vue、React 或 Angular 等现代框架，可以将构建后的静态文件加载到窗口：

```text
mainWindow.loadFile(path.join(__dirname, 'dist/index.html'))
```

或者在开发模式下加载本地服务：

```text
mainWindow.loadURL('http://localhost:5173')
```


## 窗口间通信

在多窗口应用中，可能需要在窗口间传递数据或控制行为。

父子窗口关系 可以在创建新窗口时指定 parent：

```javascript
let child = new BrowserWindow({
  parent: mainWindow,
  modal: true, // 模态窗口
  width: 400,
  height: 300,
})
```

父窗口关闭时，子窗口也会自动关闭。

多窗口数据共享 可以通过主进程作为中介，在不同渲染进程之间传递数据，也可使用全局对象或 ipcMain / ipcRenderer。

窗口消息传递 主进程可直接操作目标窗口：

```text
child.webContents.send('update-data', someData)
```

在子窗口中接收：

```javascript
const { ipcRenderer } = require('electron')
ipcRenderer.on('update-data', (event, data) => {
  console.log(data)
})
```


## 界面优化

启动画面（Splash Screen） 在主窗口加载较慢时，可先显示一个轻量级启动窗口：

```javascript
const splash = new BrowserWindow({ width: 400, height: 300, frame: false })
splash.loadFile('splash.html')

mainWindow.once('ready-to-show', () => {
  splash.close()
  mainWindow.show()
})
```

窗口显示优化 为防止白屏闪烁，常用技巧包括：

- 使用 show: false 创建窗口，待加载完再 show()。
- 在渲染页面中设置背景色。
- 预加载资源（图标、字体、样式）。

防止闪烁的技巧

- 开启 GPU 加速或禁用硬件加速（视具体情况）。
- 在 CSS 中避免复杂动画或渐变。
- 使用双缓冲渲染，减少绘制抖动。


## 多窗口 Electron 应用（含启动页、主界面与子窗口）

目录结构

```text
my-electron-app/
├── package.json
├── main.js             # 主进程入口
├── preload.js          # 预加载脚本
├── splash.html         # 启动画面
├── index.html          # 主窗口页面
├── child.html          # 子窗口页面
└── renderer.js         # 渲染进程逻辑
```

main.js（主进程）


## 实例

index.html（主窗口）


## 实例

child.html（子窗口）


## 实例

splash.html（启动画面）


## 实例

renderer.js（渲染逻辑）


## 实例

运行后流程如下：

- 启动时显示 启动画面（splash.html）。
- 加载完成后自动关闭启动页，展示 主窗口。
- 主窗口可通过按钮打开 子窗口，展示 IPC 通信功能。
- 主窗口使用了 Preload 安全暴露 API，防止直接访问 Node.js。
- 所有窗口都使用了 事件监听、延迟显示 等优化策略，避免白屏与闪烁。


## 复习重点

- 能说明 `Electron 创建和管理窗口` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
