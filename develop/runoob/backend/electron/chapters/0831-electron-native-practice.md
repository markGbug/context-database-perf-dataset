# Electron：Electron 原生功能集成

- 来源：[Electron 原生功能集成](https://www.runoob.com/electron/electron-native.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：练习笔记
- 章节序号：0831

## 本章内容

Electron 之所以强大，是因为它不仅能写前端，还能访问系统的原生功能，比如菜单、对话框、托盘、通知和全局快捷键等。

本章节我们来看看如何通过主进程模块调用这些功能。


## 菜单系统

Electron 提供 Menu 模块用于创建菜单栏、上下文菜单和系统托盘菜单。


### 应用菜单（Menu）

应用菜单是显示在窗口顶部（macOS）或应用窗口中的菜单栏。


## 实例

说明：

- label：菜单标题。
- submenu：子菜单数组。
- accelerator：快捷键（macOS、Windows 通用写法 CmdOrCtrl+X）。
- role：系统预定义行为，如 quit、copy、paste。
- click：点击事件回调函数。


### 上下文菜单（Context Menu）

右键菜单通常在渲染进程中触发：


## 实例


## 实例


### 系统托盘菜单

在系统通知区域显示图标与菜单。


## 实例


### 菜单快捷键

通过 accelerator 定义。例如：

```text
{ label: '保存', accelerator: 'CmdOrCtrl+S', click: saveFile }
```

- CmdOrCtrl：自动适配 macOS/Windows。
- Alt+F4：Windows 关闭窗口。
- Cmd+Q：macOS 退出应用。


## 系统对话框

dialog 模块提供原生文件、消息、错误等系统对话框。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Electron 原生功能集成` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
