# Electron：Electron 安全性

- 来源：[Electron 安全性](https://www.runoob.com/electron/electron-security.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：练习笔记
- 章节序号：0834

## 本章内容

Electron 结合了 Node.js 与浏览器环境，这让桌面应用功能非常强大，但也带来一定的安全风险。 正确的安全策略可以降低 XSS、远程代码执行（RCE）和数据泄露的风险。


## 安全检查清单与常见隐患


### 安全检查清单

- 启用 上下文隔离（contextIsolation）
- 使用 预加载脚本（preload.js）暴露安全 API
- 不在渲染进程中直接使用 Node.js 模块
- 启用 沙箱模式（sandbox: true）
- 配置 内容安全策略（CSP）
- 安全使用 IPC，验证来源和输入
- 限制应用访问系统权限，遵循最小权限原则
- 避免加载不可信的远程内容


### 常见安全隐患

- 远程内容注入：加载未知 URL 或 HTML 文件可能执行恶意 JS
- 不安全的 IPC 调用：渲染进程可调用任意主进程方法
- Node.js 任意执行：在渲染进程启用 nodeIntegration 可被利用执行系统命令
- XSS 攻击：用户输入直接渲染到页面
- 依赖漏洞：使用未更新的第三方库


## 上下文隔离（Context Isolation）


### contextIsolation 详解

上下文隔离允许渲染进程和主进程在不同的 JS 环境中运行。 渲染进程的网页 JS 无法直接访问 Node.js API，而是通过安全的预加载脚本暴露接口。

```javascript
const mainWindow = new BrowserWindow({
  webPreferences: {
    contextIsolation: true,  // 启用上下文隔离
    preload: path.join(__dirname, 'preload.js'),
    nodeIntegration: false   // 禁止在渲染进程使用 Node.js
  }
})
```


### 为什么需要上下文隔离

- 防止加载的网页或第三方脚本直接访问 Node.js
- 避免攻击者通过 XSS 获取系统权限
- 保持渲染进程只处理 UI，主进程处理系统操作


### 迁移到隔离上下文

- 使用 contextBridge.exposeInMainWorld 暴露安全 API
- 所有系统操作放到主进程，通过 IPC 调用

示例：

```javascript
// preload.js
const { contextBridge, ipcRenderer } = require('electron')

contextBridge.exposeInMainWorld('api', {
  getData: () => ipcRenderer.invoke('get-data')
})
```

渲染进程只调用 window.api.getData()，无法直接操作系统。


## 沙箱模式（Sandbox）


### 启用沙箱

沙箱模式让渲染进程像浏览器普通网页一样运行，完全隔离 Node.js 环境。

```javascript
const mainWindow = new BrowserWindow({
  webPreferences: {
    sandbox: true,
    contextIsolation: true,
    preload: path.join(__dirname, 'preload.js')
  }
})
```


### 沙箱限制与应对

- 限制：渲染进程无法直接访问 Node.js 模块
- 应对方法：通过 IPC 调用主进程提供的安全方法
- 优势：增强安全性，防止恶意脚本破坏系统


## 内容安全策略（CSP）

CSP 可以防止 XSS 和数据注入攻击，通过限制网页可加载的资源来源。


### CSP 配置示例

```html
<meta http-equiv="Content-Security-Policy" content="
  default-src 'self';
  script-src 'self';
  style-src 'self' 'unsafe-inline';
  img-src 'self' data:;
  connect-src 'self' https://api.example.com;">
```

说明：

- default-src 'self'：默认只允许同源资源
- script-src 'self'：只允许本地脚本
- style-src 'self' 'unsafe-inline'：允许内联样式
- connect-src：限制 AJAX / WebSocket 请求域


### 防止 XSS 攻击

- 永远不要在渲染进程直接使用 innerHTML 显示用户输入
- 对用户输入进行转义或使用框架模板渲染


## 安全的 IPC 通信


### 验证消息来源

主进程应区分渲染进程来源，避免任意执行。

示例：

```text
ipcMain.handle('do-action', (event, data) => {
  if (event.senderFrame.url.startsWith('file://')) {
    // 安全来源，执行操作
  } else {
    console.warn('不安全的 IPC 请求被阻止')
  }
})
```


### 输入验证

- 所有通过 IPC 传入的数据都应验证类型和范围
- 避免注入恶意命令或文件路径

```javascript
function validateInput(data) {
  if (typeof data !== 'string' || data.length > 100) throw new Error('非法输入')
  return data
}
```


### 最小权限原则

- 仅暴露必要功能给渲染进程
- 不要把全部 Node.js API 或系统权限暴露出去
- 使用预加载脚本控制接口访问范围


## 小结

Electron 安全最佳实践核心是 隔离 + 验证 + 限权：

- 隔离：启用上下文隔离、沙箱模式
- 验证：CSP、防 XSS、IPC 输入验证
- 限权：最小化渲染进程权限，只提供必要 API

遵循这些原则，可以大幅降低桌面应用被攻击或数据泄露的风险。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Electron 安全性` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
