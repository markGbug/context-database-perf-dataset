# Electron：Electron 进阶主题

- 来源：[Electron 进阶主题](https://www.runoob.com/electron/electron-advanced.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：学习笔记
- 章节序号：0840

## 本章内容

Electron 不仅能构建跨平台桌面应用，还支持深度系统集成和进阶功能扩展。掌握这些进阶技巧，可以让应用更专业、功能更强大。


## Native Node 模块集成


### node-gyp 使用

- node-gyp 是 Node.js 原生模块编译工具，支持 C/C++ 模块编译
- 安装：npm install -g node-gyp
- 初始化项目：node-gyp configure node-gyp build
- 输出 .node 文件，可在 Electron 中直接加载：const native = require('./build/Release/native.node')


### 编译原生模块

- 原生模块必须针对 Electron 的 Node 版本和 ABI 编译
- 使用 electron-rebuild 工具：npm install --save-dev electron-rebuild npx electron-rebuild
- 确保模块与当前 Electron 版本兼容


### 常见问题解决

- ABI 不兼容：Electron 使用不同 Node 版本，需要 electron-rebuild
- 编译失败：检查 C++ 编译环境（Windows 需安装 Visual Studio Build Tools，macOS 需 Xcode Command Line Tools）
- 路径问题：确保模块路径正确，使用绝对路径加载 .node 文件


## 与系统深度集成


### 系统主题检测

- 检测暗黑/亮色主题：const { nativeTheme } = require('electron') console.log(nativeTheme.shouldUseDarkColors) nativeTheme.on('updated', () => { console.log('主题更新:', nativeTheme.shouldUseDarkColors) })
- 阻止系统休眠：const { powerSaveBlocker } = require('electron') const id = powerSaveBlocker.start('prevent-display-sleep') powerSaveBlocker.stop(id)
- 检测电源状态：const { systemPreferences } = require('electron') console.log(systemPreferences.getSystemIdleTime())


### 屏幕管理

- 获取屏幕信息：const { screen } = require('electron') const primaryDisplay = screen.getPrimaryDisplay() console.log(primaryDisplay.size)
- 多屏幕支持、分辨率检测和窗口自动适配


### 系统空闲检测

- 通过 systemPreferences.getSystemIdleTime() 获取用户空闲时间
- 可用于自动锁屏、节能或提醒功能


## 多语言支持


### i18n 实现方案

常用库：

- i18next：支持 JSON / YAML 语言包，动态切换
- vue-i18n / react-i18next：前端框架集成

文件结构：

```text
locales/
  en.json
  zh.json
```

语言切换：

```javascript
const i18next = require('i18next')
i18next.init({
  lng: 'en',
  resources: {
    en: { translation: require('./locales/en.json') },
    zh: { translation: require('./locales/zh.json') }
  }
})
console.log(i18next.t('hello')) // 输出 hello
```

可以动态修改 lng，实现实时切换语言。


### 动态加载语言包

- 对大型项目，语言包可按需加载：async function setLanguage(lang) { const resources = await import(`./locales/${lang}.json`) i18next.addResources(lang, 'translation', resources.default) i18next.changeLanguage(lang) }
- 优化包体积，减少启动加载时间


## 自定义协议

Electron 支持注册自定义协议，使应用可以通过特定的 URL scheme 调用内部功能或实现深度链接（Deep Linking）。


### 注册自定义协议

- 使用 protocol 模块注册自定义协议
- 可用于加载应用内部资源或响应特定 URL

```javascript
const { app, protocol } = require('electron')

app.whenReady().then(() => {
  protocol.registerFileProtocol('myapp', (request, callback) => {
    const url = request.url.substr(7) // 去掉 'myapp://'
    callback({ path: `${__dirname}/${url}` })
  })
})
```

说明：

- 'myapp'：自定义协议名称
- request.url：传入的完整 URL
- callback({ path })：指向本地文件路径，可用于加载 HTML、图片等


### 深度链接（Deep Linking）

- 深度链接允许用户通过 URL 直接打开应用特定页面或功能
- 注册系统协议：if (!app.isDefaultProtocolClient('myapp')) { app.setAsDefaultProtocolClient('myapp') }
- 在 macOS / Windows 中，点击 myapp://note/123 可触发应用事件
- 处理深度链接：app.on('open-url', (event, url) => { event.preventDefault() console.log('接收到深度链接:', url) // 可解析 URL 跳转到应用内部页面 })
- Windows 事件处理：app.on('second-instance', (event, argv) => { const url = argv.find(arg => arg.startsWith('myapp://')) if (url) { console.log('接收到深度链接:', url) } })


### 协议处理

- 安全性： 验证 URL 内容，防止执行未授权操作 避免加载恶意文件或执行任意命令
- 应用场景： 打开特定笔记、文档或页面 与 Web 页面交互，调用本地功能 跨应用或跨平台通信
- 注意事项： macOS 需在 Info.plist 配置 CFBundleURLTypes Windows 需在注册表中注册协议 协议处理逻辑建议放在主进程中，渲染进程只接收事件


## 复习重点

- 能说明 `Electron 进阶主题` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
