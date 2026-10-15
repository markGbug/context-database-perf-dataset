# Electron：Vue + Electron 实战项目

- 来源：[Vue + Electron 实战项目](https://www.runoob.com/electron/vue-electron.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：练习笔记
- 章节序号：0842

## 本章内容

本章节我们将使用 Vue + Electron 制作一个笔记应用，这个实战项目名为 VueElectronNotes，功能涵盖多窗口、托盘、文件操作和 IPC 通信，是初学者练手非常合适的项目。

如果你还不了解 Vue，可以先参考：Vue 教程。


## 一、项目功能

- 桌面笔记应用（Notes）
- 主窗口显示笔记列表
- 新建笔记弹出子窗口
- 系统托盘图标，最小化到托盘
- 文件本地保存/读取
- 渲染进程与主进程安全通信


## 二、项目初始化


### 1. 创建 Vue 项目

```text
vue create VueElectronNotes
cd VueElectronNotes
```

选择默认 preset（Babel + ESLint）。


### 2. 安装 Electron 及依赖

```text
npm install --save-dev electron electron-builder concurrently wait-on
npm install electron-store
```

- electron-store 用于本地数据持久化


## 三、主进程配置


### electron-main.js：


## 实例

说明：

- mainWindow：主窗口，显示笔记列表
- noteWindow：子窗口，用于新建笔记
- Tray：系统托盘图标与菜单
- ipcMain：主进程接收渲染进程消息


## 四、渲染进程与 Vue


### preload.js：


## 实例


### src/App.vue：


## 实例


### note.html + note.js：

note.html:


## 实例

note.js:


## 实例

说明：

- note.html 是弹出窗口，用于输入笔记
- note.js 调用 electronAPI.saveNote 发送到主进程
- 主窗口会接收到 update-notes 消息更新列表


## 五、运行项目


### 开发模式：

```text
npm run electron:serve
```

- Vue Dev Server + Electron 同时启动
- 可实时调试 UI


### 打包应用：

```text
npm run electron:build
```

- 输出可执行文件到 dist_electron
- 支持 Windows/macOS/Linux


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Vue + Electron 实战项目` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
