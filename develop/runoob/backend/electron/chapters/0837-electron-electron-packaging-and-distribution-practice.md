# Electron：Electron 打包与分发

- 来源：[Electron 打包与分发](https://www.runoob.com/electron/electron-electron-packaging-and-distribution.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：练习笔记
- 章节序号：0837

## 本章内容

Electron 应用开发完成后，需要将应用打包为桌面可执行文件，并发布给用户。

打包与分发流程涉及工具选择、配置、签名和更新策略等多个环节。


## 打包工具介绍


### electron-builder

- 高度自动化，支持 Windows、macOS、Linux
- 支持自动更新功能
- 配置简单，适合生产环境
- 可生成 .exe、.dmg、.AppImage 等格式


### electron-packager

- 官方推荐打包工具，轻量
- 只负责生成可执行文件，不带自动更新
- 配置简单，但需要结合其他工具处理安装包和签名


### electron-forge

- 集成打包、模板、自动更新和发布流程
- 开箱即用，适合新手快速启动项目
- 内置 Webpack / ESBuild 构建支持


### 工具对比与选择


## 配置打包参数


### package.json 配置

```text
"build": {
  "appId": "com.example.myapp",
  "productName": "MyElectronApp",
  "directories": {
    "output": "dist"
  },
  "files": ["**/*"],
  "extraResources": ["assets/"],
  "mac": {
    "category": "public.app-category.utilities"
  },
  "win": {
    "target": "nsis",
    "icon": "build/icon.ico"
  },
  "linux": {
    "target": ["AppImage", "deb"],
    "icon": "build/icon.png"
  }
}
```


### 平台特定配置

- Windows：安装包类型（NSIS、Squirrel）、图标 .ico
- macOS：应用类别、签名、.icns 图标
- Linux：目标格式（AppImage、deb、rpm）、图标 PNG


### 图标和资源文件

- 图标尺寸和格式需满足平台要求
- 额外资源可通过 extraResources 或 extraFiles 添加


## 多平台打包


### Windows 打包

```text
electron-builder --win
```

- 可生成 .exe 或 .msi 安装文件
- 支持 NSIS 安装向导、静默安装


### macOS 打包

```text
electron-builder --mac
```

- 可生成 .dmg 或 .pkg
- 配合公证（Notarization）可通过 macOS Gatekeeper


### Linux 打包

```text
electron-builder --linux
```

- 常用格式：AppImage、deb、rpm
- 适合不同发行版的桌面分发


### 交叉编译

- Electron-builder 支持跨平台构建，但 macOS 应用必须在 macOS 上签名
- Windows / Linux 可通过 Linux 或 Windows 构建虚拟机实现交叉打包


## 代码签名


### Windows 代码签名

- 使用数字证书（.pfx）签名 .exe 或 .msi
- 示例：

```text
electron-builder --win --csc-link path/to/certificate.pfx --csc-key-password yourpassword
```

- 提升用户信任，避免 SmartScreen 阻拦


### macOS 公证（Notarization）

- Apple 官方要求应用公证通过 Gatekeeper
- 需要 Apple Developer 账号
- 构建示例：

```text
electron-builder --mac --publish never
```

- 使用 notarize API 上传应用进行自动公证


### 证书申请与管理

- Windows：购买 EV 或标准代码签名证书
- macOS：Apple Developer 账号申请开发者证书
- 证书需安全存储，避免泄露


## 自动更新


### electron-updater 使用

- 与 electron-builder 配合，支持差分更新
- 安装 electron-updater：npm install electron-updater

主进程示例：

```javascript
const { autoUpdater } = require('electron-updater')

autoUpdater.on('update-available', () => console.log('发现新版本'))
autoUpdater.on('update-downloaded', () => autoUpdater.quitAndInstall())
autoUpdater.checkForUpdates()
```


### 更新服务器搭建

- 可使用 GitHub Releases、私有服务器或 CDN
- 提供 JSON 文件描述最新版本信息


### 差分更新

- 仅下载变更文件，减少带宽消耗
- electron-updater 内置支持 NSIS / Squirrel / AppImage 差分更新


### 更新策略

- 自动检查更新（启动时或定时）
- 手动触发更新
- 弹窗提示用户是否立即更新或延迟更新


## 小结

Electron 打包与分发核心流程：

- 选择工具：electron-builder、electron-packager、electron-forge
- 配置参数：package.json 中定义平台、图标、资源
- 多平台打包：Windows、macOS、Linux
- 代码签名：确保应用可信，避免安全提示
- 自动更新：提升用户体验，支持差分更新

遵循最佳实践，可以让 Electron 应用快速安全地分发给用户，同时便于后续迭代和更新。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Electron 打包与分发` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
